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
CATEGORIES=	dvl
MASTER_SITES=   # none
DISTFILES=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

NO_BUILD=	YES
NO_INSTALL=	YES

USES=		python

RUN_DEPENDS+=	freshports-ingress>=2.0.4:dvl/freshports-ingress
RUN_DEPENDS+=	freshports-freshports>=2.0.0:dvl/freshports-freshports
RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}packages-import>=0.1.17:dvl/py-packages-import
RUN_DEPENDS+=	freshports-periodics>=1.0.24:dvl/freshports-periodics

.include <bsd.port.mk>
