# EOS systemd-boot

A package to enable systemd-boot automation using kernel-install on Arch-based distros

The kernel-install hooks were adapted from the AUR package originally written by Tilmann Meyer

The package does a few things:
* Overrides the mkinitcpio hooks to generate presets that work with kernel-install
* Installs hooks to automate the installation and removal of kernels using kernel-install
* Adds support for generating fallback images to kernel-install
* Saves kernel options to /etc/kernel/cmdline to support recovery in a chroot

## NOTE: While this package was initially developed for EndeavourOS, there is nothing specific to EOS in it.  It should work with any Arch-based distro.
