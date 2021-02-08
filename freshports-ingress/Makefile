# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the ports needed by FreshPorts
#
# Copyright (c) 2002-2006 DVL Software Limited
#

PORTNAME=	freshports-ingress
DISTVERSION=	2.0.4
PORTREVISION=	6
CATEGORIES=	dvl
MASTER_SITES=   # none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

# ingress.sh invokes perl on a script installed by freshports-scripts-git
USES=		perl5

RUN_DEPENDS+=	freshports-scripts-git>=2.0.0:dvl/freshports-scripts-git
RUN_DEPENDS+=	freshports-git-proc-commit>0:dvl/freshports-git-proc-commit
RUN_DEPENDS+=	freshports-helper_scripts>=0.0.1:dvl/freshports-helper-scripts

NO_BUILD=	YES

USERS=	ingress
GROUPS=	${USERS}

ETCDIR=	${PREFIX}/etc/freshports
LOGDIR=	/var/log/freshports

FP_SERVICESDIR=	${PREFIX}/libexec/freshports-service

SUB_FILES=	ingress
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

	${INSTALL_SCRIPT} ${WRKSRC}/ingress.sh ${STAGEDIR}${FP_SERVICESDIR}
	${INSTALL_DATA}   ${WRKSRC}/config/ingress.sh ${STAGEDIR}${ETCDIR}/ingress.sh.sample

	${MKDIR} ${STAGEDIR}/var/run/ingress

	${INSTALL_SCRIPT} ${WRKDIR}/ingress ${STAGEDIR}$/${PREFIX}/etc/rc.d/

	${INSTALL_DATA} ${FILESDIR}/ingress.syslogd.conf ${STAGEDIR}${PREFIX}/etc/syslog.d/ingress-daemon.conf.sample

.include <bsd.port.post.mk>
