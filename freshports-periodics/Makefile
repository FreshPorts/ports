# Created by: Dan Langille <dan@langille.org>
#
# Install the periodics needed by FreshPorts
#
# Copyright (c) Dan Langille
#

PORTNAME=	freshports-periodics
PORTVERSION=	1.0.28
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=   # none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only

NO_BUILD=	YES

USERS=	freshports
GROUPS=	${USERS}

PERIODS=	everythreeminutes hourly daily weekly fortnightly monthly

.include <bsd.port.pre.mk>

do-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/cron.d
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/periodic
	${MKDIR} ${STAGEDIR}${EXAMPLESDIR}

	${INSTALL_DATA} ${FILESDIR}/freshports-periodics               ${STAGEDIR}${PREFIX}/etc/cron.d
	${INSTALL_DATA} ${FILESDIR}/freshports-periodics.for.ingress   ${STAGEDIR}${EXAMPLESDIR}
	${INSTALL_DATA} ${FILESDIR}/freshports-periodics.for.newsyslog ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d/freshports-periodics.conf

.for _period in ${PERIODS}
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/periodic/${_period}
	(cd ${WRKSRC}/${_period}  && ${COPYTREE_BIN} . ${STAGEDIR}${PREFIX}/etc/periodic/${_period})
.endfor

.include <bsd.port.post.mk>
