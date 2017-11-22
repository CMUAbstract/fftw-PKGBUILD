# $Id$
# Maintainer: Ronald van Haren <ronald.archlinux.org>
# Contributor: damir <damir@archlinux.org>

# ALARM: Kevin Mihelich <kevin@archlinuxarm.org>
#  - removed -malign-double from CFLAGS
#  - removed --enable-sse2 from double precision
#  - removed --enable-sse from single precision

# Alexei Colin <ac@alexeicolin.com>
#  - enabled ARM NEON support

pkgname=fftw
pkgver=3.3.7
pkgrel=1
pkgdesc="A library for computing the discrete Fourier transform (DFT)"
arch=('i686' 'x86_64' 'armv7h')
license=('GPL2')
url="http://www.fftw.org/"
depends=('bash' 'gcc-libs')
makedepends=('gcc-fortran')
source=("http://www.fftw.org/${pkgname}-${pkgver}.tar.gz")
sha1sums=('2ae980a8d44c161ce4a09c6e2d1c79243ecbabb2')

# notes:
# http://www.fftw.org/fftw2_doc/fftw_6.html#SEC69
# http://www.fftw.org/faq/section2.html#singleprec
# http://www.fftw.org/fftw3_doc/Precision.html#Precision


build() {
  cd ${srcdir}/${pkgname}-${pkgver}
  
  # use upstream default CFLAGS while keeping our -march/-mtune
  CFLAGS+=" -O3 -fomit-frame-pointer -fstrict-aliasing -ffast-math"

  CONFIGURE="./configure F77=gfortran --prefix=/usr \
                 --enable-shared --enable-threads \
                 --enable-neon --enable-armv7a-cntvct"

  # build & install single precision
  $CONFIGURE --enable-float
  make
}

package() {
  cd ${srcdir}/${pkgname}-${pkgver}
  make DESTDIR=${pkgdir} install  
}
