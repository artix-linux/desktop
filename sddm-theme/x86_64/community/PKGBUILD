# Maintainer: artoo <artoo@artixlinux.org>
# Maintainer: nous <nous@artixlinux.org>

pkgbase=sddm-theme
pkgname=${pkgbase}-artix
pkgver=0.7
pkgrel=1
pkgdesc="Artix theme for SDDM"
arch=('any')
url="https://gitea.artixlinux.org/artix/sddm-theme-artix"
license=('GPL')
makedepends=('git')
depends=('sddm' "artix-backgrounds")
conflicts=('artix-sddm-theme')
replaces=('artix-sddm-theme')
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/${pkgver}.tar.gz")
sha256sums=('f9e82fe5f655ff30b40bf2daa9c67b0dce0777daa2c8d9a76f391068ae22247c')

package() {
    cd ${pkgname} #-${pkgver}
    make PREFIX=/usr DESTDIR=${pkgdir} install
}
