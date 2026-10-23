PORTNAME=	freshsource
PORTVERSION=	1.0.0
PORTREVISION=	0
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
