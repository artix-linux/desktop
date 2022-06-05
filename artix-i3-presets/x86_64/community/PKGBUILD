# Contributor linuxer <https://gitea.artixlinux.org/linuxer>
         
pkgname=artix-i3-presets
pkgdesc="Artix Linux i3 presets"
pkgver=20200906
pkgrel=1
#replaces=('artix-i3-presets')
arch=('any')
url="https://gitea.artixlinux.org/linuxer/artix-i3-presets"
license=('GPL')
source=("https://gitea.artixlinux.org/linuxer/artix-i3-presets/archive/$pkgver.tar.gz")
sha256sums=('2ecfa0a58b7bb529511d581cdfdf4fa464acdb2c72ffefd8ae920ca42bfa5db6')
         
package() {
    cd "${srcdir}/${pkgname}"
    mkdir -p "$pkgdir"/etc/
    cp -R skel "$pkgdir"/etc/
}
