# EOS systemd-boot

A package to enable systemd-boot automation using kernel-install on Arch-based distros

The kernel-install hooks were adapted from the AUR package originally written by Tilmann Meyer

The package basically does a few things:
* Overrides the mkinitcpio hooks to generate presets that work with kernel-install
* Installs hooks to automate the installation and removal of kernels using kernel-install
* Adds support for generating fallback images to kernel-install
* Saves kernel options to /etc/kernel/cmdline to support recovery in a chroot
