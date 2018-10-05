# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the ports needed by FreshPorts
#
# Copyright (c) 2002-2006 DVL Software Limited
#

PORTNAME=	freshports-fp-listen
PORTVERSION=	1.0.10
PORTREVISION=	3
CATEGORIES=	dvl
MASTER_SITES=   # none

PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

NO_BUILD=	YES

RUN_DEPENDS+=	FreshPorts-Scripts>0:dvl/FreshPorts-Scripts
RUN_DEPENDS+=	daemontools>0:sysutils/daemontools
RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}psycopg2>0:databases/py-psycopg2
RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}configparser>0:devel/py-configparser

WANT_PGSQL=	client
USES=		python
USE_PYTHON=	autoplist distutils

USERS=	freshports
GROUPS=	${USERS}

ETCDIR=		etc/freshports
SERVICE_DIR=	${PREFIX}/libexec/freshports-service


PLIST_SUB+=	SERVICE_DIR=${SERVICE_DIR}
SUB_LIST+=	FRESHPORTS_USER=freshports
SUB_LIST+=	PYTHON_SITELIBDIR=${PYTHON_SITELIBDIR}
SUB_LIST+=	PYTHON_CMD=${PYTHON_CMD}

SUB_FILES=	run

post-install:
	@${ECHO} "Installing in ${SERVICE_DIR}/fp-listen"
	${MKDIR} ${STAGEDIR}${PREFIX}/${ETCDIR}
	${MKDIR} ${STAGEDIR}${SERVICE_DIR}/fp-listen
	${MKDIR} ${STAGEDIR}${SERVICE_DIR}/fp-listen/env
	${MKDIR} ${STAGEDIR}${SERVICE_DIR}/fp-listen/log

	${CP}             ${WRKSRC}/fp-listen.ini.sample ${STAGEDIR}${PREFIX}/${ETCDIR}

	${CP}             ${WRKSRC}/README.txt           ${STAGEDIR}${SERVICE_DIR}/fp-listen
	${CP}             ${WRKSRC}/env/HOME             ${STAGEDIR}${SERVICE_DIR}/fp-listen/env/
	${INSTALL_SCRIPT} ${WRKSRC}/log/run              ${STAGEDIR}${SERVICE_DIR}/fp-listen/log/
	${INSTALL_SCRIPT} ${WRKDIR}/run                  ${STAGEDIR}${SERVICE_DIR}/fp-listen

.include <bsd.port.mk>
