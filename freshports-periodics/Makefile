# Created by: Dan Langille <dan@langille.org>
#
# Install the periodics needed by FreshPorts
#
# Copyright (c) Dan Langille
#

PORTNAME=	freshports-periodics
PORTVERSION=	1.0.0
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=   # none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

NO_BUILD=	YES

USERS=	freshports
GROUPS=	${USERS}

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${PREFIX}/libexec/freshports"
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/periodic
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/periodic/daily

	# install the maildrop bits
	${INSTALL_SCRIPT} ${WRKSRC}/100.fp_archive_messages    ${STAGEDIR}${PREFIX}/etc/periodic/daily

.include <bsd.port.post.mk>
