# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# For FreeBSDDiary.org website
#

PORTNAME=	freebsddiary
PORTVERSION=	0.0.1
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=	# none
PKGNAMESUFFIX=	-www

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://svn.int.unixathome.org/viewvc.cgi/freebsddiary

RUN_DEPENDS=	nginx:www/nginx

NO_BUILD=	YES

WANT_PGSQL=	client
USES=		perl5 php:web shebangfix
USE_PERL5=	build

SUB_FILES=	freebsddiary-www.conf.newsyslog.conf

SHEBANG_FILES=	www/samples/obtain_ip.pl \
		www/samples/tunnel.sh \
		www/samples/3Ware/check_3wareraid.pl \
		www/samples/3Ware/check_3wareraidunits.pl \
		www/samples/netsaint/netsaint_statd_mod_3ware \
		www/samples/netsaint/check_adptraid.pl \
		www/samples/netsaint/check_3wareraid.pl \
		configuration/newsfeeds/newsfeeds.pl

# having these configuration files in different directories.. perhaps they should be consolidated.
# In the DISTFILE, these files will have a .sample extension. Leaving that suffix off here helps us create
# symlinks to the real file
CONF_FILES=	database.php vhosts.conf
INC_FILES=	common.php

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${WWWDIR}"
	${MKDIR} ${STAGEDIR}${WWWDIR}
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/nginx/includes
	${MKDIR} ${STAGEDIR}${ETCDIR}
	
	${RM} ${WRKSRC}/configuration/weekly.pl.orig

	# install everything +x, because it's easier
	@(cd ${WRKSRC} && ${COPYTREE_BIN} . ${STAGEDIR}${WWWDIR})

	# move configuration files to the right place
.for _conf in ${CONF_FILES}
	${MV} ${STAGEDIR}${WWWDIR}/configuration/${_conf}.sample ${STAGEDIR}${ETCDIR}
	${LN} -sf ${ETCDIR}/${_conf} ${STAGEDIR}${WWWDIR}/configuration/${_conf}
.endfor

.for _inc in ${INC_FILES}
	${MV} ${STAGEDIR}${WWWDIR}/www/include/${_inc} ${STAGEDIR}${ETCDIR}${_inc}.sample
	${LN} -sf ${ETCDIR}/${_inc} ${STAGEDIR}${WWWDIR}/www/include/${_inc}
.endfor

	# robots.txt link
	${MV} ${STAGEDIR}${WWWDIR}/www/robots.txt.sample ${STAGEDIR}${ETCDIR}
	${LN} -sf ${ETCDIR}/robots.txt ${STAGEDIR}${WWWDIR}/www/robots.txt

	# phorum link
	${LN} -sf ${PREFIX}/www/phorum           ${STAGEDIR}${WWWDIR}/www/phorum
#	${LN} -sf ${ETCDIR}/cache_moderators.php ${STAGEDIR}${WWWDIR}/configuration/phorum/cache_moderators.php
#	${LN} -sf ${ETCDIR}/forums.php           ${STAGEDIR}${WWWDIR}/configuration/phorum/forums.php
#	${LN} -sf ${ETCDIR}/1.php                ${STAGEDIR}${WWWDIR}/configuration/phorum/1.php
	
	# vhosts.conf
	${MV} ${STAGEDIR}${WWWDIR}/configuration/vhosts.conf ${STAGEDIR}${ETCDIR}

	# newsyslog.conf
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d
	${INSTALL_DATA} ${WRKDIR}/freebsddiary-www.conf.newsyslog.conf ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d/freebsddiary-www.conf.sample

.include <bsd.port.post.mk>
