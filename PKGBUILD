# Contributor: Volker Schmidt <flashrom42 AT gmail DOT com>
#
pkgname=exactimage
pkgver=0.9.0
pkgrel=2
pkgdesc="A fast, modern and generic image processing library, including hocr2pdf and other utilities from frontends."
arch=('i686' 'x86_64')
url="http://www.exactcode.com/site/open_source/exactimage/"
license=('GPL')
provides=('exactimage')
conflicts=('exactimage-svn')
depends=('openexr' 'agg' 'jasper' 'libtiff' 'giflib' 'libpng')
optdepends=('expat: An XML parser library'
            'glu: Mesa OpenGL Utility library'
            'lcms: Lightweight color management development library/engine'
            'swig: Generate scripting interfaces to C/C++ code')
source=(http://dl.exactcode.de/oss/exact-image/exact-image-$pkgver.tar.bz2
        makefile-cflags.patch
        agg-missing-includes.patch
        utility-timer-dead-code.diff
        libpng15.patch
        patch-api-api.cc
        decode_before_read_stride.patch
        ftbfs_evas_object.patch
        patch-lib__ContourUtility.cc
        patch-lib__ContourMatching.cc
        patch-codecs__xpm.cc
        patch-codecs__jpeg.cc
        patch-bardecode__code128.hh
        patch-codecs__bmp.cc
        patch-lib__ImageIterator2.hh
        patch-edisplay_edisplay.cc
        patch-codecs__gif.cc
        patch-frontends-bardecode.cc
        bardecode.1
        e2mtiff.1
        econvert.1
        edentify.1
        empty-page.1
        hocr2pdf.1
        optimize2bw.1
        exactimage.7
)

sha256sums=('cf472ab1baa01f3dfd30098e308e34dc6a538c4ff3b03f0b87e2946ea8aeda4e'
            'a742a65f396b94798714c44eb610d1b602f4095d1dcc50a9cdf2099c01164ebd'
            '88729f009ba0650efdfffbc4ea05db8b6f18832165f369223eae34d6ce4dc22b'
            'e63e29d9fe46db4fdb628018c456e59469ce3e97a437e1a39fe2164f3e0861dc'
            'dd66b5514f0804c907ee7f67a7d39bca68414dd9a6553faeb906f99a3a7c768d'
            'e967acb15ee8667e232538db7aac2ab8b09e29b45f6b229788cd484b6524b0f7'
            '6054f996667dbbe85dee569b1a3fd7ebaf9a72796d181704fd1593e352118c22'
            '13e3d6002e885ec7d70110ba5a127aaca165c5453b9e6fc46e57ab937c3157eb'
            '9484f11e1b2e93c416bd0172f234fac6fb596e8213ea044bd68b9a60dccc2da6'
            'da1074642252ce6390678d5ab45c9eea60959423c14b94ce497dba1f4f3ba131'
            'c18d41e64ff51f4e5c83ade0c4aee12e510ab70c4195d4388d85751789dafee7'
            '3b9a0d02d874d1cae42e0b0fb59db51c6fddf25fe9a4c3fe81506567a2781bb8'
            '2dff965c398a83e3b3d4936e29da859f553b5b99f97ba8dc074864bb41d1f472'
            'a95b5ab4c248a08e3ee19d64f9a47d6c64a7802d61fb776d0cd0d9bc71cab5cd'
            '404b3df4f0372bc4ab991ba45bd3b96e429bb7dd1cee85b933dae3a024ba2868'
            '0e73dfcd127d2f74eabc88ff6791785de4876772146542437db2e4036abce6a3'
            '49d5e98e3ae9c7eba44aba70cd88734704c3efaf6bb50d7e2bd909bf56338bfa'
            '0e8c00351e65314d16a5130dffa5e6db22f279eb156b5e03dcd0dd0c532262e9'
            '419bd29e1ad54acebd26d44f64e9b704f4aeb0c1c52ba3d1c7668c007dad1d98'
            '69d42191c358c5db84814385d2950b6d270b70c4f59182ad44419a621484d8f6'
            '1a7186e78684a357eaedba6c73b8d787a3267c05ad08ea691ac28f1fb5a12e0e'
            '5f3a1e981ed3fda74851b0aa7411e6b5cae729c1728f8f7fca3b8127027a567d'
            '51a4d881d6fc79d5956b7bd3c93747dca42b4bf3fbbe457430608c5707084c99'
            'b5e6e2f4c6da983273e50070ead2f8fcedf41e0c462c5c08eb55ee2389139ac4'
            'a52820117c59e07bf753a32681a51b3ab2a03fd700534e4b36b1e23a792aadde'
            'efaf0857ccadb3547a1c11d7572b9dc3621292551451fe52ea079571dbe069ae')

