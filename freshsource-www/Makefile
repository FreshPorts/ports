# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the www needed by FreshSource
#
# Copyright (c) 2002-2006 DVL Software Limited
#

PORTNAME=	freshsource
PORTVERSION=	0.0.8
PORTREVISION=	1
CATEGORIES=	dvl
MASTER_SITES=   # none
PKGNAMESUFFIX=	-www

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

RUN_DEPENDS=	nginx:www/nginx

NO_BUILD=	YES

WANT_PGSQL=	client
USES=		perl5 php

SUB_FILES=	freshsource-www.conf.newsyslog.conf

# having these configuration files in different directories.. perhaps they should be consolidated.
# In the DISTFILE, these files will have a .sample extension. Leaving that suffix off here helps us create
# symlinks to the real file
CONF_FILES=	database.php virtualhost-common.conf
INC_FILES=	common.php

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${WWWDIR}"
	${MKDIR} ${STAGEDIR}${WWWDIR}
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/nginx/includes
	${MKDIR} ${STAGEDIR}${ETCDIR}

	# install everything +x, because it's easier
	@(cd ${WRKSRC} && ${COPYTREE_BIN} . ${STAGEDIR}${WWWDIR})

	# move configuration files to the right place
.for _conf in ${CONF_FILES}
	${MV} ${STAGEDIR}${WWWDIR}/configuration/${_conf}.sample ${STAGEDIR}${ETCDIR}
	${LN} -sf ${ETCDIR}/${_conf} ${STAGEDIR}${WWWDIR}/configuration/${_conf}
.endfor

.for _inc in ${INC_FILES}
	${MV} ${STAGEDIR}${WWWDIR}/www/include/${_inc}.sample ${STAGEDIR}${ETCDIR}
	${LN} -sf ${ETCDIR}/${_inc} ${STAGEDIR}${WWWDIR}/www/include/${_inc}
.endfor

	# robots.txt link
	${MV} ${STAGEDIR}${WWWDIR}/configuration/robots.txt.sample ${STAGEDIR}${ETCDIR}
	${LN} -sf ${ETCDIR}/robots.txt ${STAGEDIR}${WWWDIR}/www/robots.txt

	# phorum link
	${LN} -sf ${PREFIX}/www/phorum           ${STAGEDIR}${WWWDIR}/www/phorum
	${LN} -sf ${ETCDIR}/cache_moderators.php ${STAGEDIR}${WWWDIR}/configuration/phorum/cache_moderators.php
	${LN} -sf ${ETCDIR}/forums.php           ${STAGEDIR}${WWWDIR}/configuration/phorum/forums.php
	${LN} -sf ${ETCDIR}/1.php                ${STAGEDIR}${WWWDIR}/configuration/phorum/1.php
	
	# vhosts.conf
	${MV} ${STAGEDIR}${WWWDIR}/configuration/vhosts.conf.sample ${STAGEDIR}${ETCDIR}

	# newsyslog.conf
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d
	${INSTALL_DATA} ${WRKDIR}/freshsource-www.conf.newsyslog.conf ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d/freshsource-www.conf.sample

.include <bsd.port.post.mk>
