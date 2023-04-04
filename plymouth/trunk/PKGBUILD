# Maintainer: nikolar <nikolar@artixlinux.org>
# Contributor: Taijian <taijian@posteo.de>
# Contributor: Sebastian Lau <lauseb644@gmail.com>
# Contributor: Damian01w <damian01w@gmail.com>
# Contributor: Padfoot <padfoot@exemail.com.au>

pkgname=plymouth
pkgver=22.02.122
pkgrel=7.1
pkgdesc='Graphical boot splash screen'
arch=('x86_64')
url='https://www.freedesktop.org/wiki/Software/Plymouth/'
license=('GPL2')
depends=('bash' 'cairo' 'cantarell-fonts' 'filesystem' 'glib2' 'glibc' 'libdrm' 'libpng' 'pango')
makedepends=('gtk3' 'docbook-xsl')
optdepends=('gtk3: x11 renderer')
backup=('etc/plymouth/plymouthd.conf')
install='plymouth.install'
source=("https://www.freedesktop.org/software/$pkgname/releases/$pkgname-$pkgver.tar.xz"
        'plymouth.initcpio_hook'
        'plymouth.initcpio_install')
sha256sums=('100551442221033ce868c447ad6c74d831d209c18ae232b98ae0207e34eadaeb'
            'de852646e615e06d4125eb2e646d0528d1e349bd9e9877c08c5d32c43d288b6f'
            '1d2128f355bf410c7e5452b5a101d37a4e44a3c19fb64f78b0146a0a86672f48')

prepare() {
  cd "$pkgname-$pkgver"

  # Use mkinitcpio to update initrd
  sed -i 's/dracut -f/mkinitcpio -P/' scripts/plymouth-update-initrd

  # Change default theme
  sed -i 's/^Theme=spinner$/Theme=bgrt/' src/plymouthd.defaults
}

build() {
  cd "$pkgname-$pkgver"
  ./configure --prefix=/usr --sbindir=/usr/bin --libexecdir=/usr/lib --sysconfdir=/etc \
              --localstatedir=/var --runstatedir=/run --with-runtimedir=/run \
              --with-logo=/usr/share/pixmaps/artixlinux-logo.png --disable-systemd-integration
  sed -i -e 's/ -shared / -Wl,-O1,--as-needed\0/g' libtool
  make

  # Convert logo for the spinner theme
  rsvg-convert '/usr/share/pixmaps/artixlinux-logo-text-dark.svg' -o ../artixlinux-logo-text-dark.png
}

package() {
  cd "$pkgname-$pkgver"
  make DESTDIR="$pkgdir" install
  rm -r "$pkgdir/var/run"

  # Install mkinitcpio hook
  install -Dm644 ../plymouth.initcpio_hook "$pkgdir/usr/lib/initcpio/hooks/$pkgname"
  install -Dm644 ../plymouth.initcpio_install "$pkgdir/usr/lib/initcpio/install/$pkgname"
  
  # Install logo for the spinner theme
  install -Dm644 ../artixlinux-logo-text-dark.png "$pkgdir/usr/share/$pkgname/themes/spinner/watermark.png"
}
