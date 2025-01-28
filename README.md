# 🖥️ Neovim Nightly Binary for Arch Linux

This is a `PKGBUILD` for _Arch Linux_ that downloads and packages the latest
official nightly build of Neovim.

Based on the AUR package:
[neovim-nightly-bin](https://aur.archlinux.org/packages/neovim-nightly-bin).

## Differences from the AUR Package

- **No dependency on `hicolor-icon-theme`**: Seriously, it's a terminal-based
text editor. Why would it need that?

- **Correct license references**: Ensures the appropriate licenses are cited.

- **Avoids loading global `vim` packages**: Only loads packages specific to
`neovim`.
