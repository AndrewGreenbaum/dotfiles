# Linux DNS over TLS Configuration

A systemd-resolved drop-in that uses Cloudflare DNS over TLS. It is for Linux systems running systemd-resolved, not macOS.

Before installing, check that the service is active:

```sh
systemctl is-active systemd-resolved
resolvectl status
```

Back up any existing `/etc/systemd/resolved.conf.d/dns-over-tls.conf`. Then, from this repository:

```sh
sudo install -d /etc/systemd/resolved.conf.d
sudo install -m 0644 dns-over-tls.conf /etc/systemd/resolved.conf.d/dns-over-tls.conf
sudo systemctl restart systemd-resolved
resolvectl status
resolvectl query example.com
```

The `#cloudflare-dns.com` suffix sets the TLS server name. `DNSOverTLS=yes` requires encrypted connections for these servers, so name resolution can fail on networks that block the connection.

Per-link DNS from DHCP, NetworkManager, or a VPN can affect routing. Check `resolvectl status` for each link; this drop-in alone does not establish that every application uses encrypted DNS.

To undo the change, restore your previous drop-in (or remove this file if none existed) and restart systemd-resolved. Leave unrelated resolver settings in place.

Configuration reference: https://www.freedesktop.org/software/systemd/man/latest/resolved.conf.html

The configuration syntax was reviewed on macOS. Runtime DNS behavior still needs verification on a Linux system using systemd-resolved.
