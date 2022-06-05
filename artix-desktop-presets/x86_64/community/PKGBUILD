# Maintainer: nous <nous@artixlinux.org>

_pkgbase=desktop-presets

pkgname=artix-desktop-presets
pkgver=20220329
pkgrel=1
pkgdesc='Artix common desktop presets'
arch=('any')
url="https://gitea.artixlinux.org/artix/desktop-presets"
license=('GPL')
depends=('artix-dark-theme' 'artix-backgrounds' 'artix-icons')
makedepends=('git')
groups=('artix-branding')
#_commit=eb2382d9452c33833245b8ddf7216f68f9f35740
#source=("git+$url.git#commit=${_commit}")
#_branch='master'
#source=("git+$url.git#branch=${_branch}")
source=("git+$url.git")
sha256sums=('SKIP')

#pkgver() {
#    cd ${_pkgbase}
#    printf '%s+%s' "$(git describe --tags | sed 's/-/+/g')" "$(git rev-parse --short HEAD)"
#}

_inst_dir(){
    cd ${_pkgbase} #-${pkgver}
#    git checkout ${_branch}
    local profile="$1"

    install -d ${pkgdir}/etc
    cp -r $profile/skel ${pkgdir}/etc

    if [[ -d $profile/schemas ]];then
        install -d ${pkgdir}/usr/share/glib-2.0/schemas
        cp -r $profile/schemas ${pkgdir}/usr/share/glib-2.0/schemas
    fi

    if [[ -d $profile/scripts ]];then
        install -d ${pkgdir}/usr/bin
        cp -r $profile/scripts ${pkgdir}/usr/bin
    fi
}

package() {
    _inst_dir 'desktop'
}
