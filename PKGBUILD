# Maintainer: Philip Müller <philm[at]manjaro[dog]org>
# Contributor: artoo <artoo@manjaro.org>
# Contributor: anex <assassin.anex[@]gmail.com>
# Contributor: Stefano Capitani <stefano@manjaro.org>
# Contributor: Matti Hyttinen <matti@manjaro.org> 


pkgbase=grub-theme-live
pkgname=('grub-theme-live-common' 'grub-theme-live-manjaro' 'grub-theme-manjaro')
pkgver=20.2
pkgrel=13
_commit=10b18d066e39354b3d6cca4e05ff18adba96f9fc

pkgdesc='Manjaro Linux grub theme'
arch=('any')
url="https://gitlab.manjaro.org/artwork/branding/grub-theme"
license=('GPL')
makedepends=('git')
source=("git+$url.git#commit=$_commit")
sha256sums=('SKIP')

package_grub-theme-live-common() {
    depends=('grub')
    conflicts=('grub-theme-live')
    replaces=('grub-theme-live')

    cd grub-theme
    make PREFIX=/usr DESTDIR=${pkgdir} install_common
}
package_grub-theme-live-manjaro() {
    depends=('grub-theme-live-common')

    cd grub-theme
    make PREFIX=/usr DESTDIR=${pkgdir} install_manjaro
}

package_grub-theme-manjaro() {
    depends=('grub')
    install=manjaro-theme.install

    cd grub-theme/manjaro-live
    sed -i -e 's,.*text = "Welcome to Manjaro".*,#text = "Welcome to Manjaro",' theme.txt #remove welcome message
    find . -type f -exec install -D -m644 {} ${pkgdir}/usr/share/grub/themes/manjaro/{} \;
}
