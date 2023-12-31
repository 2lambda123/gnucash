SUBDIRS = examples

docdir = ${GNC_DOC_INSTALL_DIR}
doc_DATA = \
  README.francais \
  README.german \
  README-de.win32-bin.txt \
  README-fr.win32-bin.txt \
  README-it.win32-bin.txt \
  README-lv.win32-bin.txt \
  README-nl.win32-bin.txt \
  README-zh_CN.win32-bin.txt \
  README-zh_TW.win32-bin.txt \
  README.win32-bin.txt \
  guile-hackers.txt \
  projects.html 

man_MANS = \
  gnucash.1

tipsdir = $(GNC_SHAREDIR)
tips_DATA = tip_of_the_day.list

EXTRA_DIST = \
  ${doc_DATA} \
  misc-notes.txt \
  README.build-system \
  README.HBCI \
  README.OFX \
  README.translator.txt \
  TRANSLATION_HOWTO \
  build-aix.txt \
  build-solaris.txt \
  generic_objects.txt \
  gnome-hackers.txt \
  gnucash.1.in \
  gtkrc-2.0.gnucash \
  tip_of_the_day.list.in

## We borrow guile's convention and use @-...-@ as the substitution
## brackets here, instead of the usual @...@.  This prevents autoconf
## from substituting the values directly into the left-hand sides of
## the sed substitutions.
gnucash.1: gnucash.1.in Makefile
	rm -f $@.tmp
	${SED} < $< > $@.tmp \
            -e 's:@-VERSION-@:${VERSION}:g' \
            -e 's:@-DATE-@:$(shell date +'%B %Y'):g'
	chmod +x $@.tmp
	mv $@.tmp $@

tip_of_the_day.list: tip_of_the_day.list.in Makefile
	${CC} -E -P -x c -D'N_(x)=x' -o $@.tmp $<
	cat -s $@.tmp | ${SED} -e 's/^ *"//' \
	                       -e 's/"* *[|] */|/' \
                           -e 's:@-GNUCASH_LATEST_STABLE_SERIES-@:${GNUCASH_LATEST_STABLE_SERIES}:g' > $@
	rm -f $@.tmp
if PLATFORM_WIN32
	perl -pi.bak -e 's/" *$$//' $@
else
	perl -pi.bak -e 's/" *$$/\n/' $@
endif

DISTCLEANFILES = gnc-prices.1 gnucash.1 tip_of_the_day.list *.bak
