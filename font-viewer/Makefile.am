
AM_CPPFLAGS = $(FONT_VIEWER_CFLAGS) $(MATECC_CAPPLETS_CFLAGS) -DDIRECTORY_DIR=\"$(directorydir)\" \
  -DMATELOCALEDIR=\"$(datadir)/locale\"

bin_PROGRAMS = mate-thumbnail-font mate-font-viewer

font_loader_SOURCES = \
	sushi-font-loader.h \
	sushi-font-loader.c

mate_thumbnail_font_LDADD = $(MATECC_CAPPLETS_LIBS) -lm $(FONT_VIEWER_LIBS)
mate_thumbnail_font_SOURCES = \
	$(font_loader_SOURCES) \
	font-thumbnailer.c \
	totem-resources.c \
	totem-resources.h

mate_font_viewer_LDADD = $(MATECC_CAPPLETS_LIBS) -lm $(FONT_VIEWER_LIBS)
mate_font_viewer_SOURCES = \
	$(font_loader_SOURCES) \
	font-model.h \
	font-model.c \
	font-utils.h \
	font-utils.c \
	gd-main-toolbar.h \
	gd-main-toolbar.c \
	sushi-font-widget.h \
	sushi-font-widget.c \
	font-view.c

thumbnailerdir = $(datadir)/thumbnailers
thumbnailer_DATA = mate-font-viewer.thumbnailer

desktopdir = $(datadir)/applications
desktop_in_files = mate-font-viewer.desktop.in
desktop_DATA = $(desktop_in_files:.desktop.in=.desktop)

install-data-local: install-desktop-database

install-desktop-database: install-desktopDATA
	update-desktop-database $(DESTDIR)$(desktopdir)

uninstall-local:
	rm -f $(DESTDIR)$(desktopdir)/mimeinfo.cache

@INTLTOOL_DESKTOP_RULE@
@INTLTOOL_DIRECTORY_RULE@
@INTLTOOL_SCHEMAS_RULE@

CLEANFILES = $(desktop_DATA) \
  $(schemas_DATA) $(directory_DATA)

EXTRA_DIST = \
  $(thumbnailer_DATA) \
  $(desktop_in_files)

-include $(top_srcdir)/git.mk
