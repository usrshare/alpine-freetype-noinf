# Contributor: Carlo Landmeter <clandmeter@gmail.com>, /usr/share <usr_share@tuta.io>
# Maintainer: Carlo Landmeter <clandmeter@gmail.com>
pkgname=freetype
pkgver=2.6.3
pkgrel=1
pkgdesc="TrueType font rendering library (w/o infinality patches)"
url="http://freetype.sourceforge.net"
arch="all"
license="GPL"
depends=""
depends_dev=""
makedepends="$depends_dev zlib-dev libpng-dev"
subpackages="$pkgname-dev $pkgname-doc"
source="http://download.savannah.gnu.org/releases/freetype/freetype-$pkgver.tar.bz2
	40-memcpy-fix.patch"

_builddir="$srcdir/$pkgname-$pkgver"

prepare() {
	cd "$_builddir"
	for i in "$srcdir"/*.patch; do
		msg "Applying ${i}"
		patch -p0 -i $i || return 1
	done
}

build() {
	cd "$_builddir"
	./configure \
		--build=$CBUILD \
		--host=$CHOST \
		--prefix=/usr \
		--sysconfdir=/etc \
		--mandir=/usr/share/man \
		--infodir=/usr/share/info \
		--disable-static \
		|| return 1
	make || return 1
}

package() {
	cd "$_builddir"
	make -j1 DESTDIR="$pkgdir" install || return 1

	# for compat. This should be removed once all apps are properly using
	# pkg-config
	ln -s freetype2 "$pkgdir"/usr/include/freetype
}

md5sums="0037b25a8c090bc8a1218e867b32beb1  freetype-2.6.3.tar.bz2
bd2d808a0c00dcf9f1d1c0a9a8227ad9  40-memcpy-fix.patch"
sha256sums="371e707aa522acf5b15ce93f11183c725b8ed1ee8546d7b3af549863045863a2  freetype-2.6.3.tar.bz2
574c265c7a7032c5afb32a9807e5d04354ad0def656194cfcfff1ccca6a5540e  40-memcpy-fix.patch"
sha512sums="e1f9018835fc88beeb4479537b59f866c52393ae18d24a1e0710a464cf948ab02b35c2c6043bc20c1db3a04871ee4eb0bb1d210550c0ea2780c8b1aea98fbf0d  freetype-2.6.3.tar.bz2
1553f7f0514238012e300bc8d0b1e260145db17fb56f13e4aa667435e98c3749c00e150caa0e318289b84bca33b9a06a68b8342575e10ac3bf5af3d5cc861537  40-memcpy-fix.patch"
