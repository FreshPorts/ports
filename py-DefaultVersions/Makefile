# Created by: Dan Langille <dan@langille.org>
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the scripts needed by FreshPorts ingress for handling packages
#
# Copyright (c) 2002-2026 Dan Langille
#

PORTNAME=	DefaultVersions
DISTVERSION=	0.0.1
PORTREVISION=	0
CATEGORIES=	freshports
MASTER_SITES=	GH
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://github.com/FreshPorts/DefaultVersions

NO_BUILD=	YES

RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}psycopg2>0:databases/py-psycopg2

WANT_PGSQL=	client
USES=		python shebangfix

USE_GITHUB=	yes
GH_ACCOUNT=	FreshPorts

USERS=		freshports
GROUPS=		${USERS}

FP_DATADIR=	/var/db/freshports

SCRIPTS=	detect_default_version_changes.py default_version_change.py sync_default_version_variable.py

SHEBANG_FILES=	${SCRIPTS}

CACHE_SUBDIRS=	packages

PLIST_SUB+=	FP_DATADIR=${FP_DATADIR}

SUB_LIST+=	FRESHPORTS_USER=freshports
SUB_LIST+=	FRESHPORTS_GROUP=logcheck

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${PREFIX}/libexec/freshports"
	${MKDIR} ${STAGEDIR}${PREFIX}/libexec/freshports

.for _script in ${SCRIPTS}
	${INSTALL_SCRIPT} ${WRKSRC}/${_script} ${STAGEDIR}${PREFIX}/libexec/freshports
.endfor

.include <bsd.port.post.mk>
