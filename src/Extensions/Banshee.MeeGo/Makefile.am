ASSEMBLY = Banshee.MeeGo
TARGET = library
LINK = $(REF_EXTENSION_MEEGO) $(LINK_EXTENSION_PLAYQUEUE_DEPS)
INSTALL_DIR = $(EXTENSIONS_INSTALL_DIR)

@INTLTOOL_DESKTOP_RULE@

SOURCES =  \
	Banshee.MeeGo/MediaPanelContents.cs \
	Banshee.MeeGo/MeeGoHeaderBox.cs \
	Banshee.MeeGo/MeeGoPanel.cs \
	Banshee.MeeGo/MeeGoService.cs \
	Banshee.MeeGo/MeeGoTheme.cs \
	Banshee.MeeGo/MeeGoTrackInfoDisplay.cs \
	Banshee.MeeGo/PlaybackBox.cs \
	Banshee.MeeGo/SearchEntry.cs \
	MeeGo.Panel/PanelButtonState.cs \
	MeeGo.Panel/PanelClient.cs \
	MeeGo.Panel/PanelGtk.cs \
	MeeGo.Panel/SetPositionHandler.cs \
	MeeGo.Panel/SetSizeHandler.cs

RESOURCES = Banshee.MeeGo.addin.xml

if HAVE_MEEGO

include $(top_srcdir)/build/build.mk

module_SCRIPTS += Banshee.MeeGo.dll.config

paneldir = $(libexecdir)
panel_SCRIPTS = meego-panel-banshee

servicedir = $(datadir)/dbus-1/services
service_DATA = com.meego.UX.Shell.Panels.banshee.service

com.meego.UX.Shell.Panels.banshee.service: com.meego.UX.Shell.Panels.banshee.service.in $(top_builddir)/config.log
	sed -e "s|\@libexecdir\@|$(libexecdir)|" $< > $@

desktopfiles_in_files = meego-panel-banshee.desktop.in
desktopfiles_files = $(desktopfiles_in_files:.desktop.in=.desktop)
desktopfilesdir = $(MEEGO_PANELS_DIR)
desktopfiles_DATA = $(desktopfiles_files)

%.desktop.in: %.desktop.in.in Makefile
	sed -e "s|\@libexecdir\@|$(libexecdir)|" $< > $@

else
include $(top_srcdir)/build/build.dist.mk
endif

clean-local:
	rm -f com.meego.UX.Shell.Panels.banshee.service \
		meego-panel-banshee.desktop \
		meego-panel-banshee.desktop.in

EXTRA_DIST += \
	Banshee.MeeGo.dll.config \
	meego-panel-banshee \
	com.meego.UX.Shell.Panels.banshee.service.in \
	meego-panel-banshee.desktop.in.in
