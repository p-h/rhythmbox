NULL =

plugindir = $(PLUGINDIR)/mpris
plugin_LTLIBRARIES = libmpris.la

libmpris_la_SOURCES = \
	rb-mpris-plugin.c				\
	mpris-spec.h					\
	$(NULL)

libmpris_la_LDFLAGS = $(PLUGIN_LIBTOOL_FLAGS)
libmpris_la_LIBTOOLFLAGS = --tag=disable-static

libmpris_la_LIBADD =					\
	$(top_builddir)/shell/librhythmbox-core.la	\
	$(NULL)

AM_CPPFLAGS = 						\
        -DGNOMELOCALEDIR=\""$(datadir)/locale"\"        \
	-DG_LOG_DOMAIN=\"Rhythmbox\"		 	\
	-I$(top_srcdir) 				\
	-I$(top_builddir)	   			\
	-DPIXMAP_DIR=\""$(datadir)/pixmaps"\"		\
	-DSHARE_DIR=\"$(pkgdatadir)\"                   \
	-DDATADIR=\""$(datadir)"\"			\
	$(RHYTHMBOX_CFLAGS)				\
	$(NULL)

plugin_in_files = mpris.plugin.in

%.plugin: %.plugin.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*po) ; $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache

plugin_DATA = $(plugin_in_files:.plugin.in=.plugin)

EXTRA_DIST = $(plugin_in_files)

CLEANFILES = $(plugin_DATA)
DISTCLEANFILES = $(plugin_DATA)
