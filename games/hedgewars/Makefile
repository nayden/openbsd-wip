# $OpenBSD$

SHARED_ONLY =		Yes

COMMENT-main =		Worms-like strategy game
COMMENT-server =	Worms-like strategy game, server

MULTI_PACKAGES =	-main -server

#SHARED_LIBS +=  avwrapper                 0.0 # 0.0
#SHARED_LIBS +=  hwphysfs                  0.0 # 2.1
SHARED_LIBS +=  physlayer                 0.0 # 0.0

R =			0.9.21
V =			$R.1
DISTNAME =		hedgewars-src-$V
PKGNAME-main =		hedgewars-$V
PKGNAME-server =	hedgewars-server-$V

CATEGORIES =		games

HOMEPAGE =		http://www.hedgewars.org/

MAINTAINER =		Pascal Stumpf <Pascal.Stumpf@cubes.de>

# GPLv2
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB-main += QtGui QtNetwork SDL SDL_image SDL_mixer SDL_net SDL_ttf
WANTLIB-main += c m physfs png pthread stdc++ z
WANTLIB-main += ${MODLUA_WANTLIB} ${MODQT4_WANTLIB}

# dlopen()ed; do not remove.
WANTLIB-main += GL GLU glut

WANTLIB-server = c m pthread z ${MODLIBICONV_WANTLIB}

MASTER_SITES =		http://download.gna.org/hedgewars/
EXTRACT_SUFX =		.tar.bz2

MODULES =		devel/cmake \
			x11/qt4 \
			lang/lua \
			converters/libiconv
#MODCLANG_LANGS =	c c++
#MODCLANG_ARCHS =	*
USE_NINJA =		No
BUILD_DEPENDS =		lang/fpc
LIB_DEPENDS-main =	devel/sdl-image \
			devel/sdl-ttf \
			devel/sdl-net \
			devel/sdl-mixer \
			devel/physfs \
			graphics/freeglut \
			${MODQT4_LIB_DEPENDS}
LIB_DEPENDS-server =	converters/libiconv

CONFIGURE_ARGS +=	-DNOVIDEOREC=ON

PSEUDO_FLAVORS = no_server
FLAVOR ?=

.if ${FLAVOR:Mno_server}
CONFIGURE_ARGS +=	-DNOSERVER=ON
.else
MODULES +=		lang/ghc
BUILD_DEPENDS +=	devel/hs-vector \
			devel/hs-network \
			devel/hs-dataenc \
			devel/hs-random \
			devel/hs-hslogger \
			security/hs-SHA \
			security/hs-entropy \
			textproc/hs-bytestring-show \
			archivers/hs-zlib
MODGHC_BUILD =		nort
.endif

#CFLAGS +=		-I${X11BASE}/include

NO_TEST =		Yes

WRKDIST =		${WRKDIR}/hedgewars-src-$R

.include <bsd.port.mk>
