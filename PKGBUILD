# Maintainer: Eric Naim <dnaim@cachyos.org

pkgname=kernel-install-mkinitcpio
pkgver=1.9
pkgrel=2
pkgdesc='A framework for enabling systemd-boot automation using kernel-install with mkinitcpio'
arch=(any)
url='https://github.com/1Naim/kernel-install-mkinitcpio'
license=('GPL-2.0-or-later')
depends=('systemd' 'mkinitcpio')
makedepends=('git')
conflicts=('kernel-install-for-dracut')
source=("${pkgname}::git+${url}.git#tag=${pkgver}")
sha256sums=('b5239bdb3829248c40b96d1ed34c55269d563872b3d8edd439e77afc1178feca')

package() {
    cd "${pkgname}"
    git cherry-pick -n f9ec2c6d059f0620ce804e9d850a76d575f712bb
    cp -a src/{usr,etc} "${pkgdir}"

    # This workaround is needed to match the behaviour of default mkinitcpio
    # kernel-install will fail to generate the kernel image and initrd when
    # mkinitcpio has a non-zero exit code (usually when modules are missing)
    install -Dm644 /usr/lib/kernel/install.d/50-mkinitcpio.install \
        -t "${pkgdir}/etc/kernel/install.d"
    sed -i 's#\^"${GENERATOR_CMD[@]}\" .*#\"${GENERATOR_CMD[@]}\" || true#' \
        "${pkgdir}/etc/kernel/install.d/50-mkinitcpio.install"
}
