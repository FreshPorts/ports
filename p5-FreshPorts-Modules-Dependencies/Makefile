# Created by: Dan Langille <dan@langille.org>
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the perl modules needed by dev FreshPorts ingress
#

PORTNAME=	FreshPorts-Modules-Dependencies
PORTVERSION=	1.1.20
PORTREVISION=	0
CATEGORIES=	freshports
MASTER_SITES=	# none
PKGNAMEPREFIX=	p5-
DISTFILES=	# none
EXTRACT_ONLY=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		# none - used by development nodes

USES=		pgsql

RUN_DEPENDS+=	p5-Class-Observable>0:devel/p5-Class-Observable \
		p5-Date-Calc>0:devel/p5-Date-Calc \
		p5-DBD-Pg>0:databases/p5-DBD-Pg \
		p5-Email-Address-XS>0:mail/p5-Email-Address-XS \
		p5-Email-MIME>0:mail/p5-Email-MIME \
		p5-Email-Sender>0:mail/p5-Email-Sender \
		p5-Email-Stuffer>0:mail/p5-Email-Stuffer \
		p5-IO-Socket-SSL>0:security/p5-IO-Socket-SSL \
		p5-libwww>0:www/p5-libwww \
		p5-List-MoreUtils>0:lang/p5-List-MoreUtils \
		p5-Readonly>0:devel/p5-Readonly \
		p5-Text-Unidecode>0:converters/p5-Text-Unidecode \
		p5-TimeDate>0:devel/p5-TimeDate \
		p5-Unix-Syslog>0:sysutils/p5-Unix-Syslog \
		p5-XML-Node>0:textproc/p5-XML-Node \
		p5-XML-Writer>0:textproc/p5-XML-Writer \
		subversion>0:devel/subversion \
		sudo>0:security/sudo

WANT_PGSQL=	client
USES=		perl5 pgsql python

NO_BUILD=	YES
NO_INSTALL=	YES

.include <bsd.port.mk>
