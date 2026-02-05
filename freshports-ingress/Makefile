PORTNAME=	freshports-ingress
DISTVERSION=	2.0.4
PORTREVISION=	15
CATEGORIES=	freshports
MASTER_SITES=	# none

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		https://svn.int.unixathome.org/viewvc.cgi/freshports-1/daemontools/branches/git/ingress/

# ingress.sh invokes perl on a script installed by freshports-scripts
USES=		perl5 python

RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}freshports-git-proc-commit>0:freshports/py-freshports-git-proc-commit \
		freshports-helper_scripts>=0.0.1:freshports/freshports-helper-scripts \
		p5-freshports-scripts>=2.0.0:freshports/p5-freshports-scripts

NO_BUILD=	YES

USERS=		ingress
GROUPS=		${USERS}

ETCDIR=		${PREFIX}/etc/freshports
LOGDIR=		/var/log/freshports

FP_SERVICESDIR=	${PREFIX}/libexec/freshports-service

SUB_FILES=	ingress
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

	${INSTALL_SCRIPT} ${WRKSRC}/ingress.sh ${STAGEDIR}${FP_SERVICESDIR}
	${INSTALL_DATA}   ${WRKSRC}/config/ingress.sh ${STAGEDIR}${ETCDIR}/ingress.sh.sample

	${MKDIR} ${STAGEDIR}/var/run/ingress

	${INSTALL_SCRIPT} ${WRKDIR}/ingress ${STAGEDIR}$/${PREFIX}/etc/rc.d/

	${INSTALL_DATA} ${FILESDIR}/ingress.syslogd.conf ${STAGEDIR}${PREFIX}/etc/syslog.d/ingress-daemon.conf.sample

# newsyslog.conf
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d
	${INSTALL_DATA} ${FILESDIR}/freshports-ingress.newsyslog.d.conf ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d/ingress.conf.sample

.include <bsd.port.post.mk>
