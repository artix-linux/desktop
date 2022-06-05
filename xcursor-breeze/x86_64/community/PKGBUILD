# Maintainer: Nathan <ndowens@artixlinux.org>
# Contributor: goetzc
# Contributor: grimi

pkgname=xcursor-breeze
epoch=1
pkgver=5.19.1
pkgrel=1
pkgdesc="Breeze cursor theme (KDE Plasma 5). This package is for usage in non-KDE Plasma desktops."
arch=('any')
url="https://www.kde.org"
license=('GPL')
depends=('libxcursor')
conflicts=('breeze')
source=("http://download.kde.org/stable/plasma/${pkgver}/breeze-${pkgver}.tar.xz")
b2sums=('dcc597f5a7a834921cf91566b503f93d96fc94efc0d8c4bb1ec3cc3e65f341ebb53c8481ad62ef37459af5b95b99ca7fbbc3bcf6dcd1a7dd1cb6cec7fee1a08e')

package() {
  install -dm755 "$pkgdir"/usr/share/icons/
  cp -r "$srcdir"/breeze-${pkgver}/cursors/{Breeze/Breeze,Breeze_Snow}           "$pkgdir"/usr/share/icons/
}
