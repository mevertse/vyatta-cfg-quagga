share_perl5dir = /opt/vyatta/share/perl5/Vyatta/Quagga
cfgdir = $(datadir)/vyatta-cfg/templates
bin_sudo_usersdir = $(bindir)/sudo-users
curverdir = $(sysconfdir)/config-migrate/current
gentmpdir = generated-templates

sbin_SCRIPTS = scripts/bgp/vyatta-bgp.pl
sbin_SCRIPTS += scripts/policy/vyatta-policy.pl
sbin_SCRIPTS += scripts/vyatta_quagga_utils.pl
sbin_SCRIPTS += scripts/policy/vyatta-check-as-prepend.pl
sbin_SCRIPTS += scripts/vyatta-policy-action-verify.pl
sbin_SCRIPTS += scripts/vyatta-gateway-static_route-check.pl
sbin_SCRIPTS += scripts/vyatta-link-detect
sbin_SCRIPTS += scripts/vyatta-next-hop-check
sbin_SCRIPTS += scripts/vyatta-update-static-route.pl
sbin_SCRIPTS += scripts/vyos-update-rpki-cache.py

bin_sudo_users_SCRIPTS = scripts/vyatta-static-dhcp.pl

share_perl5_DATA = lib/Vyatta/Quagga/Config.pm

src_check_prefix_boundary = src/check_prefix_boundary.c

curver_DATA = cfg-version/quagga@3

cpiop = find  . ! -regex '\(.*~\|.*\.bak\|.*\.swp\|.*\#.*\#\)' -print0 | \
	cpio -0pd

all-local:
	rm -rf $(gentmpdir)
	./gen-interface-templates.pl $(gentmpdir)

clean-local:
	rm -rf $(gentmpdir)

install-exec-hook:
	mkdir -p $(DESTDIR)$(cfgdir)
	cd templates; $(cpiop) $(DESTDIR)$(cfgdir)
	cd $(gentmpdir); $(cpiop) $(DESTDIR)$(cfgdir)
