SUBDIRS = . test

pkglib_LTLIBRARIES = libgncmod-standard-reports.la

libgncmod_standard_reports_la_SOURCES = \
  gncmod-standard-reports.c

libgncmod_standard_reports_la_LDFLAGS = -avoid-version

libgncmod_standard_reports_la_LIBADD = \
  ${top_builddir}/src/gnc-module/libgnc-module.la \
  ${GUILE_LIBS} \
  ${GLIB_LIBS}

AM_CPPFLAGS = \
  -I${top_srcdir}/src \
  -I${top_srcdir}/src/gnc-module \
  ${GUILE_INCS} \
  ${GLIB_CFLAGS}

gncscmmoddir = ${GNC_SHAREDIR}/guile-modules/gnucash/report/
gncscmmod_DATA = \
   standard-reports.scm

gncscmreportmoddir = ${GNC_SHAREDIR}/guile-modules/gnucash/report/standard-reports
gncscmreportmod_DATA = \
   account-piecharts.scm \
   account-summary.scm \
   advanced-portfolio.scm \
   average-balance.scm \
   balance-sheet.scm \
   budget.scm \
   budget-balance-sheet.scm \
   budget-barchart.scm \
   budget-flow.scm \
   budget-income-statement.scm \
   cash-flow.scm \
   category-barchart.scm \
   daily-reports.scm \
   equity-statement.scm \
   net-barchart.scm \
   income-statement.scm \
   portfolio.scm \
   price-scatter.scm \
   register.scm \
   trial-balance.scm \
   general-journal.scm \
   general-ledger.scm \
   transaction.scm \
   sx-summary.scm \
   net-linechart.scm

if GNUCASH_SEPARATE_BUILDDIR
#For executing test cases
SCM_FILE_LINKS = ${gncscmmod_DATA} ${gncscmreportmod_DATA}
endif

.scm-links:
	$(RM) -rf gnucash
	mkdir -p  gnucash
	mkdir -p  gnucash/report
	mkdir -p  gnucash/report/standard-reports
if GNUCASH_SEPARATE_BUILDDIR
	for X in ${SCM_FILE_LINKS} ; do \
	  $(LN_S) -f ${srcdir}/$$X . ; \
	done
endif
	( cd gnucash/report; for A in $(gncscmmod_DATA) ; do $(LN_S) -f ../../$$A . ; done )
	( cd gnucash/report/standard-reports; for A in $(gncscmreportmod_DATA) ; do $(LN_S) -f ../../../$$A . ; done )
if ! OS_WIN32
# Windows knows no "ln -s" but uses "cp": must copy every time (see bug #566567).
	touch .scm-links
endif

clean-local:
	$(RM) -rf gnucash

noinst_DATA = .scm-links

EXTRA_DIST = ${gncscmmod_DATA} ${gncscmreportmod_DATA}

CLEANFILES = .scm-links
DISTCLEANFILES = ${SCM_FILE_LINKS}

AM_CPPFLAGS += -DG_LOG_DOMAIN=\"gnc.report.standard\"
