# Resolver security notes

This repository contains a systemd-resolved configuration, with no service,
accounts or application credentials to rotate.

`DNSOverTLS=yes` requires TLS for the configured resolver connection. It does
not encrypt application traffic or prevent a VPN, per-link DNS setting, or
application-specific resolver from using a different route. Check
`resolvectl status` after changing networks and verify the behavior you need.

For a configuration problem, include your distribution, systemd version and
relevant resolver settings in an issue. Remove private search domains,
internal hostnames and other network details before posting diagnostics.
