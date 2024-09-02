# Created by: Dan Langille <dan@langille.org>
#
# fp-listen listens for PostgreSQL NOTIFY events
# and clears cache.
#
# Copyright (c) 2002-2021 Dan Langille
#

PORTNAME=	freshports-fp-listen
PORTVERSION=	1.0.9
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=	# none
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://svn.int.unixathome.org/viewvc.cgi/freshports-1/daemontools/branches/git/fp-listen/

NO_BUILD=	YES

RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}configparser>0:devel/py-configparser@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}psycopg2>0:databases/py-psycopg2@${PY_FLAVOR}

WANT_PGSQL=	client
USES=		python
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

post-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/${ETCDIR}
	${INSTALL_DATA}   ${WRKSRC}/etc/freshports/fp-listen.ini.sample ${STAGEDIR}/${PREFIX}/${ETCDIR}/
	${INSTALL_SCRIPT} ${WRKDIR}/fp_listen ${STAGEDIR}$/${PREFIX}/etc/rc.d/

.include <bsd.port.mk>