build() {
  cd "$srcdir/exact-image-$pkgver"

  msg "Patching for Makefile CFLAGS --> From DEBIAN Project."
  patch -p1 -EN < ../makefile-cflags.patch

  msg "Patching for missing includes --> From DEBIAN Project."
  patch -p1 -EN < ../agg-missing-includes.patch

  msg "Patching for dead code in utility/Timer.cc --> From DEBIAN Project."
  patch -p1 -EN < ../utility-timer-dead-code.diff

  msg "Patching for compiling w/libpng-1.5 --> From DEBIAN Project."
  patch -p1 -EN < ../libpng15.patch

  msg "Patching for api.cc --> From FreeBSDProject."
  patch -p0 -EN < ../patch-api-api.cc

  msg "Patching for rotate.cc --> From DEBIAN Project."
  patch -p1 -EN < ../decode_before_read_stride.patch

  msg "Patching for X11Helper.cc --> From DEBIAN Project."
  patch -p1 -EN < ../ftbfs_evas_object.patch

  msg "Patching for ContourUtility.cc --> From FreeBSDProject."
  patch -p0 -EN < ../patch-lib__ContourUtility.cc

  msg "Patching for ContourMatching.cc --> From FreeBSDProject."
  patch -p0 -EN < ../patch-lib__ContourMatching.cc

  msg "Patching for codecs__xpm.cc --> From FreeBSDProject."
  patch -p0 -EN < ../patch-codecs__xpm.cc

  msg "Patching for codecs__jpeg.cc --> From FreeBSDProject."
  patch -p0 -EN < ../patch-codecs__jpeg.cc

  msg "Patching for bardecode__code128.hh --> From FreeBSDProject."
  patch -p0 -EN < ../patch-bardecode__code128.hh

  msg "Patching for codecs__bmp.cc --> From FreeBSDProject."
  patch -p0 -EN < ../patch-codecs__bmp.cc

  msg "Patching for lib__ImageIterator2.hh --> From FreeBSDProject."
  patch -p0 -EN < ../patch-lib__ImageIterator2.hh

  msg "Patching for edisplay_edisplay.cc --> From FreeBSDProject."
  patch -p0 -EN < ../patch-edisplay_edisplay.cc

  msg "Patching for codecs__gif.cc --> From FreeBSDProject (Partly!)."
  patch -p0 -EN < ../patch-codecs__gif.cc

  msg "Patching for bardecode.cc --> From FreeBSDProject."
  patch -p0 -EN < ../patch-frontends-bardecode.cc

  ./configure --prefix=/usr \
    --with-libungif=-lgif \
    --without-lua \
    --without-php \
    --without-perl \
    --without-python \
    --without-ruby
  make
}

package() {
  cd "$srcdir/exact-image-$pkgver"
  make DESTDIR="$pkgdir/" install
  # install the man-pages fetched from debian project
  msg "Installing the man-pages fetched from DEBIAN Project."
  cd ${srcdir}
  mkdir -p ${pkgdir}/usr/share/man/man7
  install -m 644 -o root -g root exactimage.7 ${pkgdir}/usr/share/man/man7
  mkdir -p ${pkgdir}/usr/share/man/man1
  for i in *.1
  do
    install -m 644 -o root -g root ${i} ${pkgdir}/usr/share/man/man1
  done
  find ${pkgdir}/usr/share/man -type f | xargs gzip --name --best 
}

# vim:set ts=2 sw=2 et:
