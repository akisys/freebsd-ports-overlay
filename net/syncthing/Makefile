# Created by: Steve Wills <swills@FreeBSD.org>
# $FreeBSD$

PORTNAME=	syncthing
PORTVERSION=	0.11.5
PORTREVISION=	0
PORTEPOCH=	0
CATEGORIES=	net
DISTVERSIONPREFIX=	v

MAINTAINER=	swills@FreeBSD.org
COMMENT=	Encrypted file sync tool

BUILD_DEPENDS=	${LOCALBASE}/bin/go:${PORTSDIR}/lang/go

USE_GITHUB=	yes
USE_RC_SUBR=	syncthing
PLIST_FILES=	bin/syncthing
PORTDOCS=	*

USERS=		syncthing
GROUPS=		syncthing

STRIP=		# stripping can break go binaries

post-patch:
	@cd ${WRKSRC} ; ${MKDIR} src/github.com/${PORTNAME}/${PORTNAME} ; \
		${MV} AUTHORS CONTRIBUTING.md Godeps LICENSE README.md \
		build.go build.sh check-contrib.sh assets cmd gui internal \
		protocol test src/github.com/${PORTNAME}/${PORTNAME}

do-build:
	# timestamp here refers to source, not build time
	cd ${WRKSRC}/src/github.com/${PORTNAME}/${PORTNAME} ; \
		${SETENV} GOPATH=${WRKSRC} go run build.go -no-upgrade=true -version v${PORTVERSION}

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/src/github.com/${PORTNAME}/${PORTNAME}/bin/syncthing \
		${STAGEDIR}${PREFIX}/bin/
	${MKDIR} ${STAGEDIR}${DOCSDIR}
.for x in AUTHORS CONTRIBUTING.md LICENSE README.md
	${INSTALL_MAN} ${WRKSRC}/src/github.com/${PORTNAME}/${PORTNAME}/${x} \
		${STAGEDIR}${DOCSDIR}
.endfor

.include <bsd.port.mk>
