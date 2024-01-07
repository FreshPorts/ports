# Created by: Dan Langille <dan@langille.org>
#
# Install the scripts needed by FreshPorts ingress
#
# Copyright (c) 2002-2023 Dan Langille
#

PORTNAME=	freshports-scripts

PORTVERSION=	2.0.44
PORTREVISION=	1
CATEGORIES=	dvl
MASTER_SITES=	# none
PKGNAMEPREFIX=	p5-

MAINTAINER=	dan@langille.org
COMMENT=	For use by Dan Langille only
WWW=		http://www.FreshPorts.org/

USES=		perl5 pgsql python

NO_BUILD=	YES

RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}pygit2>0:devel/py-pygit2 \
		git-lite>0:devel/git@lite \
		logcheck>0:security/logcheck \
		p5-DBD-Pg>0:databases/p5-DBD-Pg \
		p5-freshports-modules>=2.0.0:dvl/p5-freshports-modules \
		p5-IO-String>0:devel/p5-IO-String \
		p5-Text-Wrapper>0:textproc/p5-Text-Wrapper \
		p5-XML-DOM-XPath>=0:textproc/p5-XML-DOM-XPath \
		p5-XML-Writer>0:textproc/p5-XML-Writer \
		sudo>0:security/sudo

WANT_PGSQL=	client

USERS=		freshports ingress
GROUPS=		${USERS}

FP_DATADIR=		/var/db/freshports
FP_JAILS_DIR=		/jails
FP_JAIL_PATH=		${FP_JAILS_DIR}/freshports
INGRESS_DATADIR=	/var/db/ingress
ETCDIR=			${PREFIX}/etc/freshports
FP_LOGDIR=		/var/log/freshports
FP_LIBEXEC=		libexec/freshports

#
# this line should match what you find in Jail/refresh-jail-scripts.sh in the ingress code
#
JAIL_SCRIPTS=	cat-descr.sh make-category-comment.sh \
		make-flavors-package-names.sh make-generate-plist.sh \
		make-master-port-test.sh make-master-sites-all.sh \
		make-pkg-message-in.sh make-port.sh make-showconfig.sh \
		realpath.sh vars.sh.sample

CACHE_SUBDIRS=	daily html news ports spooling

PLIST_SUB+=	FP_DATADIR=${FP_DATADIR} \
		FP_JAIL_PATH=${FP_JAIL_PATH} \
		FP_JAILS_DIR=${FP_JAILS_DIR} \
		FP_LIBEXEC=${FP_LIBEXEC} \
		INGRESS_DATADIR=${INGRESS_DATADIR}

SUB_LIST+=	FP_LIBEXEC=${FP_LIBEXEC} \
		FP_LOGDIR=${FP_LOGDIR} \
		FRESHPORTS_USER=freshports \
		INGRESS_USER=ingress \
		LOGCHECK_GROUP=logcheck

SUB_FILES=	freshports.conf.newsyslog.conf freshports.conf.syslog.conf

.include <bsd.port.pre.mk>

do-install:
	${RM} ${WRKSRC}/Makefile.PL
	@${ECHO} "Installing in ${PREFIX}/${FP_LIBEXEC}"
	${MKDIR} ${STAGEDIR}${PREFIX}/${FP_LIBEXEC}
	${MKDIR} ${STAGEDIR}${FP_JAIL_PATH}
	${MKDIR} ${STAGEDIR}${FP_JAIL_PATH}/etc

# install everything +x, because it's easier
	@(cd ${WRKSRC} && ${COPYTREE_BIN} . ${STAGEDIR}${PREFIX}/${FP_LIBEXEC})

# move configuration files to the right place
	${MKDIR} ${STAGEDIR}${ETCDIR}
	${MV}    ${STAGEDIR}${PREFIX}/${FP_LIBEXEC}/config.sh.sample  ${STAGEDIR}${ETCDIR}

# symlinks from code dir to ETCDIR
	${LN} -sf ${ETCDIR}/config.sh ${STAGEDIR}${PREFIX}/${FP_LIBEXEC}/config.sh

# install scripts into the jail directory
.for _script in ${JAIL_SCRIPTS}
	${INSTALL_SCRIPT} ${WRKSRC}/Jail/scripts/${_script} ${STAGEDIR}${FP_JAIL_PATH}
.endfor

# install the make.conf file
	${INSTALL_SCRIPT} ${WRKSRC}/Jail/files/etc/make.conf ${STAGEDIR}${FP_JAIL_PATH}/etc

# syslog.conf
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/syslog.d
	${INSTALL_DATA} ${WRKDIR}/freshports.conf.syslog.conf    ${STAGEDIR}${PREFIX}/etc/syslog.d/freshports.conf.sample

# newsyslog.conf
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d
	${INSTALL_DATA} ${WRKDIR}/freshports.conf.newsyslog.conf ${STAGEDIR}${PREFIX}/etc/newsyslog.conf.d/freshports.conf.sample

.include <bsd.port.post.mk>
