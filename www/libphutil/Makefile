# $OpenBSD: Makefile,v 1.45 2013/03/11 11:44:50 espie Exp $

COMMENT =	collection of PHP utility classes for phabricator

COMMIT_ID =     944738bdf93751d11f20f6aa6dc2e4e62d86a308
DUMMY_VER =	0.20131007
DISTNAME =	libphutil-${DUMMY_VER}
DISTFILES = 	libphutil-${DUMMY_VER}{${COMMIT_ID}.tar.gz}
CATEGORIES =	www devel

HOMEPAGE =	http://phabricator.org/
MAINTAINER =	Gabriel Guzman <gabe@lifewaza.com>

# Apache
PERMIT_PACKAGE_CDROM =	Yes

MASTER_SITES =	http://github.com/facebook/libphutil/archive/

MODULES =	lang/php

NO_BUILD =	Yes
NO_TEST =	Yes
PKG_ARCH =	*

PREFIX =	/var/www
INSTDIR =	${PREFIX}/libphutil
WRKDIST  =      ${WRKDIR}/libphutil-${COMMIT_ID}/

SUBST_VARS =	INSTDIR

do-install:
	${INSTALL_DATA_DIR} ${PREFIX}/libphutil
	cd ${WRKSRC} && pax -rw * ${PREFIX}/libphutil

.include <bsd.port.mk>
