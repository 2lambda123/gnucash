SUBDIRS = . test

pkglib_LTLIBRARIES=libgncmod-ofx.la

libgncmod_ofx_la_SOURCES = \
  gnc-ofx-import.c \
  gnc-ofx-kvp.c \
  gncmod-ofx-import.c \
  gnc-plugin-ofx.c

noinst_HEADERS = \
  gnc-ofx-import.h \
  gnc-ofx-kvp.h \
  gnc-plugin-ofx.h

libgncmod_ofx_la_LDFLAGS = -avoid-version

libgncmod_ofx_la_LIBADD = \
  ${top_builddir}/src/import-export/libgncmod-generic-import.la \
  ${top_builddir}/src/gnome-utils/libgncmod-gnome-utils.la \
  ${top_builddir}/src/app-utils/libgncmod-app-utils.la \
  ${top_builddir}/src/engine/libgncmod-engine.la \
  ${top_builddir}/src/core-utils/libgnc-core-utils.la \
  ${top_builddir}/src/gnc-module/libgnc-module.la \
  ${top_builddir}/src/libqof/qof/libgnc-qof.la \
  ${GLIB_LIBS} \
  ${LIBOFX_LIBS}

AM_CPPFLAGS = \
  -I${top_srcdir}/src \
  -I${top_srcdir}/src/core-utils \
  -I${top_srcdir}/src/engine \
  -I${top_srcdir}/src/gnc-module \
  -I${top_srcdir}/src/app-utils \
  -I${top_srcdir}/src/gnome \
  -I${top_srcdir}/src/gnome-utils \
  -I${top_srcdir}/src/import-export \
  -I${top_srcdir}/src/libqof/qof \
  ${GNOME_CFLAGS} \
  ${GLADE_CFLAGS} \
  ${GUILE_INCS} \
  ${GLIB_CFLAGS} \
  ${LIBOFX_CFLAGS} 

uidir = $(GNC_UI_DIR)
ui_DATA = \
	gnc-plugin-ofx-ui.xml

EXTRA_DIST = $(ui_DATA)

AM_CPPFLAGS += -DG_LOG_DOMAIN=\"gnc.import.ofx\"
