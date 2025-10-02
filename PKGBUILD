# Maintainer: Antonio Medeiros <linuxkamarada@gmail.com>
# Contributor: Philip Müller <philm[at]manjaro[dog]org>
# Contributor: artoo <artoo@manjaro.org>
# Contributor: anex <assassin.anex[@]gmail.com>
# Contributor: Stefano Capitani <stefano@manjaro.org>
# Contributor: Matti Hyttinen <matti@manjaro.org> 

pkgbase=grub-theme-kamarada-src
pkgname=('grub-theme-live-common' 'grub-theme-live-kamarada' 'grub-theme-kamarada')
pkgver=20.2
pkgrel=16
pkgdesc="Linux Kamarada GRUB theme"
arch=('any')
url="https://github.com/kamarada/grub-theme-kamarada-src"
license=('GPL-3.0-or-later')
makedepends=('git')
_commit=4fd6761d889cd49e8a815f71696f31d1d576b7da
source=("git+$url.git#commit=$_commit")
sha256sums=('SKIP') # TODO

package_grub-theme-live-common() {
  pkgdesc+=" for live ISO (common files)"
  depends=('grub')
  conflicts=('grub-theme-live')
  replaces=('grub-theme-live')

  cd "$pkgbase"
  make PREFIX=/usr DESTDIR="${pkgdir}" install_common
}
package_grub-theme-live-kamarada() {
  pkgdesc+=" for live ISO"
  depends=('grub-theme-live-common')

  cd "$pkgbase"
  make PREFIX=/usr DESTDIR="${pkgdir}" install_kamarada
}

package_grub-theme-kamarada() {
  depends=('grub')
  install=kamarada-theme.install

  cd "$pkgbase/kamarada-live"

  find . -type f -exec install -D -m644 {} "${pkgdir}"/usr/share/grub/themes/kamarada/{} \;
}
