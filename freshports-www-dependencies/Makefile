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
PORTVERSION=	2.2.0
PORTREVISION=	1
CATEGORIES=	dvl
MASTER_SITES=	# none
PKGNAMESUFFIX=	-www-dependencies
DISTFILES=	# none
EXTRACT_ONLY=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

USES=		perl5 php python

WANT_PGSQL=	client

USE_PHP=	ctype dom exif fileinfo filter gd hash iconv json mbstring opcache pgsql phar posix session simplexml tokenizer xml xmlreader xmlwriter zip zlib

FP_LOGDIR=	/var/log/freshports

PLIST_SUB+=	FP_DATADIR=${FP_DATADIR}
PLIST_SUB+=	FP_LOGDIR=${FP_LOGDIR}

SUB_LIST+=	FP_LOGDIR=${FP_LOGDIR}
SUB_LIST+=	FRESHPORTS_USER=freshports

SUB_LIST+=	LOGCHECK_GROUP=logcheck

SUB_FILES=	freshports-www.conf.newsyslog.conf freshports-www.conf.syslog.conf

# having these configuration files in different directories.. perhaps they should be consolidated.
# In the DISTFILE, these files will have a .sample extension. Leaving that suffix off here helps us create
# symlinks to the real file
CONF_FILES=	config.sh database.php freshports.conf.php freshports.net.conf robots.txt status-config.php vhosts.conf vhosts.conf.nginx virtualhost-common.conf virtualhost-common-ssl.conf
INC_FILES=	common.php constants.local.php
NEWS_FILES=	atom0.3.php html.php js.php mbox.php opml.php pie0.1.php rss0.91.php rss1.0.php rss2.0.php

# these are copied from freshports-www-git/Makefile
RUN_DEPENDS+=	phpmailer6>0:mail/phpmailer6
RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}freshports-fp-listen-git>=1.0.2:dvl/py-freshports-fp-listen-git@${PY_FLAVOR}
RUN_DEPENDS+=	UniversalFeedCreator>=1.8.3:www/UniversalFeedCreator
RUN_DEPENDS+=	nginx:www/nginx
RUN_DEPENDS+=	php${PHP_VER}-pear-HTML_Page2>0:devel/pear-HTML_Page2
RUN_DEPENDS+=	php${PHP_VER}-pear-Pager>0:devel/pear-Pager
RUN_DEPENDS+=	libucl>0:textproc/libucl

# these are useful to have
RUN_DEPENDS+=	subversion>0:devel/subversion
RUN_DEPENDS+=	git>0:devel/git
RUN_DEPENDS+=	sudo>0:security/sudo
RUN_DEPENDS+=	libucl>0:textproc/libucl
RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}psycopg2>0:databases/py-psycopg2

NO_BUILD=	YES

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${WWWDIR}"
	${MKDIR} ${STAGEDIR}${WWWDIR}
	${MKDIR} ${STAGEDIR}${FP_DATADIR}
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/cache
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/cache/daily
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/cache/general
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/cache/news
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/cache/pages
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/cache/ports
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/signals
	${MKDIR} ${STAGEDIR}${FP_DATADIR}/tmp

	${MKDIR} ${STAGEDIR}${WWWDIR}/configuration
	${MKDIR} ${STAGEDIR}${WWWDIR}/include
	${MKDIR} ${STAGEDIR}${WWWDIR}/www/backend

	# move configuration files to the right place
	${MKDIR} ${STAGEDIR}${ETCDIR}
.for _conf in ${CONF_FILES}
	${LN} -sf ${ETCDIR}/${_conf} ${STAGEDIR}${WWWDIR}/configuration/${_conf}
.endfor

.for _inc in ${INC_FILES}
	${LN} -sf ${ETCDIR}/${_inc} ${STAGEDIR}${WWWDIR}/include/${_inc}
.endfor

.for _news in ${NEWS_FILES}
	(cd ${STAGEDIR}${WWWDIR}/www/backend && ${LN} -sf news.php ${_news})
.endfor

	# robots.txt link
	${LN} -sf ${ETCDIR}/robots.txt ${STAGEDIR}${WWWDIR}/www/robots.txt

	# nginx link
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/nginx/includes
	${LN} -sf ${ETCDIR}/vhosts.conf ${STAGEDIR}${PREFIX}/etc/nginx/includes/freshports.org.conf

	# logs
	${MKDIR} ${STAGEDIR}${FP_LOGDIR}

	# syslog.conf
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/syslog.d
	${INSTALL_DATA} ${WRKDIR}/freshports-www.conf.syslog.conf    ${STAGEDIR}${PREFIX}/etc/syslog.d/freshports-www.conf.sample

	# newsyslog.conf
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d
	${INSTALL_DATA} ${WRKDIR}/freshports-www.conf.newsyslog.conf ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d/freshports-www.conf.sample

.include <bsd.port.post.mk>
