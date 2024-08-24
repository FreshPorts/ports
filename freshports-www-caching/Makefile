# Created by: Dan Langille <dan@langille.org>
# $FreeBSD$
#
# $Id: Makefile,v 1.4 2011-06-14 17:32:41 dan Exp $
#
# Install the www needed by FreshPorts
#
# Copyright (c) 2002-2006 DVL Software Limited
#

PORTNAME=	freshports-www-cache
PORTVERSION=	0.0.1
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=	# none
PKGNAMESUFFIX=	-www-cache
DISTFILES=	# none
EXTRACT_ONLY=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		# none - creates directories for developement nodes

NO_BUILD=	YES

USERS=		freshports www
GROUPS=		${USERS}

FP_DATADIR=	/var/db/freshports

PLIST_SUB+=	FP_DATADIR=${FP_DATADIR}

# NOTE: the html directory is nullfs mounted from the ingress directory
CACHE_DIR=	${FP_DATADIR}/cache
CACHE_DIRS=	categories daily general html news packages pages ports spooling

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${CACHE_DIR}"
	${MKDIR} ${STAGEDIR}${CACHE_DIR}

.for _dir in ${CACHE_DIRS}
	${MKDIR} ${STAGEDIR}${CACHE_DIR}/${_dir}
.endfor

.include <bsd.port.post.mk>
