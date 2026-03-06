# Demo Script (Dotfiles)

## Goal
Show practical operational discipline on system config changes.

## Flow

1. Explain intent of the config and risk surface.
2. Show install command path.
3. Validate effective resolver config.
4. Demonstrate rollback command.

## Commands

```bash
sudo cp dns-over-tls.conf /etc/systemd/resolved.conf.d/
sudo systemctl restart systemd-resolved
resolvectl status
```

Rollback:
```bash
sudo rm -f /etc/systemd/resolved.conf.d/dns-over-tls.conf
sudo systemctl restart systemd-resolved
```
