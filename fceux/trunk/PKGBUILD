# Maintainer: Cory Sanin <corysanin@artixlinux.org>
# Contributor: Eric Belanger <eric@archlinux.org>
# Contributor: Jo Christian Bergskås <jcberg@gmail.com>

pkgname=fceux
pkgver=2.6.5
pkgrel=2
pkgdesc='Fast and ultra-compatible NES/Famicom emulator'
arch=(x86_64)
url='https://github.com/TASEmulators/fceux.git'
license=(GPL)
depends=(gd lua minizip qt5-base sdl2)
makedepends=(cmake git glu mesa-libgl ninja setconf scons)
optdepends=('ffmpeg: for recording')
source=("_$pkgname::git+$url#commit=ea6ed69b874e3ae94072f1b4f14b9a8f0fdd774b") # tag: v2.6.5
b2sums=('SKIP')

prepare() {
  cd _$pkgname
  sed -i 's/-interim git//g' src/version.h
  setconf scripts/genGitHdr.sh GIT_URL "'""$url""'"
  setconf scripts/genGitHdr.sh GIT_REV "${source#*=}"
}

build() {
  artix-cmake \
    -B build \
    -D CMAKE_C_FLAGS="$CFLAGS -fPIC -w" \
    -D CMAKE_CXX_FLAGS="$CXXFLAGS -fPIC -w" \
    -D CMAKE_INSTALL_PREFIX=/usr \
    -G Ninja \
    -S _$pkgname
  ninja -C build
}

package() {
  DESTDIR="$pkgdir" ninja -C build install
  install -d "$pkgdir/usr/share/doc/$pkgname"
  cp -r _$pkgname/documentation/* "$pkgdir/usr/share/doc/$pkgname/"
  install -Dm644 _$pkgname/changelog.txt \
    "$pkgdir/usr/share/doc/$pkgname/changelog.txt"
}
