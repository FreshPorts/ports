PORTNAME=	freshports-www-offline
PORTVERSION=	0.0.2
PORTREVISION=	1
CATEGORIES=	dvl
MASTER_SITES=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://github.com/FreshPorts/freshports-www-offline

USE_GITHUB=	yes
GH_ACCOUNT=	FreshPorts

NO_BUILD=	YES

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${WWWDIR}"
	${MKDIR} ${STAGEDIR}${WWWDIR}

# rename that one file
	${MV} ${WRKSRC}/nginx-includes/offline.conf ${WRKSRC}/nginx-includes/offline.conf.sample
# install everything +x, because it's easier
	@(cd ${WRKSRC} && ${COPYTREE_BIN} . ${STAGEDIR}${WWWDIR})

.include <bsd.port.post.mk>
