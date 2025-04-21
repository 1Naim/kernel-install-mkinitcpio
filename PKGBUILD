# Maintainer: Eric Naim <dnaim@cachyos.org

pkgname=kernel-install-mkinitcpio
pkgver=2.0.pre4
pkgrel=1
pkgdesc='A framework for enabling systemd-boot automation using kernel-install with mkinitcpio'
arch=(any)
url='https://github.com/1Naim/kernel-install-mkinitcpio'
license=('GPL-2.0-or-later')
depends=(
    'bash'
    'coreutils'
    'findutils'
    'grep'
    'sed'
    'systemd'
    'mkinitcpio'
)
optdepends=(
    'snapper: For bootable snapshot entries support'
)
makedepends=('git')
conflicts=('kernel-install-for-dracut' 'systemd-boot-manager')
source=("${pkgname}::git+${url}.git#tag=${pkgver}")
sha256sums=('a8cd2c7cfe55c995f0fd9b3d4f46a1900422af8aa8527a31fbda1969eb8c8cda')

package() {
    cd "${pkgname}"
    cp -a ./{usr,etc} "${pkgdir}"

    # This workaround is needed to match the behaviour of default mkinitcpio
    # kernel-install will fail to generate the kernel image and initrd when
    # mkinitcpio has a non-zero exit code (usually when modules are missing)
    install -Dm644 /usr/lib/kernel/install.d/50-mkinitcpio.install \
        -t "${pkgdir}/etc/kernel/install.d"
    sed -i 's#\^"${GENERATOR_CMD[@]}\" .*#\"${GENERATOR_CMD[@]}\" || true#' \
        "${pkgdir}/etc/kernel/install.d/50-mkinitcpio.install"
}
