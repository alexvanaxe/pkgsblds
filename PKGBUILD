# Contributor: Patrick Jackson <PatrickSJackson gmail com>
# Maintainer: Christoph Vigano <mail@cvigano.de>

pkgname=st
pkgver=0.8.1
pkgrel=1
pkgdesc='A simple virtual terminal emulator for X.'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft' 'libxext' 'xorg-fonts-misc')
makedepends=('ncurses')
url="http://st.suckless.org"
source=(https://github.com/alexvanaxe/ava_st/archive/master.zip)
sha256sums=('091aac3cf2331262b3c75378a5975cca667fdea65e37972164b51a44192ba83d')

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
