AM_CFLAGS = -O2 -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wreturn-type -Wcast-align

bin_PROGRAMS = mochad
mochad_SOURCES = mochad.c decode.c encode.c global.c x10state.c x10_write.c \
		 decode.h encode.h global.h x10state.h x10_write.h
EXTRA_DIST = udev/91-usb-x10-controllers.rules udev/91-usb-x10-controllers.rules-systemd \
	     hotplug2/20-usb-x10 hotplug2/mochad systemd/mochad.service \
	     cgi/x10.pl cgi/netcat.pl cgi/getsensors.pl cgi/cgi-lib.pl \
	     apps/mochamon.pl apps/simplemon.pl apps/bash.sh \
	     apps/rfsectopl3.pl apps/x10-tk.py apps/mochad.scr

install-exec-hook:
	if test -d /lib/systemd/system -a -x /bin/systemctl ; then \
		cp $(abs_top_srcdir)/systemd/mochad.service /lib/systemd/system ; \
		cp $(abs_top_srcdir)/udev/91-usb-x10-controllers.rules-systemd /etc/udev/rules.d/91-usb-x10-controllers.rules ; \
	else \
		if test -d /etc/udev/rules.d ; then \
			cp $(abs_top_srcdir)/udev/91-usb-x10-controllers.rules /etc/udev/rules.d ; \
		fi ; \
	fi ;
	if test -d /etc/hotplug.d/usb ; then \
		cp $(abs_top_srcdir)/hotplug2/20-usb-x10 /etc/hotplug.d/usb ; \
		cp $(abs_top_srcdir)/hotplug2/mochad /etc/init.d ; \
	fi
