# Created by: Dan Langille <dan@langille.org>
#
# Install the git-specific helper scripts
#
# Copyright (c) Dan Langille
#

PORTNAME=	helper_scripts
DISTVERSION=	0.0.5
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=	https://git.langille.org/FreshPorts/helper_scripts/archive/${DISTVERSION}${EXTRACT_SUFX}?dummy=/
PKGNAMEPREFIX=	freshports-

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

NO_BUILD=	YES

USERS=	freshports
GROUPS=	${USERS}

LIBEXECDIR=${PREFIX}/libexec/freshports/helper_scripts

PLIST_SUB=	LIBEXECDIR=${LIBEXECDIR}
WRKSRC=		${WRKDIR}/${PORTNAME}

.include <bsd.port.pre.mk>

do-install:
	${MKDIR} ${STAGEDIR}${LIBEXECDIR}
	@(cd ${WRKSRC} && ${COPYTREE_BIN} . ${STAGEDIR}${LIBEXECDIR} "-name *\.sh")

	${INSTALL_SCRIPT} ${WRKSRC}/create-symlinks-amongst-dev-source-directories ${STAGEDIR}${LIBEXECDIR}
	${INSTALL_SCRIPT} ${WRKSRC}/website-clear-all-cache.sample                 ${STAGEDIR}${LIBEXECDIR}

.include <bsd.port.post.mk>
