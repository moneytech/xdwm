#
# Makefile
# Adrian Perez, 2011-12-14 11:51
#

DESTDIR ?=
RST2MAN ?= rst2man
PREFIX ?= /usr/local

XSESSIONS_DIR = $(PREFIX)/share/xsessions
BINDIR        = $(PREFIX)/bin
MANDIR        = $(PREFIX)/share/man

all: xdwm-session.1.gz

%.gz: %
	gzip -9c $< > $@

xdwm-session.1: xdwm-session.rst
	$(RST2MAN) $< $@

install: all
	install -m 755 -d $(DESTDIR)$(XSESSIONS_DIR)
	install -m 644 -t $(DESTDIR)$(XSESSIONS_DIR) xdwm.desktop
	install -m 755 -d $(DESTDIR)$(BINDIR)
	install -m 755 -t $(DESTDIR)$(BINDIR) xdwm-session
	install -m 755 -d $(DESTDIR)$(MANDIR)/man1
	install -m 644 -t $(DESTDIR)$(MANDIR)/man1 xdwm-session.1.gz
	install -m 755 -d $(DESTDIR)/etc/xdg/xdwm
	install -m 644 -t $(DESTDIR)/etc/xdg/xdwm rc.example

uninstall:
	rm -f $(DESTDIR)$(XSESSIONS_DIR)/xdwm.desktop
	rm -f $(DESTDIR)$(BINDIR)/xdwm-session

clean:
	$(RM) xdwm-session.1.gz

.PHONY: install uninstall clean

# vim:ft=make
#
