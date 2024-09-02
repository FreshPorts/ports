# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the ports needed by FreshPorts
#
# Copyright (c) 2002-2006 DVL Software Limited
#

PORTNAME=	FreshPorts-Scripts-Dependencies
PORTVERSION=	1.0.7
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=	# none
DISTFILES=	# none
EXTRACT_ONLY=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

NO_BUILD=	YES
NO_INSTALL=	YES

# for p5-FreshPortsModules
BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}psycopg2>0:databases/py-psycopg2@${PY_FLAVOR}

RUN_DEPENDS+=	p5-Class-Observable>0:devel/p5-Class-Observable \
		p5-Date-Calc>0:devel/p5-Date-Calc \
		p5-DBD-Pg>0:databases/p5-DBD-Pg \
		p5-Email-MIME>0:mail/p5-Email-MIME \
		p5-Email-Sender>0:mail/p5-Email-Sender \
		p5-IO-String>0:devel/p5-IO-String \
		p5-libwww>0:www/p5-libwww \
		p5-List-MoreUtils>0:lang/p5-List-MoreUtils \
		p5-Text-Unidecode>0:converters/p5-Text-Unidecode \
		p5-Text-Wrapper>0:textproc/p5-Text-Wrapper \
		p5-TimeDate>0:devel/p5-TimeDate \
		p5-Unix-Syslog>0:sysutils/p5-Unix-Syslog \
		p5-XML-DOM-XPath>=0:textproc/p5-XML-DOM-XPath \
		p5-XML-Node>0:textproc/p5-XML-Node \
		p5-XML-Writer>0:textproc/p5-XML-Writer

RUN_DEPENDS+=	p5-DBD-Pg>0:databases/p5-DBD-Pg \
		p5-XML-Writer>0:textproc/p5-XML-Writer \
		subversion>0:devel/subversion

# for importing Git commits
RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}lxml>0:devel/py-lxml@${PY_FLAVOR}

RUN_DEPENDS+=	git-lite>0:devel/git@lite \
		sudo>0:security/sudo

WANT_PGSQL=	client
USES=		perl5 pgsql python

USERS=		freshports ingress
GROUPS=		${USERS}

ETCDIR=		${PREFIX}/etc/freshports
FP_LOGDIR=	/var/log/freshports

PLIST_SUB+=	FP_LOGDIR=${FP_LOGDIR}

.include <bsd.port.mk>
