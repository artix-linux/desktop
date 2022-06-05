# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Ionut Biru <ibiru@archlinux.org>
# Contributor: Kessia 'even' Pinheiro <kessiapinheiro at gmail.com
# Contributor: Bjorn Lindeijer <bjorn lindeijer nl>

pkgname=telepathy-glib
pkgver=0.24.2
pkgrel=2.1
pkgdesc="GLib bindings for the Telepathy D-Bus protocol"
arch=(x86_64)
url="http://telepathy.freedesktop.org"
license=(LGPL2.1)
depends=(dbus-glib)
makedepends=(libxslt vala gobject-introspection python)
source=(https://telepathy.freedesktop.org/releases/$pkgname/$pkgname-$pkgver.tar.gz)
sha256sums=('e32097e8609d87b2de137a6418e4c4f8409886eada3bb5f6e7795cbaa0c8653c')

build() {
  cd $pkgname-$pkgver
  ./configure --prefix=/usr \
      --libexecdir=/usr/lib/telepathy \
      --enable-vala-bindings \
      --enable-static=no
  make
}

package() {
  cd $pkgname-$pkgver
  make DESTDIR="$pkgdir" install
}
