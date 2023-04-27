# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: tinywrkb <tinywrkb@gmail.com>

pkgname=power-profiles-daemon
pkgver=0.13
pkgrel=1
pkgdesc='Makes power profiles handling available over D-Bus'
url='https://gitlab.freedesktop.org/hadess/power-profiles-daemon'
license=(GPL3)
arch=(x86_64)
depends=(upower polkit)
optdepends=('python-gobject: for powerprofilesctl')
makedepends=(meson)
checkdepends=(python-dbusmock python-isort python-mccabe umockdev)
source=(https://gitlab.freedesktop.org/hadess/power-profiles-daemon/-/archive/$pkgver/$pkgname-$pkgver.tar.gz
        power-profiles-daemon.tmpfiles)
b2sums=('80dba838433c7abdbc6079a8c6ff330cfda8dc1f0e8b8628125e466987238b1b7912b91af201ff120a2b1b7a5b081824c98d2a7e67a6c81d6ba7eb905d168ce4'
        '4448feb0622ee95017b38dd0cc54a012df20132d4e409dc80ddea2137132892c3d596f752829b5644dc5f4aa420a6f0b050824e775881920982b96fdd9783ee5')

build() {
  # set a dummy dir to avoid systemd dep
  meson $pkgname-$pkgver build \
    --prefix /usr \
    --libexec lib \
    --sysconfdir /usr/share \
    -Dsystemdsystemunitdir=/usr/lib/systemd
  meson compile -C build
}

check() {
  meson test -C build
}

package() {
  meson install -C build --destdir "$pkgdir"
  rm -r $pkgdir/usr/lib/systemd
  install -vDm 644 "${pkgname}.tmpfiles" \
    "${pkgdir}/usr/lib/tmpfiles.d/${pkgname}.conf"
}
