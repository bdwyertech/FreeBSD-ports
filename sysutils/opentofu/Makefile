PORTNAME=	opentofu
DISTVERSIONPREFIX=	v
DISTVERSION=	1.6.0-rc1
CATEGORIES=	sysutils

MAINTAINER=	bofh@FreeBSD.org
COMMENT=	Tool for building, changing, and versioning infrastructure
WWW=		https://opentofu.org/

LICENSE=	MPL20
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		go:modules
GO_BUILDFLAGS=	-o bin/
GO_MODULE=	github.com/opentofu/opentofu
GO_TARGET=	./cmd/tofu

PLIST_FILES=	bin/tofu

.include <bsd.port.mk>
