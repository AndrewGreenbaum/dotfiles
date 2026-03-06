# Dotfiles

Small, explicit system configuration repository for my local environment.

## What’s Here

- `dns-over-tls.conf`: systemd-resolved drop-in enabling DNS-over-TLS.
- Security baseline docs (`SECURITY.md`) and process notes.

## Why This Exists

I keep system-level tweaks versioned so they are reviewable, reversible, and reproducible across reinstalls.

## Install

```bash
sudo mkdir -p /etc/systemd/resolved.conf.d
sudo cp dns-over-tls.conf /etc/systemd/resolved.conf.d/
sudo systemctl restart systemd-resolved
```

## Verify

```bash
resolvectl status | sed -n '1,120p'
```

## Rollback

```bash
sudo rm -f /etc/systemd/resolved.conf.d/dns-over-tls.conf
sudo systemctl restart systemd-resolved
```

## Tradeoffs

- Privacy/integrity gain from encrypted DNS.
- Dependency on compatible resolver behavior and network path.

## Interview Talking Points

- Why I version infra/system config, not just app code.
- How I validate and rollback low-level config safely.
