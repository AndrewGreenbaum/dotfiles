# Dotfiles

System configuration files.

## DNS over TLS

`dns-over-tls.conf` — systemd-resolved drop-in config that enables DNS over TLS with Cloudflare.

**Install:**
```bash
sudo cp dns-over-tls.conf /etc/systemd/resolved.conf.d/
sudo systemctl restart systemd-resolved
```
