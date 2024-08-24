# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the perl modules needed by FreshPorts ingress
#
# Copyright (c) 2002-2006 DVL Software Limited
#

PORTNAME=	FreshPorts-Modules-Dependencies
PORTVERSION=	1.1.19
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=   # none
PKGNAMEPREFIX=	p5-
DISTFILES=	# none
EXTRACT_ONLY=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		# none - used by development nodes 

USES=		pgsql

RUN_DEPENDS+=	p5-Class-Observable>0:devel/p5-Class-Observable
RUN_DEPENDS+=	p5-Date-Calc>0:devel/p5-Date-Calc
RUN_DEPENDS+=	p5-DBD-Pg>0:databases/p5-DBD-Pg
RUN_DEPENDS+=	p5-Email-MIME>0:mail/p5-Email-MIME
RUN_DEPENDS+=	p5-List-MoreUtils>0:lang/p5-List-MoreUtils
RUN_DEPENDS+	p5-IO-Socket-SSL>0:security/p5-IO-Socket-SSL
RUN_DEPENDS+=	p5-Email-Sender>0:mail/p5-Email-Sender
RUN_DEPENDS+=	p5-Text-Unidecode>0:converters/p5-Text-Unidecode
RUN_DEPENDS+=	p5-TimeDate>0:devel/p5-TimeDate
RUN_DEPENDS+=	p5-XML-Node>0:textproc/p5-XML-Node
RUN_DEPENDS+=	p5-XML-Writer>0:textproc/p5-XML-Writer
RUN_DEPENDS+=	p5-libwww>0:www/p5-libwww
RUN_DEPENDS+=	p5-Unix-Syslog>0:sysutils/p5-Unix-Syslog
RUN_DEPENDS+=	subversion>0:devel/subversion
RUN_DEPENDS+=	sudo>0:security/sudo

WANT_PGSQL=	client

NO_BUILD=	YES
NO_INSTALL=	YES

.include <bsd.port.mk>
