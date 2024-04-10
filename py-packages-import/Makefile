# Created by: Dan Langille <dan@langille.org>
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the scripts needed by FreshPorts ingress for handling packages
#
# Copyright (c) 2002-2006 DVL Software Limited
#

PORTNAME=	packages-import
DISTVERSION=	2.6.3
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=	GH
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

NO_BUILD=	YES

RUN_DEPENDS+=	jq>0:textproc/jq
RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}yaml>0:devel/py-yaml
RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}psycopg2>0:databases/py-psycopg2

WANT_PGSQL=	client
USES=		python shebangfix

USE_GITHUB=	yes
GH_ACCOUNT=	FreshPorts

USERS=		freshports
GROUPS=		${USERS}

FP_DATADIR=	/var/db/freshports

SCRIPTS=	UpdatePackagesFromRawPackages.py check_repos_for_new_stuff.py get_packagesite.txz_date import_packagesite.py fetch-extract-parse-import-one-abi.sh import-via-copy-packagesite-all-raw-fields.py

SHEBANG_FILES=	UpdatePackagesFromRawPackages.py check_repos_for_new_stuff.py import_packagesite.py import-via-copy-packagesite-all-raw-fields.py

CACHE_SUBDIRS=	packages

PLIST_SUB+=	FP_DATADIR=${FP_DATADIR}

SUB_LIST+=	FRESHPORTS_USER=freshports
SUB_LIST+=	FRESHPORTS_GROUP=logcheck

SUB_FILES=	config.ini.sample 900.freshports-check-repos-for-new-builds

.include <bsd.port.pre.mk>

do-install:
	${RM} ${WRKSRC}/Makefile.PL
	@${ECHO} "Installing in ${PREFIX}/libexec/freshports"
	${MKDIR} ${STAGEDIR}${PREFIX}/libexec/freshports
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/freshports/
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/packagesite

	# FP_DATADIR is the homedir of the freshports user and will already exist.

	${MKDIR} ${STAGEDIR}${PREFIX}/etc/periodic/hourly

.for _script in ${SCRIPTS}
	${INSTALL_SCRIPT} ${WRKSRC}/${_script} ${STAGEDIR}${PREFIX}/libexec/freshports
.endfor

	${INSTALL_SCRIPT} ${WRKDIR}/900.freshports-check-repos-for-new-builds ${STAGEDIR}${PREFIX}/etc/periodic/hourly
	${INSTALL_DATA} ${WRKDIR}/config.ini.sample ${STAGEDIR}${PREFIX}/etc/freshports/

.include <bsd.port.post.mk>
