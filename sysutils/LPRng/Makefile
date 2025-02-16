PORTNAME=	LPRng
PORTVERSION=	3.8.C
PORTREVISION=	6
PORTEPOCH=	1
CATEGORIES=	sysutils print
MASTER_SITES=	SF/${PORTNAME:tl}/${PORTNAME:tl}
DISTNAME=	${PORTNAME:tl}-${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Enhanced Printer Spooler
WWW=		https://lprng.sourceforge.net/

LICENSE=	ART10 GPLv2
LICENSE_COMB=	dual

LIB_DEPENDS=	libgdbm.so:databases/gdbm

USES=		gmake ssl
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--with-config_subdir="" \
		--with-filterdir=${PREFIX}/libexec/filters \
		--with-filter_path="${PREFIX}/bin:/bin:/usr/bin:${PREFIX}/sbin:/sbin:/usr/sbin" \
		--with-printcap_path=/etc/printcap \
		--with-ld_library_path="${PREFIX}/lib:/lib:/usr/lib:/${LOCALBASE}/lib"
MAKE_ARGS=	INSTALLCONFIGEXAMPLES=""
USE_LDCONFIG=	yes
USE_RC_SUBR=	${PORTNAME:tl}

CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

# Upstream dead, don't expect a proper fix.
CFLAGS+=	-fcommon

SUB_FILES=	pkg-message

CONFLICTS=	cups

OPTIONS_DEFINE=		LIBWRAP NLS
OPTIONS_DEFAULT=	LIBWRAP
OPTIONS_SUB=		yes

LIBWRAP_CONFIGURE_ENABLE=	tcpwrappers
NLS_USES=		gettext
NLS_CONFIGURE_ENABLE=	nls
NLS_CONFIGURE_ENV=	gt_cv_func_gnugettext1_libc=yes \
			ac_cv_func_ngettext=yes
NLS_LDFLAGS=		-lintl

post-install:
.for i in lpd.perms printcap
	(cd ${WRKSRC}/conf && $ ${INSTALL_DATA} ${i} \
		${STAGEDIR}/${PREFIX}/etc/${i}.sample)
.endfor
.for i in lpd.conf
	(cd ${WRKSRC}/src && $ ${INSTALL_DATA} ${i} \
		${STAGEDIR}/${PREFIX}/etc/${i}.sample)
.endfor

.include <bsd.port.mk>
