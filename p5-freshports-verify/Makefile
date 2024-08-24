# Created by: Dan Langille <dan@langille.org>
#
# Install the perl scripts used to run one-off task.
#
# Copyright (c) 2002-2021 DVL Software Limited
#

PORTNAME=	freshports-verify
PORTVERSION=	2.0.10
PORTREVISION=	1
CATEGORIES=	dvl
MASTER_SITES=   # none
PKGNAMEPREFIX=	p5-

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://svn.int.unixathome.org/viewvc.cgi/freshports-1/ingress/Verify/trunk/

NO_BUILD=	YES

USES=		perl5

RUN_DEPENDS+=	p5-freshports-scripts>0:dvl/p5-freshports-scripts
RUN_DEPENDS+=	p5-freshports-modules>0:dvl/p5-freshports-modules

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${PREFIX}/libexec/freshports/Verify"
	${MKDIR} ${STAGEDIR}/${SITE_PERL}/FreshPorts/Verify

	# install everything +x, because it's easier
	@(cd ${WRKSRC} && ${COPYTREE_BIN} . ${STAGEDIR}/${SITE_PERL}/FreshPorts/Verify)

.include <bsd.port.post.mk>
