# Engineering Decisions (Dotfiles)

## 1) Keep changes minimal and auditable
I only track high-value system changes with clear rollback paths.
Tradeoff: fewer convenience tweaks in repo.

## 2) Explicit install/rollback commands in docs
Operational clarity is prioritized over clever scripting.
Tradeoff: manual steps instead of one-click automation.

## 3) Avoid machine-specific secret material
No private key paths or credentials in config/docs.
Tradeoff: setup is slightly less turnkey.
