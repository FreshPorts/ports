# Created by: Dan Langille <dan@langille.org>
#
# Install the git-specific helper scripts
#
# Copyright (c) Dan Langille
#

PORTNAME=	helper_scripts
DISTVERSION=	0.0.1
PORTREVISION=	1
CATEGORIES=	dvl
MASTER_SITES=   # none
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

.include <bsd.port.post.mk>
