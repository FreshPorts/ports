# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the www needed by FreshSource
#
# Copyright (c) 2002-2026 Dan Langille
#

PORTNAME=	freshsource
DISTVERSION=	2.3.15.2
PORTREVISION=	1
CATEGORIES=	freshports
MASTER_SITES=	# none
PKGNAMESUFFIX=	-www

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://github.com/FreshPorts/freshsource

RUN_DEPENDS=	freshports-www>0:freshports/freshports-www \
		nginx>0:www/nginx

USES=		perl5 php

NO_BUILD=	YES

WANT_PGSQL=	client
USE_GITHUB=	yes
GH_ACCOUNT=	FreshPorts

SUB_FILES=	freshsource-www.conf.newsyslog.conf

# having these configuration files in different directories.. perhaps they should be consolidated.
# In the DISTFILE, these files will have a .sample extension. Leaving that suffix off here helps us create
# symlinks to the real file
CONF_FILES=	database.php vhosts.conf virtualhost-common.conf \
		virtualhost-common-ssl.conf

INC_FILES=	common.php

# icons linked from the <head> emitted by FreshPorts include/freshports.php
# and from www/manifest.json; FreshSource has none of its own
ICON_FILES=	android-icon-144x144.png android-icon-192x192.png \
		android-icon-36x36.png android-icon-48x48.png \
		android-icon-72x72.png android-icon-96x96.png \
		favicon-16x16.png favicon-32x32.png favicon-96x96.png \
		ms-icon-144x144.png ms-icon-150x150.png \
		ms-icon-310x310.png ms-icon-70x70.png

FP_WWWDIR=	${PREFIX}/www/freshports

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${WWWDIR}"
	${MKDIR} ${STAGEDIR}${WWWDIR}
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/nginx/includes
	${MKDIR} ${STAGEDIR}${ETCDIR}

# we don't need this in here.
	${RM} ${WRKSRC}/README.md

# install everything +x, because it's easier
	@(cd ${WRKSRC} && ${COPYTREE_BIN} . ${STAGEDIR}${WWWDIR})

# move configuration files to the right place
.for _conf in ${CONF_FILES}
	${MV} ${STAGEDIR}${WWWDIR}/configuration/${_conf}.sample ${STAGEDIR}${ETCDIR}
	${LN} -sf ${ETCDIR}/${_conf} ${STAGEDIR}${WWWDIR}/configuration/${_conf}
.endfor

.for _inc in ${INC_FILES}
	${MV} ${STAGEDIR}${WWWDIR}/include/${_inc}.sample ${STAGEDIR}${ETCDIR}
	${LN} -sf ${ETCDIR}/${_inc} ${STAGEDIR}${WWWDIR}/include/${_inc}
.endfor

# robots.txt link
	${MV} ${STAGEDIR}${WWWDIR}/configuration/robots.txt.sample ${STAGEDIR}${ETCDIR}
	${LN} -sf ${ETCDIR}/robots.txt ${STAGEDIR}${WWWDIR}/www/robots.txt

# newsyslog.conf
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d
	${INSTALL_DATA} ${WRKDIR}/freshsource-www.conf.newsyslog.conf ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d/freshsource-www.conf.sample

# freshports.conf.php

# vendor directory symlink
	${LN} -sf ${FP_WWWDIR}/vendor  ${STAGEDIR}${WWWDIR}
	${LN} -sf ${FP_WWWDIR}/classes ${STAGEDIR}${WWWDIR}

	${LN} -sf ${FP_WWWDIR}/configuration/freshports.conf.php ${STAGEDIR}${WWWDIR}/configuration

	${LN} -sf ${FP_WWWDIR}/www/images/captcha ${STAGEDIR}${WWWDIR}/www/images
.for _icon in ${ICON_FILES}
	${LN} -sf ${FP_WWWDIR}/www/images/${_icon} ${STAGEDIR}${WWWDIR}/www/images
.endfor
	${LN} -sf ${FP_WWWDIR}/www/css            ${STAGEDIR}${WWWDIR}/www
	${LN} -sf ${FP_WWWDIR}/www/javascript     ${STAGEDIR}${WWWDIR}/www
	${LN} -sf ${FP_WWWDIR}/www/fontsize.php   ${STAGEDIR}${WWWDIR}/www
	${LN} -sf ${FP_WWWDIR}/www/language.php   ${STAGEDIR}${WWWDIR}/www

	${LN} -sf ${FP_WWWDIR}/include/constants.local.php          ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/constants.php                ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/fontsize.php                 ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/htmlify.php                  ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/i18n.php                     ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/lib_autolink                 ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/new-user.php                 ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/password-reset-via-token.php ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/redirect-back.php            ${STAGEDIR}${WWWDIR}/include
	${LN} -sf ${FP_WWWDIR}/include/spam-filter-information.php  ${STAGEDIR}${WWWDIR}/include

# translations, read by include/i18n.php from ../locale
	${LN} -sf ${FP_WWWDIR}/locale ${STAGEDIR}${WWWDIR}

.include <bsd.port.post.mk>
