pkglib_LTLIBRARIES = libgncmod-business-utils.la

AM_CPPFLAGS = \
  -I${top_srcdir}/src \
  -I${top_builddir}/src \
  -I${top_srcdir}/src/engine \
  -I${top_srcdir}/src/gnc-module \
  -I${top_srcdir}/src/libqof/qof \
  ${GUILE_INCS} \
  ${GLIB_CFLAGS} \
  ${GNOME_CFLAGS}

libgncmod_business_utils_la_SOURCES = \
  gncmod-business-utils.c

libgncmod_business_utils_la_LDFLAGS = -avoid-version

libgncmod_business_utils_la_LIBADD = \
  ${top_builddir}/src/gnc-module/libgnc-module.la \
  ${top_builddir}/src/libqof/qof/libgnc-qof.la \
  ${GUILE_LIBS} \
  ${GLIB_LIBS} \
  ${EFENCE_LIBS}

# Guile Modules
gncmoddir = ${GNC_SHAREDIR}/guile-modules/gnucash
gncmod_DATA = business-utils.scm

# For regular scheme definitions
gncscmdir = ${GNC_SHAREDIR}/scm
gncscm_DATA = \
  business-options.scm \
  business-prefs.scm

EXTRA_DIST = \
  ${gncscm_DATA} \
  ${gncmod_DATA}

noinst_DATA = .scm-links

if GNUCASH_SEPARATE_BUILDDIR
SCM_FILE_LINKS = business-utils.scm \
  ${gncscm_DATA}
endif

.scm-links: 
	$(RM) -rf gnucash
	mkdir -p  gnucash
if GNUCASH_SEPARATE_BUILDDIR
	for X in ${SCM_FILE_LINKS} ; do \
	  $(LN_S) -f ${srcdir}/$$X . ; \
	done
endif
	( cd gnucash; for A in $(gncmod_DATA) ; do $(LN_S) -f ../$$A . ; done )
if ! OS_WIN32
# Windows knows no "ln -s" but uses "cp": must copy every time (see bug #566567).
	touch .scm-links
endif

clean-local:
	$(RM) -rf gnucash

CLEANFILES = .scm-links
DISTCLEANFILES = ${SCM_FILE_LINKS}

AM_CPPFLAGS += -DG_LOG_DOMAIN=\"gnc.business.utils\"
