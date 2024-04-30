PORTNAME=	freshports
DISTVERSION=	2.9.1
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=	# none
PKGNAMESUFFIX=	-www

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://github.com/FreshPorts/freshports

USES=		perl5 php python

USE_GITHUB=	yes
GH_ACCOUNT=	FreshPorts

NO_BUILD=	YES

WANT_PGSQL=	client plperl
USE_PHP=	ctype dom exif fileinfo filter gd hash iconv json mbstring \
		opcache pgsql phar posix session simplexml tokenizer xml \
		xmlreader xmlwriter zip zlib

USERS=		freshports www
GROUPS=		${USERS}

SUB_LIST+=	FRESHPORTS_USER=freshports

SUB_FILES=	freshports-www.conf.newsyslog freshports-www.conf.syslog \
		php.conf.newsyslog

FP_LOGDIR=	/var/log/freshports
SUB_LIST+=	FP_LOGDIR=${FP_LOGDIR}
SUB_LIST+=	LOGCHECK_GROUP=logcheck

# having these configuration files in different directories.. perhaps they should be consolidated.
# In the DISTFILE, these files will have a .sample extension. Leaving that suffix off here helps us create
# symlinks to the real file
CONF_FILES=	config.sh database.php freshports.conf.php freshports.net.conf \
		robots.txt vhosts.conf vhosts.conf.nginx \
		virtualhost-common.conf virtualhost-common-ssl.conf
INC_FILES=	common.php constants.local.php
NEWS_FILES=	atom0.3.php html.php js.php mbox.php opml.php pie0.1.php \
		rss0.91.php rss1.0.php rss2.0.php

RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}freshports-fp-listen>=1.0.2:dvl/py-freshports-fp-listen@${PY_FLAVOR} \
		libucl>0:textproc/libucl \
		nginx:www/nginx \
		php${PHP_VER}-pear-HTML_Page2>0:devel/pear-HTML_Page2 \
		php${PHP_VER}-pear-Pager>0:devel/pear-Pager \
		phpmailer6>0:mail/phpmailer6 \
		UniversalFeedCreator>=1.8.3:www/UniversalFeedCreator

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

# nginx link
	${LN} -sf ${PREFIX}/etc/nginx/includes/freshports.org.conf ${STAGEDIR}${ETCDIR}/vhosts.conf

# syslog.conf
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/syslog.d
	${INSTALL_DATA} ${WRKDIR}/freshports-www.conf.syslog    ${STAGEDIR}${PREFIX}/etc/syslog.d/freshports-www.conf.sample

# newsyslog.conf
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d
	${INSTALL_DATA} ${WRKDIR}/freshports-www.conf.newsyslog ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d/freshports-www.conf.sample
	${INSTALL_DATA} ${WRKDIR}/php.conf.newsyslog            ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d/php.conf.sample

.include <bsd.port.post.mk>
