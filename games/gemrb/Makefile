# $OpenBSD$

SHARED_ONLY = 		Yes

SHARED_LIBS += 		gemrb_core 0.0

COMMENT =		open-source implementation of Bioware's Infinity Engine

DISTNAME =		gemrb-0.8.2

CATEGORIES =		games emulators x11

HOMEPAGE =		http://www.gemrb.org/

MAINTAINER =		Kirill Bychkov <kirby@openbsd.org>

# GPLv2
PERMIT_PACKAGE_CDROM =	Yes

MASTER_SITES =		${MASTER_SITE_SOURCEFORGE:=gemrb/}

WANTLIB += SDL SDL_mixer c freetype m openal png pthread stdc++
WANTLIB += vlc vorbisfile z ${MODPY_WANTLIB}

MODULES =		converters/libiconv devel/cmake lang/python
LIB_DEPENDS =		audio/openal \
			devel/sdl-mixer \
			graphics/png \
			x11/vlc \
			${MODPY_LIB_DEPENDS}
RUN_DEPENDS = 		devel/desktop-file-utils \
			x11/gtk+3,-guic

CONFIGURE_ARGS +=	-DCMAKE_BUILD_TYPE=Release \
			-DSYSCONF_DIR=${SYSCONFDIR}/gemrb/ \
			-DEXAMPLE_CONF_DIR=${PREFIX}/share/examples/gemrb/ \
			-DMAN_DIR=${PREFIX}/man/man6 \
			-DCMAKE_MODULE_LINKER_FLAGS=-lc \
			-DCMAKE_CXX_FLAGS="${CXXFLAGS} -DSYSCONFDIR=\\\"\${SYSCONFDIR}/gemrb\\\"" \
			-DDISABLE_WERROR=1

NO_TEST =		Yes

post-install:
	 cd ${PREFIX}/share/gemrb/GUIScripts/ && find * -name \*.py \
		-exec ${MODPY_BIN} ${MODPY_LIBDIR}/compileall.py \
		${PREFIX}/share/gemrb/GUIScripts/{} \;

.include <bsd.port.mk>
