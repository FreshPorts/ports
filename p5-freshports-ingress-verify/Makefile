# Created by: Dan Langille <dan@langille.org>
#
# Install the perl scripts used to run one-off task.
#
# Copyright (c) 2002-2021 DVL Software Limited
#

PORTNAME=	freshports-ingress-verify
PORTVERSION=	2.2.0
PORTREVISION=	0
CATEGORIES=	freshports
MASTER_SITES=	# none
PKGNAMEPREFIX=	p5-

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://svn.int.unixathome.org/viewvc.cgi/freshports-1/ingress/Verify/trunk/

USES=		perl5

USE_GITHUB=	yes
GH_ACCOUNT=	FreshPorts
GH_PROJECT=	ingress-verify

NO_BUILD=	YES

RUN_DEPENDS+=	p5-freshports-ingress-modules>0:freshports/p5-freshports-ingress-modules \
		p5-freshports-ingress-scripts>0:freshports/p5-freshports-ingress-scripts

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${PREFIX}/libexec/freshports/Verify"
	${MKDIR} ${STAGEDIR}/${SITE_PERL}/FreshPorts/Verify

# install everything +x, because it's easier
	@(cd ${WRKSRC} && ${COPYTREE_BIN} . ${STAGEDIR}/${SITE_PERL}/FreshPorts/Verify)

.include <bsd.port.post.mk>
