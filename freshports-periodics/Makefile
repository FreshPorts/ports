# Created by: Dan Langille <dan@langille.org>
#
# Install the periodics needed by FreshPorts
#
# Copyright (c) Dan Langille
#

PORTNAME=	freshports-periodics
PORTVERSION=	1.0.14
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
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/periodic/hourly
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/periodic/daily

	# the master port testing scripts
	(cd ${WRKSRC}/hourly && ${COPYTREE_BIN} . ${STAGEDIR}${PREFIX}/etc/periodic/hourly)
	(cd ${WRKSRC}/daily  && ${COPYTREE_BIN} . ${STAGEDIR}${PREFIX}/etc/periodic/daily)

.include <bsd.port.post.mk>
