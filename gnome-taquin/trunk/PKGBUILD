# Maintainer: Jan Alexander Steffens (heftig) <heftig@archlinux.org>
# Contributor: Jan de Groot <jgc@archlinux.org>

pkgname=gnome-taquin
pkgver=3.38.1+r35+g35edb95
pkgrel=1
pkgdesc="Move tiles so that they reach their places"
url="https://wiki.gnome.org/Apps/Taquin"
arch=(x86_64)
license=(GPL3)
depends=(gtk3 librsvg gsound)
makedepends=(meson vala yelp-tools appstream-glib git)
groups=(gnome-extra)
options=(debug)
_commit=35edb95303b75559607d0599c4424c6cbc661648  # master
source=("git+https://gitlab.gnome.org/GNOME/gnome-taquin.git#commit=$_commit")
sha256sums=('SKIP')

pkgver() {
  cd $pkgname
  git describe --tags | sed 's/[^-]*-g/r&/;s/-/+/g'
}

prepare() {
  cd $pkgname

  # fix building with vala 0.52
  git cherry-pick -n 99dea5e7863e112f33f16e59898c56a4f1a547b3
  git cherry-pick -n 66be44dc20d114e449fc33156e3939fd05dfbb16
}

build() {
  artix-meson $pkgname build
}

#check() {
#  meson test -C build --print-errorlogs
#}

package() {
  meson install -C build --destdir="$pkgdir"
}

# vim:set sw=2 sts=-1 et:
