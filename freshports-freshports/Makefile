# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the ports needed by FreshPorts
#
# Copyright (c) 2002-2006 DVL Software Limited
#

PORTNAME=	freshports-freshports
PORTVERSION=	2.0.11
PORTREVISION=	6
CATEGORIES=	dvl
MASTER_SITES=   # none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

# ingress.sh invokes perl on a script installed by freshports-scripts-git
USES=		perl5

RUN_DEPENDS+=	p5-freshports-scripts-git>=2.0.0:dvl/p5-freshports-scripts-git

NO_BUILD=	YES

USERS=	freshports
GROUPS=	${USERS}

ETCDIR=	${PREFIX}/etc/freshports
LOGDIR=	/var/log/freshports

FP_SERVICESDIR=	${PREFIX}/libexec/freshports-service

SUB_FILES=	freshports
SUB_LIST=	LOGDIR=${LOGDIR} \
		FP_SERVICESDIR=${FP_SERVICESDIR}

PLIST_SUB+=	FP_SERVICESDIR=${FP_SERVICESDIR} \
		LOGDIR=${LOGDIR}

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${FP_SERVICESDIR}"
	${MKDIR} ${STAGEDIR}${FP_SERVICESDIR}
	${MKDIR} ${STAGEDIR}/${LOGDIR}
	${MKDIR} ${STAGEDIR}/${ETCDIR}
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/syslog.d

	${INSTALL_SCRIPT} ${WRKSRC}/freshports.sh ${STAGEDIR}${FP_SERVICESDIR}
	${INSTALL_DATA}   ${WRKSRC}/config/freshports.sh ${STAGEDIR}${ETCDIR}/freshports.sh.sample
	
	${MKDIR} ${STAGEDIR}/var/run/freshports

	${INSTALL_SCRIPT} ${WRKDIR}/freshports ${STAGEDIR}$/${PREFIX}/etc/rc.d/

	${INSTALL_DATA} ${FILESDIR}/freshports.syslogd.conf ${STAGEDIR}${PREFIX}/etc/syslog.d/freshports-daemon.conf.sample

	# newsyslog.conf
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d
	${INSTALL_DATA} ${FILESDIR}/freshports-daemon.newsyslog.d.conf ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d/freshports-daemon.conf.sample

.include <bsd.port.post.mk>
