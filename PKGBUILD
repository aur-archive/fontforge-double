# $Id: PKGBUILD 145161 2011-12-18 12:09:19Z bisson $
# Maintainer: Gaetan Bisson <bisson@archlinux.org>
# Contributor: Eric Belanger <eric@archlinux.org>
# Contributor: William Rea <sillywilly@gmail.com>

pkgname=fontforge-double
pkgver=20111214
pkgrel=2
pkgdesc='Outline and bitmap font editor'
arch=('i686' 'x86_64')
url='http://fontforge.sourceforge.net/'
license=('BSD')
depends=('libxkbui' 'libxi' 'libxml2' 'pango' 'giflib' 'libtiff' 'python2' 'libspiro')
options=('!libtool' '!makeflags')
conflicts=('fontforge')
provides=('fontforge')
source=("ftp://ftp.archlinux.org/other/fontforge/fontforge-${pkgver}.tar.xz")
sha1sums=('55c3f00c0b486492ba071fc479e1feb426562e2b')

# git clone git://fontforge.git.sourceforge.net/gitroot/fontforge/fontforge; cd fontforge; git archive --prefix=${pkgname}-${pkgver}/ master | xz > ../${pkgname}-${pkgver}.tar.xz

build() {
	cd "${srcdir}/fontforge-${pkgver}"
	sed -i 's/python /python2 /g' Makefile.dynamic.in
	./configure \
	  --prefix=/usr \
	  --mandir=/usr/share/man \
	  --enable-type3 \
          --enable-double \
	  --enable-devicetables \
	  --with-regular-link \
	  --with-python=python2 \
	  --enable-pyextension \
          
	make
}

package() {
	cd "${srcdir}/fontforge-${pkgver}"
	make DESTDIR="${pkgdir}" install
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
