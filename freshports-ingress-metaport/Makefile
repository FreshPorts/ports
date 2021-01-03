# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# $Id$
#
# Install the ports needed by FreshPorts in an ingress site
#
# Copyright (c) 2002-2020 Dan Langille
#

PORTNAME=	freshports-ingress-metaport
PORTVERSION=	0.1.0
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=   # none
DISTFILES=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

NO_BUILD=	YES
NO_INSTALL=	YES


RUN_DEPENDS+=	freshports-ingress>=2.0.4:dvl/freshports-ingress
RUN_DEPENDS+=	freshports-ingress-svn>=1.0.9:dvl/freshports-ingress-svn
RUN_DEPENDS+=	packages-import>=0.1.17:dvl/packages-import
RUN_DEPENDS+=	freshports-periodics>=1.0.24:dvl/freshports-periodics

.include <bsd.port.mk>
