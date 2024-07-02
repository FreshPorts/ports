PORTNAME=	default_vhost
PORTVERSION=	1.0.6
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=	https://git.langille.org/dvl/${PORTNAME}/archive/${DISTVERSION}${EXTRACT_SUFX}?dummy=/
PKGNAMESUFFIX=	_nginx
#DISTFILES=	# none
#EXTRACT_ONLY=	# none

WWWDIR=	${PREFIX}/www/${PORTNAME}${PKGNAMESUFFIX}
WRKSRC=	${WRKDIR}/${PORTNAME}/${PORTNAME}${PKGNAMESUFFIX}
#/wrkdirs/usr/ports/dvl/nginx_default_vhost/work/nginx_default_vhost/default_vhost
MAINTAINER=	dan@langille.org
COMMENT=	A default nginx website

NO_BUILD=	YES

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${WWWDIR}"
	${MKDIR} ${STAGEDIR}${WWWDIR}
	${MKDIR} ${STAGEDIR}${WWWDIR}/configuration
	${MKDIR} ${STAGEDIR}${WWWDIR}/www

	${INSTALL_DATA} ${WRKSRC}/configuration/vhosts.conf.sample           ${STAGEDIR}${WWWDIR}/configuration/
	${INSTALL_DATA} ${WRKSRC}/configuration/virtualhost-common-ssl.conf  ${STAGEDIR}${WWWDIR}/configuration/
	${INSTALL_DATA} ${WRKSRC}/configuration/virtualhost-common.conf      ${STAGEDIR}${WWWDIR}/configuration/

	${INSTALL_DATA} ${WRKSRC}/www/index.html                             ${STAGEDIR}${WWWDIR}/www/
	${INSTALL_DATA} ${WRKSRC}/www/robots.txt                             ${STAGEDIR}${WWWDIR}/www/
	${INSTALL_DATA} ${WRKSRC}/www/favicon.ico                            ${STAGEDIR}${WWWDIR}/www/

.include <bsd.port.post.mk>
