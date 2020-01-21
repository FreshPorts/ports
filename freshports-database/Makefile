# Created by: Dan Langille <dan@langille.org>
#
# Install the components pertaining to the FreshPorts database
#
# Copyright (c) Dan Langille
#

PORTNAME=	freshports-database
PORTVERSION=	1.0.0
PORTREVISION=	1
CATEGORIES=	dvl
MASTER_SITES=   # none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

NO_BUILD=	YES

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${DATADIR}"
	${MKDIR} ${STAGEDIR}${DATADIR}

	${INSTALL_DATA} ${WRKSRC}/ri.txt ${STAGEDIR}${DATADIR}
	${INSTALL_DATA} ${WRKSRC}/sp.txt ${STAGEDIR}${DATADIR}

.include <bsd.port.post.mk>
