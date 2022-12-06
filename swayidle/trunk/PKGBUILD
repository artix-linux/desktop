# Maintainer: Nathan <ndowens@artixlinux.org>
# Contributor: gilbus

pkgname=swayidle
pkgver=1.8.0
pkgrel=1
license=('MIT')
pkgdesc="Idle management daemon for Wayland"
makedepends=(
    'elogind'
    'meson'
    'scdoc'
    'wayland-protocols'
)
depends=(
    'wayland'
    'libelogind'
)
arch=('x86_64')
url="https://github.com/swaywm/swayidle"
options=(debug)
source=(
    "https://github.com/swaywm/swayidle/releases/download/$pkgver/$pkgname-$pkgver.tar.gz"{,.sig}
)
sha256sums=('16b3e76a117f2f0ff2ee5fbebf38849595cdd705db1cd5f6aceaed00d71b3aa1'
            'SKIP')
validpgpkeys=('34FF9526CFEF0E97A340E2E40FDE7BE0E88F5E48'  # Simon Ser
              '9DDA3B9FA5D58DD5392C78E652CB6609B22DA89A') # Drew DeVault

build() {
    artix-meson "$pkgname-$pkgver" build \
        -Dlogind=enabled \
        -Dman-pages=enabled \
        -Dlogind-provider=elogind
    ninja -C build
}

package() {
    DESTDIR="$pkgdir/" ninja -C build install
    install -Dm644 "$pkgname-$pkgver/LICENSE" -t "$pkgdir/usr/share/licenses/$pkgname"
    install -Dm644 "$pkgname-$pkgver/README.md" -t "$pkgdir/usr/share/doc/$pkgname"
}
