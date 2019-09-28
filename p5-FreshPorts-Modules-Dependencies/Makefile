# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the perl modules needed by FreshPorts ingress
#
# Copyright (c) 2002-2006 DVL Software Limited
#

PORTNAME=	FreshPorts-Modules-Dependencies
PORTVERSION=	1.1.18
PORTREVISION=	3
CATEGORIES=	dvl
MASTER_SITES=   # none
PKGNAMEPREFIX=	p5-
DISTFILES=	# none
EXTRACT_ONLY=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

USES=		perl5 python pgsql

RUN_DEPENDS+=	p5-Class-Observable>0:devel/p5-Class-Observable
RUN_DEPENDS+=	p5-Date-Calc>0:devel/p5-Date-Calc
RUN_DEPENDS+=	p5-DBD-Pg>0:databases/p5-DBD-Pg
RUN_DEPENDS+=	p5-Email-MIME>0:mail/p5-Email-MIME
RUN_DEPENDS+=	p5-List-MoreUtils>0:lang/p5-List-MoreUtils
RUN_DEPENDS+	p5-IO-Socket-SSL>0:security/p5-IO-Socket-SSL
RUN_DEPENDS+=	p5-Email-Sender>0:mail/p5-Email-Sender
RUN_DEPENDS+=	p5-Text-Unidecode>0:converters/p5-Text-Unidecode
RUN_DEPENDS+=	p5-TimeDate>0:devel/p5-TimeDate
RUN_DEPENDS+=	p5-XML-Node>0:textproc/p5-XML-Node
RUN_DEPENDS+=	p5-XML-Writer>0:textproc/p5-XML-Writer
RUN_DEPENDS+=	p5-libwww>0:www/p5-libwww
RUN_DEPENDS+=	p5-Unix-Syslog>0:sysutils/p5-Unix-Syslog
RUN_DEPENDS+=	subversion>0:devel/subversion
RUN_DEPENDS+=	sudo>0:security/sudo

WANT_PGSQL=	client

USERS=	freshports ingress
GROUPS=	${USERS}

ETCDIR=			${PREFIX}/etc/freshports
FP_LOGDIR=		/var/log/freshports

SUB_LIST+=	FRESHPORTS_USER=freshports
SUB_LIST+=	FRESHPORTS_GROUP=freshports
SUB_LIST+=	FP_LOGDIR=${FP_LOGDIR}

SUB_FILES=	freshports.conf.newsyslog.conf freshports.conf.syslog.conf

NO_BUILD=	YES

.include <bsd.port.pre.mk>

do-install:
	# move configuration files to the right place
	${MKDIR} ${STAGEDIR}${ETCDIR}

	# symlinks from code dir to ETCDIR
	${MKDIR} ${STAGEDIR}/${SITE_PERL}/FreshPorts
	${LN} -sf ${ETCDIR}/config.pm ${STAGEDIR}/${SITE_PERL}/FreshPorts

.include <bsd.port.post.mk>
