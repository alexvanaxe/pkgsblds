# Contributor: Patrick Jackson <PatrickSJackson gmail com>
# Maintainer: Christoph Vigano <mail@cvigano.de>

pkgname=ava_st
pkgver=0.8.1
pkgrel=1
pkgdesc='A simple virtual terminal emulator for X. Applyed scroll, alpha, icon hide...'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft' 'libxext' 'xorg-fonts-misc')
makedepends=('ncurses')
url="http://st.suckless.org"
source=(https://github.com/alexvanaxe/ava_st/archive/master.zip)
sha256sums=('bff8922677ed4c4ccaf45496fa686828e570466e482421c1786d12a62b7ebd0c')

prepare() {
  cd $srcdir/ava_st-master
  # skip terminfo which conflicts with nsurses
  sed -i '/tic /d' Makefile
}

build() {
  cd $srcdir/ava_st-master
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd $srcdir/ava_st-master
  make PREFIX=/usr DESTDIR="$pkgdir" TERMINFO="$pkgdir/usr/share/terminfo" install
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -Dm644 README "$pkgdir/usr/share/doc/$pkgname/README"
}
