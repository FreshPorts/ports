# Created by: Dan Langille <dan@langille.org>
#
# fp-listen listens for PostgreSQL NOTIFY events
# and clears cache.
#
# Copyright (c) 2002-2021 Dan Langille
#

PORTNAME=	freshports-fp-listen
PORTVERSION=	2.0.2
PORTREVISION=	0
CATEGORIES=	freshports
MASTER_SITES=	# none
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://github.com/FreshPorts/fp-listen/

NO_BUILD=	YES

RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}configparser>0:devel/py-configparser@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}psycopg2>0:databases/py-psycopg2@${PY_FLAVOR}

USES=		python

USE_GITHUB=	yes
GH_ACCOUNT=	FreshPorts
GH_PROJECT=	fp-listen

WANT_PGSQL=	client
USE_PYTHON=	distutils

USERS=		freshports
GROUPS=		${USERS}

ETCDIR=		etc/freshports
SERVICE_DIR=	${PREFIX}/libexec/freshports-service

SUB_LIST+=	ETCDIR=${PREFIX}/${ETCDIR} \
		FP_SERVICESDIR=${PYTHON_SITELIBDIR}/fp-listen \
		FRESHPORTS_USER=freshports \
		PYTHON_SITELIBDIR=${PYTHON_SITELIBDIR}

SUB_FILES=	fp_listen

PLIST_SUB=	PORTVERSION=${PORTVERSION}

post-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/${ETCDIR}
	${INSTALL_DATA}   ${WRKSRC}/etc/freshports/fp-listen.ini.sample ${STAGEDIR}/${PREFIX}/${ETCDIR}/
	${INSTALL_SCRIPT} ${WRKDIR}/fp_listen ${STAGEDIR}$/${PREFIX}/etc/rc.d/

.include <bsd.port.mk>
