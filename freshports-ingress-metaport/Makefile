#
# Created by: Dan Langille <dan@langille.org>
#
# Install the ports needed by FreshPorts in an ingress site
#
# Copyright (c) 2002-2020 Dan Langille
#

PORTNAME=	freshports-ingress-metaport
PORTVERSION=	0.1.1
PORTREVISION=	0
CATEGORIES=	freshports
MASTER_SITES=	# none
DISTFILES=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

NO_BUILD=	YES
NO_INSTALL=	YES

USES=		python

RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}packages-import>=0.1.17:freshports/py-packages-import \
		freshports-freshports>=2.0.0:freshports/freshports-freshports \
		freshports-ingress>=2.0.4:freshports/freshports-ingress \
		freshports-periodics>=1.0.24:freshports/freshports-periodics

.include <bsd.port.mk>
