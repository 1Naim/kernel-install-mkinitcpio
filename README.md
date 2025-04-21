> [!NOTE]
> This repository is a fork of
> [dalto.8/eos-system-boot](https://gitlab.com/dalto.8/eos-systemd-boot). GitHub
> doesn't support forking from GitLab so no proper fork data is available. All
> original credits go to dalto and EndeavourOS

# kernel-install-mkinitcpio

This repository contains helper scripts and pacman hooks to make systemd-boot
and kernel-install a more seamless experience in Arch Linux-based installations.

## Features
* Overrides the mkinitcpio hooks to generate presets that work with kernel-install
* Installs hooks to automate the installation and removal of kernels using kernel-install and bootctl
* Script to update kernel commandline in entries by overriding with parameters
  from `/etc/kernel/cmdline`
* Create bootable snapshot entries if snapper is installed
* Calculate the checksum of generated initramfs and appends it to the filename
    * This is especially useful for snapshots because we can reuse existing
      initramfs if they are the same. This helps to save storage space.

## Acknowledgments

This section is dedicated to the various parties and projects that helped
improve this project, whether by idea, code, etc.

### EndeavourOS

[dalto8](https://github.com/dalto8) from EndeavourOS was the original author of
this project. It has since been forked but all original attributions go to them.

### OpenSUSE

The [entry
specification](https://github.com/openSUSE/sdbootutil/blob/main/ARCHITECTURE.md)
written by them served as a foundation for supporting bootable snapshot entries.
[The snapper plugin](./usr/lib/snapper/plugins/10-kim.snapper) was originally
also sourced from
[OpenSUSE/sdbootutil](https://github.com/openSUSE/sdbootutil/blob/main/10-sdbootutil.snapper)
and was rewritten to fit `kernel-install-mkinitcpio`'s ecosystem.
