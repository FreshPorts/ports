# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the scripts needed by FreshPorts ingress - for git processing
#
# Copyright (c) 2002-2021 DVL Software Limited
#

PORTNAME=	freshports-git-proc-commit
PORTVERSION=	0.0.4
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=	# none
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DISTFILES=	# none
EXTRACT_ONLY=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://svn.int.unixathome.org/viewvc.cgi/websites/ports/py-freshports-git-proc-commit-dependencies/

USES=		python

NO_BUILD=	YES
NO_INSTALL=	YES

RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}pygit2>0:devel/py-pygit2@${PY_FLAVOR}
RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}lxml>0:devel/py-lxml@${PY_FLAVOR}
RUN_DEPENDS+=	git-lite>0:devel/git@lite

.include <bsd.port.mk>
