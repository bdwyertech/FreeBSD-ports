PORTNAME=	ndiff
PORTVERSION=	2.00
PORTREVISION=	4
CATEGORIES=	math
MASTER_SITES=	ftp://ftp.math.utah.edu/pub/misc/

MAINTAINER=	pizzamig@FreeBSD.org
COMMENT=	Compare files, ignoring numeric differences
WWW=		https://www.math.utah.edu/~beebe/software/ndiff/

LICENSE=	GPLv2

USES=		desthack
GNU_CONFIGURE=	yes

PLIST_FILES=	bin/${PORTNAME} \
		man/man1/${PORTNAME}.1.gz \
		%%DATADIR%%/${PORTNAME}.awk

PORTDOCS=	*.html *.pdf *.ps *.txt

OPTIONS_DEFINE=	DOCS GMP

GMP_LIB_DEPENDS=	libgmp.so:math/gmp
GMP_CFLAGS=	-I${LOCALBASE}/include
GMP_LDFLAGS=	-L${LOCALBASE}/lib
GMP_CONFIGURE_ON=	--with-gmp

.include <bsd.port.options.mk>

.if ! ${PORT_OPTIONS:MGMP}
CONFIGURE_ARGS+=	--with-double
.endif

post-patch:
	${REINPLACE_CMD} -e \
	's|$$(shrlibtop)/$$(PROGNAME)-$$(VERSION)|$${DESTDIR}${DATADIR}|; \
	s|.*shrlibtop.*||; \
	s|664|644|' ${WRKSRC}/Makefile.in

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/${PORTNAME}

	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S|^|${WRKSRC}/|} ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
