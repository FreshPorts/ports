# Created by: Dan Langille <dan@langille.org>
#
# Install the periodics needed by FreshPorts
#
# Copyright (c) Dan Langille
#

PORTNAME=	freshports-periodics
PORTVERSION=	1.0.38
PORTREVISION=	0
CATEGORIES=	dvl
MASTER_SITES=   # none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://svn.int.unixathome.org/viewvc.cgi/freshports-1/periodics

NO_BUILD=	YES

USERS=	freshports
GROUPS=	${USERS}

# variables for substitution in vendor tarbaalal
FP_LIBEXEC="${LOCALBASE}/libexec/freshports"
FP_USER_FRESHPORTS="freshports"
FP_USER_INGRESS="ingress"
FP_LOG_DIR="/var/log/freshports"
LOGCHECK_USER=logcheck

SUB_LIST+=	FP_LOG_DIR=${FP_LOG_DIR} \
		FP_USER_FRESHPORTS=freshports \
		LOGCHECK_GROUP=logcheck

SUB_FILES=	freshports-periodics.for.newsyslog

PERIODS=	everythreeminutes hourly daily weekly fortnightly monthly

.include <bsd.port.pre.mk>

post-patch:
	@${FIND} ${WRKSRC} -type f -exec \
		${REINPLACE_CMD} -e 's@%%LOCALBASE%%@${LOCALBASE}@g' \
	                         -e 's@%%FP_LIBEXEC%%@${FP_LIBEXEC}@g' \
	                         -e 's@%%FP_USER_FRESHPORTS%%@${FP_USER_FRESHPORTS}@g' \
	                         -e 's@%%FP_USER_INGRESS%%@${FP_USER_INGRESS}@g' \
	                         -e 's@%%FP_LOG_DIR%%@${FP_LOG_DIR}@g' {} \;

do-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/cron.d
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/periodic
	${MKDIR} ${STAGEDIR}${EXAMPLESDIR}

	${INSTALL_DATA} ${FILESDIR}/freshports-periodics               ${STAGEDIR}${PREFIX}/etc/cron.d
	${INSTALL_DATA} ${FILESDIR}/freshports-periodics.for.ingress   ${STAGEDIR}${EXAMPLESDIR}
	${INSTALL_DATA} ${WRKDIR}/freshports-periodics.for.newsyslog   ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d/freshports-periodics.conf

.for _period in ${PERIODS}
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/periodic/${_period}
	(cd ${WRKSRC}/${_period}  && ${COPYTREE_BIN} . ${STAGEDIR}${PREFIX}/etc/periodic/${_period})
.endfor

.include <bsd.port.post.mk>
