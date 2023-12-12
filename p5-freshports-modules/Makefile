# Created by: Dan Langille <dan@langille.org>
#
# Install the  modules needed by FreshPorts ingress
#
# Copyright (c) 2002-2023 Dan Langille
#

PORTNAME=	freshports-modules
PORTVERSION=	2.0.30
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=	# none
PKGNAMEPREFIX=	p5-

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

NO_BUILD=	YES

BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}psycopg2>0:databases/py-psycopg2

RUN_DEPENDS+=	p5-Email-Address-XS>0:mail/p5-Email-Address-XS
RUN_DEPENDS+=	p5-Class-Observable>0:devel/p5-Class-Observable
RUN_DEPENDS+=	p5-Date-Calc>0:devel/p5-Date-Calc
RUN_DEPENDS+=	p5-DBD-Pg>0:databases/p5-DBD-Pg
RUN_DEPENDS+=	p5-Email-MIME>0:mail/p5-Email-MIME
RUN_DEPENDS+=	p5-Email-Stuffer>0:mail/p5-Email-Stuffer
RUN_DEPENDS+=	p5-List-MoreUtils>0:lang/p5-List-MoreUtils
RUN_DEPENDS+	p5-IO-Socket-SSL>0:security/p5-IO-Socket-SSL
RUN_DEPENDS+=	p5-Email-Sender>0:mail/p5-Email-Sender
RUN_DEPENDS+=	p5-Text-Unidecode>0:converters/p5-Text-Unidecode
RUN_DEPENDS+=	p5-TimeDate>0:devel/p5-TimeDate
RUN_DEPENDS+=	p5-XML-Node>0:textproc/p5-XML-Node
RUN_DEPENDS+=	p5-XML-Writer>0:textproc/p5-XML-Writer
RUN_DEPENDS+=	p5-libwww>0:www/p5-libwww
RUN_DEPENDS+=	p5-Unix-Syslog>0:sysutils/p5-Unix-Syslog
RUN_DEPENDS+=	sudo>0:security/sudo

WANT_PGSQL=	client
USES=		perl5 python pgsql
USE_PERL5=	configure

USERS=	freshports ingress
GROUPS=	${USERS}

FP_DATADIR=		/var/db/freshports
INGRESS_DATADIR=	/var/db/ingress
ETCDIR=			${PREFIX}/etc/freshports
FP_LOGDIR=		/var/log/freshports

CACHE_SUBDIRS=	daily html news ports spooling

SUB_LIST+=	FRESHPORTS_USER=freshports
SUB_LIST+=	FRESHPORTS_GROUP=freshports
SUB_LIST+=	FP_LOGDIR=${FP_LOGDIR}

SUB_FILES=	freshports.conf.newsyslog.conf freshports.conf.syslog.conf

.include <bsd.port.pre.mk>

post-install:
	# move configuration files to the right place
	${MKDIR} ${STAGEDIR}${ETCDIR}
	${INSTALL_DATA} ${WRKSRC}/config.pm.sample  ${STAGEDIR}${ETCDIR}

	# symlinks from code dir to ETCDIR
	${LN} -sf ${ETCDIR}/config.pm ${STAGEDIR}/${SITE_PERL}/FreshPorts

.include <bsd.port.post.mk>
