PORTNAME=	freshports-freshports
PORTVERSION=	2.0.15
PORTREVISION=	3
CATEGORIES=	freshports
MASTER_SITES=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://github.com/FreshPorts/freshports

# ingress.sh invokes perl on a script installed by freshports-scripts
USES=		perl5

RUN_DEPENDS+=	p5-freshports-scripts>=2.0.0:freshports/p5-freshports-scripts

NO_BUILD=	YES

USERS=		freshports
GROUPS=		${USERS}

ETCDIR=		${PREFIX}/etc/freshports
LOGDIR=		/var/log/freshports

FP_SERVICESDIR=	${PREFIX}/libexec/freshports-service

SUB_FILES=	freshports
SUB_LIST=	FP_SERVICESDIR=${FP_SERVICESDIR} \
		LOGDIR=${LOGDIR}

PLIST_SUB+=	FP_SERVICESDIR=${FP_SERVICESDIR} \
		LOGDIR=${LOGDIR}

.include <bsd.port.pre.mk>

do-install:
	@${ECHO} "Installing in ${FP_SERVICESDIR}"
	${MKDIR} ${STAGEDIR}${FP_SERVICESDIR}
	${MKDIR} ${STAGEDIR}/${LOGDIR}
	${MKDIR} ${STAGEDIR}/${ETCDIR}
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/syslog.d

	${INSTALL_SCRIPT} ${WRKSRC}/freshports.sh ${STAGEDIR}${FP_SERVICESDIR}
	${INSTALL_DATA}   ${WRKSRC}/config/freshports.sh ${STAGEDIR}${ETCDIR}/freshports.sh.sample

	${MKDIR} ${STAGEDIR}/var/run/freshports

	${INSTALL_SCRIPT} ${WRKDIR}/freshports ${STAGEDIR}$/${PREFIX}/etc/rc.d/

	${INSTALL_DATA} ${FILESDIR}/freshports.syslogd.conf ${STAGEDIR}${PREFIX}/etc/syslog.d/freshports-daemon.conf.sample

# newsyslog.conf
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d
	${INSTALL_DATA} ${FILESDIR}/freshports-daemon.newsyslog.d.conf ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d/freshports-daemon.conf.sample

.include <bsd.port.post.mk>
