# Maintainer : Christian Rebischke <Chris.Rebischke@archlinux.org>
# Contributor: Vlad M. <vlad@archlinux.net>
# Contributor: Patrice Peterson <runiq at archlinux dot us>
# Contributor: Vivien Didelot <vivien+aur@didelot.org>

pkgname=i3blocks
pkgver=1.5
pkgrel=3.1
pkgdesc='Define blocks for your i3bar status line'
arch=('x86_64')
groups=('i3')
url="https://github.com/vivien/i3blocks"
license=('GPL3')
makedepends=('git')
depends=('glibc')
source=(
        "${pkgname}-${pkgver}::git+https://github.com/vivien/${pkgname}#tag=${pkgver}"
        bash.patch
        )
backup=('etc/i3blocks.conf')
validpgpkeys=('44C919BDF206CFDC49C7101A66C63FBDFD79670A')
install=i3blocks.install

prepare () {
  cd "${pkgname}-${pkgver}"
  patch -Np1 -i ../bash.patch
}

build () {
  cd "${pkgname}-${pkgver}"
  ./autogen.sh
  ./configure --prefix=/usr --libexecdir=/usr/lib --sysconfdir=/etc
  make VERSION="${pkgver}"
}

package () {
  cd "${pkgname}-${pkgver}"
  make VERSION="${pkgver}" DESTDIR="${pkgdir}" install

  # install bash-competion - broken in version 1.5
  mkdir -p $pkgdir/usr/share/bash-completion/completions
  install -c -m 644 bash-completion $pkgdir/usr/share/bash-completion/completions/i3blocks
}

sha256sums=('SKIP'
            '99e383ff5add6b672ea09181119a64133703bb23ca3d83ce178cd8e57c54a15d')
