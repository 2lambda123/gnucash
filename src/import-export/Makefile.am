if WITH_OFX
    OFX_DIR=ofx
endif
if WITH_AQBANKING
    AQBANKING_DIR=aqbanking
endif
SUBDIRS = . schemas qif qif-import \
	${OFX_DIR} ${AQBANKING_DIR} log-replay test csv

pkglib_LTLIBRARIES=libgncmod-generic-import.la

libgncmod_generic_import_la_SOURCES = \
	import-account-matcher.c \
	import-commodity-matcher.c \
	import-backend.c \
	import-format-dialog.c \
	import-match-picker.c \
	import-parse.c \
	import-utilities.c \
	import-settings.c \
	import-match-map.c \
	import-main-matcher.c \
	gnc-import-desc-format.c \
	gnc-import-format-cb.c \
	gnc-import-format-gnome.c \
	gncmod-generic-import.c

gncincludedir = ${GNC_INCLUDE_DIR}
gncinclude_HEADERS = \
  import-match-map.h \
  gnc-import-desc-format.h \
  gnc-import-format-cb.h \
  import-parse.h

noinst_HEADERS = \
  import-account-matcher.h \
  import-backend.h \
  import-commodity-matcher.h \
  import-main-matcher.h \
  import-match-map.h \
  import-match-picker.h \
  import-settings.h \
  import-utilities.h \
  gnc-import-format-gnome.h

libgncmod_generic_import_la_LDFLAGS = -avoid-version

libgncmod_generic_import_la_LIBADD = \
  ${top_builddir}/src/gnome-utils/libgncmod-gnome-utils.la \
  ${top_builddir}/src/app-utils/libgncmod-app-utils.la \
  ${top_builddir}/src/engine/libgncmod-engine.la \
  ${top_builddir}/src/core-utils/libgnc-core-utils.la \
  ${top_builddir}/src/gnc-module/libgnc-module.la \
  ${top_builddir}/src/libqof/qof/libgnc-qof.la \
  ${GNOME_LIBS} \
  ${GLADE_LIBS} \
  ${REGEX_LIBS} \
  ${GLIB_LIBS}

gladedir = ${GNC_GLADE_DIR}
glade_DATA = \
  generic-import.glade \
  import-provider-format.glade

AM_CPPFLAGS = \
  -I${top_srcdir}/src \
  -I${top_srcdir}/src/core-utils \
  -I${top_srcdir}/src/engine \
  -I${top_srcdir}/src/gnc-module \
  -I${top_srcdir}/src/app-utils \
  -I${top_srcdir}/src/gnome \
  -I${top_srcdir}/src/gnome-utils \
  -I${top_srcdir}/src/libqof/qof \
  ${GNOME_CFLAGS} \
  ${GLADE_CFLAGS} \
  ${GUILE_INCS} \
  ${GLIB_CFLAGS}

EXTRA_DIST = \
  $(glade_DATA) \
  generic-import-design.txt

AM_CPPFLAGS += -DG_LOG_DOMAIN=\"gnc.i-e\"
