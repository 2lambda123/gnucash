
AM_CPPFLAGS = \
  -I${top_srcdir} \
  -I${top_srcdir}/src \
  -I${top_srcdir}/src/gnc-module \
  -I${top_srcdir}/src/test-core \
  -I${top_srcdir}/src/engine \
  -I${top_srcdir}/src/engine/test-core \
  -I${top_srcdir}/src/libqof/qof \
  -I${top_srcdir}/src/core-utils \
  ${GUILE_INCS} \
  ${GLIB_CFLAGS}

LDADD = \
  ${top_builddir}/src/libqof/qof/libgnc-qof.la \
  ${top_builddir}/src/gnc-module/libgnc-module.la \
  ${top_builddir}/src/test-core/libtest-core.la \
  ../libgncmod-engine.la \
  ../test-core/libgncmod-test-engine.la \
  ${top_builddir}/src/core-utils/libgnc-core-utils.la \
  ${GLIB_LIBS}

# these tests are ordered kind more or less in the order
# that they should be executed, with more basic tests coming first.
#
TESTS = \
  test-link \
  test-load-engine \
  test-guid \
  test-numeric \
  test-date \
  test-object \
  test-commodities \
  test-create-account \
  test-account-object \
  test-group-vs-book \
  test-lots \
  test-period \
  test-querynew \
  test-query \
  test-recursive \
  test-split-vs-account  \
  test-transaction-reversal \
  test-transaction-voiding \
  test-recurrence \
  test-scm-query

GNC_TEST_DEPS = \
  --gnc-module-dir ${top_builddir}/src/engine \
  --guile-load-dir ${top_builddir}/src/gnc-module \
  --guile-load-dir ${top_builddir}/src/engine \
  --library-dir    ${top_builddir}/src/libqof/qof \
  --library-dir    ${top_builddir}/src/core-utils \
  --library-dir    ${top_builddir}/src/gnc-module \
  --library-dir    ${top_builddir}/src/engine \
  --library-dir    ${top_builddir}/src/backend/xml \
  --library-dir    ${top_builddir}/src/backend/sql

TESTS_ENVIRONMENT = \
  GUILE_WARN_DEPRECATED=no \
  GUILE="${GUILE}" \
  SRCDIR=${srcdir} \
  GNC_BUILDDIR=`\cd ${top_builddir} && pwd` \
  $(shell ${top_builddir}/src/gnc-test-env --no-exports ${GNC_TEST_DEPS})

check_PROGRAMS = \
  test-link \
  test-commodities \
  test-date \
  test-recurrence \
  test-guid \
  test-account-object \
  test-group-vs-book \
  test-load-engine \
  test-period \
  test-lots \
  test-numeric \
  test-object \
  test-query \
  test-querynew \
  test-recursive \
  test-scm-query \
  test-split-vs-account \
  test-transaction-reversal \
  test-transaction-voiding


test_link_SOURCES = test-link.c
test_link_LDADD = ../libgncmod-engine.la \
  ${top_builddir}/src/libqof/qof/libgnc-qof.la \
  ${top_builddir}/src/core-utils/libgnc-core-utils.la

EXTRA_DIST = \
  test-create-account \
  test-create-account.scm \
  test-scm-query-import \
  test-scm-query-import.scm

clean-local:
	rm -f translog.*

distclean-local: clean-local
