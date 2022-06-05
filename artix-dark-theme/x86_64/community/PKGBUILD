# Maintainer: nous

pkgname=artix-dark-theme
pkgver=20201126
pkgrel=3
pkgdesc="Dark theme for the community ISOs of Artix Linux. Gtk2/3, Qt5, Plasma splash."
arch=('any')
url="https://gitea.artixlinux.org/nous/artix-dark-theme"
license=('GPL')
source=('git+https://gitea.artixlinux.org/artix/artix-dark-theme.git')
sha256sums=('SKIP')
depends=('artix-backgrounds' 'artix-icons')
makedepends=('git')
optdepends=('gtk2' 'gtk3' 'qt5' 'plasma' 'gtk-engines' 'xcursor-premium' 'qt5ct' 'openbox' 'gtk-engine-murrine')
groups=('artix-branding')

package() {
  cd "${srcdir}/$pkgname"
#  mkdir -p "${pkgdir}"/usr/share/
  cp -rf usr "${pkgdir}"/
}
