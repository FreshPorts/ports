# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# Install the dependencies required by services.unixathome.org
#
# Copyright (c) 2020 DVL Software Limited
#

PORTNAME=	services-dependencies
PORTVERSION=	1.0.2
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=	# none
DISTFILES=	# none
EXTRACT_ONLY=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

USES=		php:web
# for bacula
USE_PHP=	pgsql

RUN_DEPENDS+=	mod_php81>0:www/mod_php81

# used by /usr/local/etc/nrpe.d/atlas_probe.cfg which invokes /usr/local/libexec/nagios-custom/check_ripe_atlas
RUN_DEPENDS+=	p5-LWP-Protocol-https>0:www/p5-LWP-Protocol-https

NO_BUILD=	YES
NO_INSTALL=	YES

.include <bsd.port.mk>
