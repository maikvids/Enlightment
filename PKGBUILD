pkgname=enlightenment
pkgver=0.20.7
pkgrel=1
pkgdesc="Enlightenment window manager"
arch=('i686' 'x86_64')
url="http://www.enlightenment.org"
license=('BSD')
depends=('elementary' 'xcb-util-keysyms' 'hicolor-icon-theme' 'pixman' 'mesa'
         'desktop-file-utils' 'udisks2' 'ttf-freefont' 'bluez')
source=(http://download.enlightenment.org/rel/apps/${pkgname}/$pkgname-$pkgver.tar.gz)
md5sums=('930f3dd45dbad54388bfd0f9b7d8c215')

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"

  export CFLAGS="$CFLAGS -fvisibility=hidden"

  ./configure --prefix=/usr --sysconfdir=/etc \
    --enable-xwayland --enable-wayland \
    --disable-wl-weekeyboard

  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  make -j1 DESTDIR="$pkgdir" install
}
