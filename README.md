# ss-rust-pkgbuild
---
### Purpose repository
This repository was primarily done for myself. I use this software. Before it was created, [this repository](https://github.com/naruto522ru/shadowsocks-rust-PKGBUILD) in [AUR](https://aur.archlinux.org/) was not a binary, and there is still no stable branch. There is no software on Rust. Not every computer compile someone can use the binary version of this software.

### How to switch between build a binary version and not binary package?
**Answer:**
>git checkout binary #Binary version

>git checkout source #Source version

### How exactly to collect the package?
Depending on which the version you need on that branch and switch.

For binary version command in the terminal such:
>makepkg -scC

For source version command in the terminal such:
>makepkg -scCr

### How to install?
>sudo pacman -U PACKAGE
