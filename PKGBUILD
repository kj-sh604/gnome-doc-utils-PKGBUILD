# Maintainer: Brian Bidulock <bidulock@openss7.org>
# Contributor: Jan de Groot <jgc@archlinux.org>

pkgname=gnome-doc-utils
pkgver=0.21
pkgrel=604
pkgdesc="Documentation utilities for Gnome"
arch=('any')
license=('GPL' 'LGPL')
depends=(docbook-xml rarian)
makedepends=(intltool gnome-common git)
url="https://www.gnome.org"
source=("git+https://github.com/kj-sh604/gnome-doc-utils.git")
# pkgver() {
#   cd $pkgname
#   git describe --tags | sed 's/-/+/g'
# }
prepare() {
  cd $pkgname
  rm -f m4/glib-gettext.m4
  NOCONFIGURE=1 ./autogen.sh
  sed -i 's/SUBDIRS = .*/SUBDIRS = /' doc/Makefile.am
}

build() {
  cd "$pkgname"
  PYTHON=/usr/bin/python2 ./configure --prefix=/usr \
      --sysconfdir=/etc --mandir=/usr/share/man \
      --localstatedir=/var --disable-scrollkeeper
  make
}

package() {
  cd "$pkgname"
  make DESTDIR="$pkgdir" install
}
