# $Id$
# Maintainer:  pvg <pvg@poczta.fm>

pkgname=kadu-pre
pkgver=1.0
pkgrel=1
pkgdesc='Qt-based Jabber/XMPP and Gadu-Gadu client - development version'
arch=('i686' 'x86_64')
url='http://www.kadu.net/'
license=('GPL')
depends=('qt4' 'libgadu>=1.12.0' 'libxss' 'enchant' 'phonon' 'qca-ossl'
         'libidn' 'libmpdclient' 'qtwebkit' 'xdg-utils' 'libotr')
makedepends=('cmake' 'libao' 'libsndfile' 'libxtst' 'curl' 'optipng')
provides=('kadu' 'kadu-theme-faenza')
conflicts=('kadu' 'kadu-theme-faenza')
install=kadu.install
source=(http://download.kadu.im/stable/kadu-1.0.tar.bz2)
md5sums=('a91c00707d73e0ba7fe8245885dd59a5')

prepare() {
  find -name '*.png' -exec optipng -quiet -force -fix {} +
}

build() {
  mkdir build
  cd build

  cmake ../${pkgname//-pre/}-${pkgver//_/-} \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_INSTALL_LIBDIR=/usr/lib
  make
}

package() {
  cd build
  make DESTDIR=$pkgdir LIBDIR=/usr/lib install

  #mv $pkgdir/usr/sdk $pkgdir/usr/share/kadu/sdk
  rm -rf $pkgdir/usr/{lib,include}/{libgadu*,pkgconfig}
}
