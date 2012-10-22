# $Id: PKGBUILD 78568 2012-10-21 05:11:47Z ebelanger $
# Maintainer: Dave Reisner <dreisner@archlinux.org>
# Contributor: judd <jvinet@zeroflux.org>

_pkgbasename=util-linux
pkgname=lib32-$_pkgbasename
pkgver=2.22.1
pkgrel=1
pkgdesc="Miscellaneous system utilities for Linux (32-bit)"
url='http://www.kernel.org/pub/linux/utils/util-linux/'
arch=('x86_64')
depends=('lib32-glibc' "$_pkgbasename")
makedepends=('gcc-multilib')
provides=('lib32-util-linux-ng')
conflicts=('lib32-util-linux-ng')
replaces=('lib32-util-linux-ng')
license=('GPL2')
options=('!libtool' '!emptydirs')
source=("ftp://ftp.kernel.org/pub/linux/utils/util-linux/v2.22/util-linux-$pkgver.tar.xz")
md5sums=('730cf9932531ed09b53a04ca30fcb4c9')

shopt -s extglob

build() {
  cd "$_pkgbasename-$pkgver"

  export CC="gcc -m32"
  export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"

  ./configure --without-ncurses --libdir=/usr/lib32

  make lib{uuid,blkid,mount}.la
}

package() {
  make -C "$_pkgbasename-$pkgver" \
    DESTDIR="$pkgdir" \
    install-usrlib_execLTLIBRARIES \
    install-pkgconfigDATA
}
