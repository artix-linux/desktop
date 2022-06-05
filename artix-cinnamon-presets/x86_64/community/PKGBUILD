# Maintainer: Chris Cromer <cromer@artixlinux.org>

_pkgbase=desktop-presets

pkgname=artix-cinnamon-presets
pkgver=20211217
pkgrel=1
pkgdesc='Artix Cinnamon presets'
arch=('any')
url="https://gitea.artixlinux.org/artix/desktop-presets"
license=('GPL')
provides=('desktop-presets')
depends=('artix-dark-theme')
makedepends=('git')
#_commit=eb2382d9452c33833245b8ddf7216f68f9f35740
_branch='master'
source=("git+$url.git#branch=${_branch}")
sha256sums=('SKIP')

#pkgver() {
#    cd ${_pkgbase}
#    git describe --tags | sed 's/-/+/g'
#}

package() {
	install -d ${pkgdir}/usr/share/glib-2.0/schemas
    install -Dm644 ${_pkgbase}/gtk/schemas/*_cinnamon*.override "${pkgdir}"/usr/share/glib-2.0/schemas/
}
