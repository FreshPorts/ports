# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the ports needed by FreshPorts
#
# Copyright (c) 2002-2006 DVL Software Limited
#

PORTNAME=	FreshPorts-Scripts-Dependencies
PORTVERSION=	1.0.3
PORTREVISION=	3
CATEGORIES=	dvl
MASTER_SITES=   # none
DISTFILES=	# none
EXTRACT_ONLY=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

NO_BUILD=	YES
NO_INSTALL=	YES

# needed for freshports-fp-daemon
RUN_DEPENDS+=	daemontools>0:sysutils/daemontools

# for p5-FreshPortsModules
BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}psycopg2>0:databases/py-psycopg2@${PY_FLAVOR}

RUN_DEPENDS+=	p5-Class-Observable>0:devel/p5-Class-Observable
RUN_DEPENDS+=	p5-Date-Calc>0:devel/p5-Date-Calc
RUN_DEPENDS+=	p5-DBD-Pg>0:databases/p5-DBD-Pg
RUN_DEPENDS+=	p5-Email-MIME>0:mail/p5-Email-MIME
RUN_DEPENDS+=	p5-List-MoreUtils>0:lang/p5-List-MoreUtils
RUN_DEPENDS+	p5-IO-Socket-SSL>0:security/p5-IO-Socket-SSL
RUN_DEPENDS+=	p5-Email-Sender>0:mail/p5-Email-Sender
RUN_DEPENDS+=	p5-Text-Unidecode>0:converters/p5-Text-Unidecode
RUN_DEPENDS+=	p5-TimeDate>0:devel/p5-TimeDate
RUN_DEPENDS+=	p5-Text-Wrapper>0:textproc/p5-Text-Wrapper
RUN_DEPENDS+=	p5-XML-Node>0:textproc/p5-XML-Node
RUN_DEPENDS+=	p5-XML-Writer>0:textproc/p5-XML-Writer
RUN_DEPENDS+=	p5-libwww>0:www/p5-libwww
RUN_DEPENDS+=	p5-Unix-Syslog>0:sysutils/p5-Unix-Syslog

RUN_DEPENDS+=	maildrop>0:mail/maildrop
RUN_DEPENDS+=	p5-DBD-Pg>0:databases/p5-DBD-Pg
RUN_DEPENDS+=	p5-XML-Writer>0:textproc/p5-XML-Writer
RUN_DEPENDS+=	subversion>0:devel/subversion

# for importing Git commits
RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}GitPython>0:devel/py-gitpython@${PY_FLAVOR}
RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}lxml>0:devel/py-lxml@${PY_FLAVOR}

RUN_DEPENDS+=	git-lite>0:devel/git-lite
RUN_DEPENDS+=	sudo>0:security/sudo

WANT_PGSQL=	client
USES=		perl5 python:3.6 pgsql

USERS=	freshports ingress
GROUPS=	${USERS}

FP_DATADIR=	/var/db/freshports
INGRESS_DATADIR=	/var/db/ingress
PORTSJAIL=	/var/db/freshports/ports-jail
FP_LOGDIR=	/var/log/freshports

PLIST_SUB+=	INGRESS_DATADIR=${INGRESS_DATADIR}
PLIST_SUB+=	FP_DATADIR=${FP_DATADIR}
PLIST_SUB+=	FP_LOGDIR=${FP_LOGDIR}


.include <bsd.port.pre.mk>

post-install:
	# logs
	${MKDIR} ${STAGEDIR}${FP_LOGDIR}
	${MKDIR} ${STAGEDIR}${PORTSJAIL}/etc
	${INSTALL_DATA} ${FILESDIR}/make.conf ${STAGEDIR}${PORTSJAIL}/etc/
	${MKDIR} ${STAGEDIR}${PREFIX}/libexec/freshports
	# FP_DATADIR is the homedir of the freshports user and will already exist.
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/cache
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/cache/html
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/cache/spooling
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/mail
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/message-queues
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/message-queues/archive
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/message-queues/recent
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/message-queues/retry
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail/bin
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail/dev
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail/etc
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail/lib
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail/libexec
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail/sbin
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail/usr/share/mk
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail/usr/sbin
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail/usr/bin
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail/usr/lib
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail/usr/libexec
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail/var
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail/var/db
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/ports-jail/var/db/repos
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/signals
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/tmp
	${MKDIR} ${STAGEDIR}${INGRESS_DATADIR}/mail
	${MKDIR} ${STAGEDIR}${INGRESS_DATADIR}/message-queues
	${MKDIR} ${STAGEDIR}${INGRESS_DATADIR}/message-queues/incoming
	
.include <bsd.port.post.mk>
