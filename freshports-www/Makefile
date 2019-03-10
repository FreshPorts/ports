# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the www needed by FreshPorts
#
# Copyright (c) 2002-2006 DVL Software Limited
#

PORTNAME=	freshports
PORTVERSION=	1.1.6
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=   # none
PKGNAMESUFFIX=	-www

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

USES=		perl5 php python

USE_GITHUB=	yes
GH_ACCOUNT=	FreshPorts

NO_BUILD=	YES

WANT_PGSQL=	client plperl
USE_PHP=	ctype dom exif fileinfo filter gd hash iconv json mbstring opcache pgsql phar posix session simplexml tokenizer xml xmlreader xmlwriter zip zlib

FP_DATADIR=	/var/db/freshports
FP_LOGDIR=	/var/log/freshports

PLIST_SUB+=	FP_DATADIR=${FP_DATADIR}
PLIST_SUB+=	FP_LOGDIR=${FP_LOGDIR}

SUB_LIST+=	FP_LOGDIR=${FP_LOGDIR}
SUB_LIST+=	FRESHPORTS_USER=freshports

SUB_FILES=	freshports-www.conf.newsyslog.conf freshports-www.conf.syslog.conf

# having these configuration files in different directories.. perhaps they should be consolidated.
# In the DISTFILE, these files will have a .sample extension. Leaving that suffix off here helps us create
# symlinks to the real file
CONF_FILES=	database.php freshports.conf.php robots.txt status-config.php vhosts.conf vhosts.conf.nginx virtualhost-common.conf virtualhost-common-ssl.conf
INC_FILES=	common.php constants.local.php
NEWS_FILES=	atom0.3.php html.php js.php mbox.php opml.php pie0.1.php rss0.91.php rss1.0.php rss2.0.php

RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}freshports-fp-listen>=0:dvl/py-freshports-fp-listen
RUN_DEPENDS+=	UniversalFeedCreator>=1.8.3:www/UniversalFeedCreator
RUN_DEPENDS+=	nginx:www/nginx
RUN_DEPENDS+=	php${PHP_VER}-pear-HTML_Page2>0:devel/pear-HTML_Page2
RUN_DEPENDS+=	php${PHP_VER}-pear-Pager>0:devel/pear-Pager

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${WWWDIR}"
	${MKDIR} ${STAGEDIR}${WWWDIR}

	# we don't need this in here.
	${RM} -rf ${WRKSRC}/docs

	# install everything +x, because it's easier
	@(cd ${WRKSRC} && ${COPYTREE_BIN} . ${STAGEDIR}${WWWDIR})

	# move configuration files to the right place
	${MKDIR} ${STAGEDIR}${ETCDIR}
.for _conf in ${CONF_FILES}
	${INSTALL_SCRIPT} ${WRKSRC}/configuration/${_conf}.sample ${STAGEDIR}${ETCDIR}
	${LN} -sf ${ETCDIR}/${_conf} ${STAGEDIR}${WWWDIR}/configuration/${_conf}
.endfor

.for _inc in ${INC_FILES}
	${INSTALL_SCRIPT} ${WRKSRC}/include/${_inc}.sample ${STAGEDIR}${ETCDIR}
	${LN} -sf ${ETCDIR}/${_inc} ${STAGEDIR}${WWWDIR}/include/${_inc}
.endfor

.for _news in ${NEWS_FILES}
	(cd ${STAGEDIR}${WWWDIR}/www/backend && ${LN} -sf news.php ${_news})
.endfor

	# robots.txt link
	${LN} -sf ${ETCDIR}/robots.txt ${STAGEDIR}${WWWDIR}/www/robots.txt

	# phorum link
	${LN} -sf ${PREFIX}/www/phorum           ${STAGEDIR}${WWWDIR}/www/phorum
	${LN} -sf ${ETCDIR}/cache_moderators.php ${STAGEDIR}${WWWDIR}/configuration/phorum/cache_moderators.php
	${LN} -sf ${ETCDIR}/forums.php           ${STAGEDIR}${WWWDIR}/configuration/phorum/forums.php
	${LN} -sf ${ETCDIR}/1.php                ${STAGEDIR}${WWWDIR}/configuration/phorum/1.php
	${LN} -sf ${ETCDIR}/2.php                ${STAGEDIR}${WWWDIR}/configuration/phorum/2.php

	# nginx link
	${LN} -sf ${PREFIX}/etc/nginx/includes/freshports.org.conf ${STAGEDIR}${ETCDIR}/vhosts.conf

	# logs
	${MKDIR} ${STAGEDIR}${FP_LOGDIR}

	# syslog.conf
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/syslog.d
	${INSTALL_DATA} ${WRKDIR}/freshports-www.conf.syslog.conf    ${STAGEDIR}${PREFIX}/etc/syslog.d/freshports-www.conf.sample

	# newsyslog.conf
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d
	${INSTALL_DATA} ${WRKDIR}/freshports-www.conf.newsyslog.conf ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d/freshports-www.conf.sample

.include <bsd.port.post.mk>
