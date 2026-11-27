PORTNAME=	packages-import
DISTVERSION=	2.9.0
PORTREVISION=	0
CATEGORIES=	freshports
MASTER_SITES=	GH
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://github.com/FreshPorts/packages-import

NO_BUILD=	YES

RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}psycopg2>0:databases/py-psycopg2 \
		${PYTHON_PKGNAMEPREFIX}pyyaml>0:devel/py-pyyaml \
		jq>0:textproc/jq

WANT_PGSQL=	client
USES=		python shebangfix

USE_GITHUB=	yes
GH_ACCOUNT=	FreshPorts

USERS=		freshports
GROUPS=		${USERS}

FP_DATADIR=	/var/db/freshports

SCRIPTS=	UpdatePackagesFromRawPackages.py check_repos_for_new_stuff.py \
		fetch-parse-meta.conf get_packagesite.txz_date \
		import_packagesite.py fetch-extract-parse-import-one-abi.sh \
		import-via-copy-packagesite-all-raw-fields.py \
		packages-delete-missing-repos.py

SHEBANG_FILES=	check_repos_for_new_stuff.py \
		import-via-copy-packagesite-all-raw-fields.py \
		import_packagesite.py packages-delete-missing-repos.py \
		UpdatePackagesFromRawPackages.py

CACHE_SUBDIRS=	packages

PLIST_SUB+=	FP_DATADIR=${FP_DATADIR}

SUB_LIST+=	FRESHPORTS_GROUP=logcheck \
		FRESHPORTS_USER=freshports

SUB_FILES=	900.freshports-check-repos-for-new-builds config.ini.sample

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
