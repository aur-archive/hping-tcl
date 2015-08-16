# $Id: PKGBUILD 32612 2010-11-15 22:11:14Z lfleischer $
# Maintainer: Lukas Fleischer <archlinux at cryptocrack dot de>
# Contributor: Kevin Piche <kevin@archlinux.org>

pkgname=hping-tcl
pkgver=3.0.0
pkgrel=1
pkgdesc='hping is a command-line oriented TCP/IP packet assembler/analyzer. (built with tcl scripting enabled)'
arch=('i686' 'x86_64')
url='http://www.hping.org'
license=('GPL2' 'BSD')
depends=('libpcap' 'tcl')
conflicts=('hping')
source=("http://www.hping.org/hping3-20051105.tar.gz"
        'Makefile.patch'
        'bytesex.h.patch')
md5sums=('ca4ea4e34bcc2162aedf25df8b2d1747'
         '3c6f920201fc980d377408917a28df93'
         '8af8e336819df1447b0c1b879a704be9')

build() {
  cd "${srcdir}/hping3-20051105"

  [ "$CARCH" == "x86_64" ] && patch -Np1 -i ../bytesex.h.patch

  MANPATH=/usr/share/man ./configure
  make
}

package() {
  cd "${srcdir}/hping3-20051105"

  patch -p1 < ../Makefile.patch

  make DESTDIR="${pkgdir}" install
  install -Dm0644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
