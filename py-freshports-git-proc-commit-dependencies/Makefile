# Created by: Dan Langille <dan@langille.org>
#
# Install the scripts needed by FreshPorts ingress - for git processing
# Useful only if you're not installing py-freshports-git-proc-commit
#
# Copyright (c) 2002-2026 Dan Langille
#

PORTNAME=	freshports-git-proc-commit
PORTVERSION=	0.0.4
PORTREVISION=	2
CATEGORIES=	freshports
MASTER_SITES=	# none
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
PKGNAMESUFFIX=	-dependencies
DISTFILES=	# none
EXTRACT_ONLY=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://github.com/FreshPorts/git_proc_commit

USES=		python

NO_BUILD=	YES
NO_INSTALL=	YES
NO_ARCH=	YES

RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}lxml>0:devel/py-lxml@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}pygit2>=1.15.0:devel/py-pygit2@${PY_FLAVOR} \
		git-lite>0:devel/git@lite

.include <bsd.port.mk>
