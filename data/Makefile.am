include $(GLIB_MAKEFILE)

if HAVE_SYSTEMD
systemdsystemunit_DATA = \
	thermald.service
	thermald

thermald.service: thermald.service.in
	$(edit) $< >$@

thermald_msrfix.service: thermald_msrfix.service.in
	$(edit) $< >$@

thermald_msrfix.sh: thermald_msrfix.sh.in
	$(edit) $< >$@

servicedir = $(datadir)/dbus-1/system-services
service_in_files = org.freedesktop.thermald.service.in
service_DATA = $(service_in_files:.service.in=.service)

$(service_DATA): $(service_in_files) Makefile
	$(edit) $< >$@
endif

edit = sed \
	-e 's|@bindir[@]|$(bindir)|g' \
	-e 's|@sbindir[@]|$(sbindir)|g' \
	-e 's|@sysconfdir[@]|$(sysconfdir)|g' \
	-e 's|@localstatedir[@]|$(localstatedir)|g'

dbusservicedir = $(DBUS_SYS_DIR)
dbusservice_DATA = org.freedesktop.thermald.conf

tdconfigdir = $(tdconfdir)
tdconfig_DATA = \
	thermal-cpu-cdev-order.xml

EXTRA_DIST = \
	thermald.service.in \
	thermald_msrfix.service.in \
	thermald_msrfix.sh.in \
	org.freedesktop.thermald.service.in \
	$(dbusservice_DATA) \
	$(tdconfig_DATA)

CLEANFILES = thermald.service thermald_msrfix.service thermald_msrfix.sh org.freedesktop.thermald.service
