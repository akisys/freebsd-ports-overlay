
PORTNAME=          kibana
PORTVERSION=       4.0.2
CATEGORIES=        net-mgmt
DISTVERSIONPREFIX= v

MAINTAINER=        akisys@alexanderkuemmel.com

USE_GITHUB=        YES
GH_ACCOUNT=        elastic
GH_PROJECT=        ${PORTNAME}

RUN_DEPENDS=       ${LOCALBASE}/bin/node:${PORTSDIR}/www/node\
                   ${LOCALBASE}/bin/npm:${PORTSDIR}/www/npm \
		   ${LOCALBASE}/bin/git:${PORTSDIR}/devel/git

USE_RC_SUBR=       kibana

do-build:
	@echo "nothing to do here"

do-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/${PORTNAME}
	@cd ${WRKSRC} && \
		${COPYTREE_SHARE} . ${STAGEDIR}${PREFIX}/${PORTNAME}


.include <bsd.port.mk>
