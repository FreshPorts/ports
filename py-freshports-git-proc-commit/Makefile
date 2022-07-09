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
PORTVERSION=	0.1.3
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=	# none
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	dan@langille.org
COMMENT=	Process git commits into XML

USES=		python shebangfix

NO_BUILD=	YES

RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}pygit2>0:devel/py-pygit2@${PY_FLAVOR}
RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}lxml>0:devel/py-lxml@${PY_FLAVOR}
RUN_DEPENDS+=	git-lite>0:devel/git@lite

USE_GITHUB=	yes
GH_ACCOUNT=	FreshPorts
GH_PROJECT=	git_proc_commit

SHEBANG_FILES=	git-to-freshports/git-to-freshports-xml.py
SCRIPTS=	check_git.sh git-delta.sh git-range-of-commits.sh git-single-commit.sh git-to-freshports-xml.py

.include <bsd.port.pre.mk>

do-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/libexec/freshports

	# install everything +x, because it's easier
.for _script in ${SCRIPTS}
	${INSTALL_SCRIPT} ${WRKSRC}/git-to-freshports/${_script} ${STAGEDIR}${PREFIX}/libexec/freshports
.endfor

.include <bsd.port.post.mk>
