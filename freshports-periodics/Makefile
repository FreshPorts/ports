# Created by: Dan Langille <dan@langille.org>
#
# Install the periodics needed by FreshPorts
#
# Copyright (c) Dan Langille
#

PORTNAME=	freshports-periodics
PORTVERSION=	1.0.17
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=   # none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

NO_BUILD=	YES

USERS=	freshports
GROUPS=	${USERS}

PERIODS=	hourly daily weekly fortnightly monthly

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${PREFIX}/libexec/freshports"
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/periodic

.for _period in ${PERIODS}
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/periodic/${_period}
	(cd ${WRKSRC}/${_period}  && ${COPYTREE_BIN} . ${STAGEDIR}${PREFIX}/etc/periodic/${_period})
.endfor

.include <bsd.port.post.mk>
