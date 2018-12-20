# Contributor: Patrick Jackson <PatrickSJackson gmail com>
# Maintainer: Christoph Vigano <mail@cvigano.de>

pkgname=ava_st
pkgver=0.8.1
pkgrel=1
pkgdesc='A simple virtual terminal emulator for X.'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft' 'libxext' 'xorg-fonts-misc')
makedepends=('ncurses')
url="http://st.suckless.org"
source=(https://github.com/alexvanaxe/ava_st/archive/master.zip)
sha256sums=('6f4b4906756428268c3cd405d0d44e984cf60c8f2f73fe2dfbb306728feb97b0')

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
