# $OpenBSD$
# This port is released to the public domain.
#
COMMENT=	"timetabling for a school"

V=		1.1
DISTNAME=	asigna-${V}
CATEGORIES=    	education
PKGNAME= 	${DISTNAME}p0

HOMEPAGE=	http://structio.sourceforge.net/asigna
MAINTAINER=	Vladimir T�mara <vtamara@pasosdeJesus.org>

MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=structio/}
DISTFILES=	${DISTNAME}.tar.gz



#Public domain
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM= Yes
PERMIT_DISTFILES_FTP=	Yes

CONFIGURE_STYLE=        simple
CONFIGURE_SCRIPT=       conf.sh

#PREFIX=/

do-regress:
	cd ${WRKSRC} && make check

do-install:
	cd ${WRKSRC} && make instala && make instala-php

.include <bsd.port.mk>
