PORTNAME=	hesiod
PORTVERSION=	3.2.1
PORTREVISION=	3
CATEGORIES=	dns
MASTER_SITES=	https://BSDforge.com/projects/source/dns/hesiod/

MAINTAINER=	portmaster@BSDforge.com
COMMENT=	Directory service built on DNS and BIND

LICENSE=	BSD2CLAUSE
LICENSE_FILE=	${WRKSRC}/COPYING

BROKEN=		Unfetchable

OPTIONS_DEFINE=	IDN
OPTIONS_DEFAULT=IDN

USES=		cpe libtool pathfix
CPE_VENDOR=	${PORTNAME}_project
GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip
USE_LDCONFIG=	yes

CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MIDN}
LIB_DEPENDS+=	libidn.so:dns/libidn
.else
CONFIGURE_ARGS+=--without-libidn
.endif

.include <bsd.port.mk>
