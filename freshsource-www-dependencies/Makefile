PORTNAME=	freshsource
PORTVERSION=	1.0.0
PORTREVISION=	1
CATEGORIES=	freshports
MASTER_SITES=	# none
PKGNAMESUFFIX=	-www-dependencies
DISTFILES=	# none
EXTRACT_ONLY=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://github.com/FreshPorts/freshsource

# For FreshSource dev instances: the website is a git checkout in ${WWWDIR}
# and this port supplies only the symlinks into FreshPorts and ${ETCDIR}.
RUN_DEPENDS=	freshports-www-dependencies>0:freshports/freshports-www-dependencies

CONFLICTS_INSTALL=	freshsource-www

NO_BUILD=	YES
NO_ARCH=	YES

# icons linked from the <head> emitted by FreshPorts include/freshports.php
# and from www/manifest.json; FreshSource has none of its own
ICON_FILES=	android-icon-144x144.png android-icon-192x192.png \
		android-icon-36x36.png android-icon-48x48.png \
		android-icon-72x72.png android-icon-96x96.png \
		favicon-16x16.png favicon-32x32.png favicon-96x96.png \
		ms-icon-144x144.png ms-icon-150x150.png \
		ms-icon-310x310.png ms-icon-70x70.png

FP_WWWDIR=	${PREFIX}/www/freshports

do-install:
	${MKDIR} ${STAGEDIR}${WWWDIR}/configuration
	${MKDIR} ${STAGEDIR}${WWWDIR}/include
	${MKDIR} ${STAGEDIR}${WWWDIR}/www/images

	${LN} -sf ${ETCDIR}/database.php ${STAGEDIR}${WWWDIR}/configuration

	${LN} -sf ${FP_WWWDIR}/vendor  ${STAGEDIR}${WWWDIR}
	${LN} -sf ${FP_WWWDIR}/classes ${STAGEDIR}${WWWDIR}

	${LN} -sf ${FP_WWWDIR}/configuration/freshports.conf.php ${STAGEDIR}${WWWDIR}/configuration

	${LN} -sf ${FP_WWWDIR}/www/images/captcha ${STAGEDIR}${WWWDIR}/www/images
.for _icon in ${ICON_FILES}
	${LN} -sf ${FP_WWWDIR}/www/images/${_icon} ${STAGEDIR}${WWWDIR}/www/images
.endfor
	${LN} -sf ${FP_WWWDIR}/www/css            ${STAGEDIR}${WWWDIR}/www
	${LN} -sf ${FP_WWWDIR}/www/javascript     ${STAGEDIR}${WWWDIR}/www

	${LN} -sf ${FP_WWWDIR}/include/constants.local.php          ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/constants.php                ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/fontsize.php                 ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/htmlify.php                  ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/i18n.php                     ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/lib_autolink                 ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/new-user.php                 ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/password-reset-via-token.php ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/spam-filter-information.php  ${STAGEDIR}${WWWDIR}/include

.include <bsd.port.mk>
