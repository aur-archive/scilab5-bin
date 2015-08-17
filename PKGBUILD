# Contributor: Simon Lipp <aur@simon.lipp.name>
pkgname=scilab5-bin
pkgver=5.4.1
pkgrel=1
pkgdesc="Scilab is a scientific software package for numerical computations [official binary package]"
arch=(i686 x86_64)
url="http://www.scilab.org/"
provides=("scilab=$pkgver")
conflicts=('scilab')
license=('custom:CeCILL')
depends=('libxi' 'libgl' 'libxml2' 'libxtst' 'libxss')
makedepends=('patch')
options=(!strip)
source=("http://www.scilab.org/download/$pkgver/scilab-$pkgver.bin.linux-$CARCH.tar.gz"
	'fix-thirdparty-path.patch' 'scilab.desktop')
if [ "$CARCH" = "x86_64" ] ; then
	md5sums=('63d64dc8fe367d5098df12fbaad6b7e7'
		 '86fa6cd956438130d381d95316be6f91'
		 'bd76d40d4caabae835ca17569a5f25d8')
else
	md5sums=('fe51ded9c7f2804e3992054edbae2bfa'
		 '86fa6cd956438130d381d95316be6f91'
		 'bd76d40d4caabae835ca17569a5f25d8')
fi


build() {
	cd "$srcdir/scilab-$pkgver"
	patch -p1 < "$srcdir/fix-thirdparty-path.patch" || return 1
}

package() {
	install -d "$pkgdir/usr/lib" &&
	install -d "$pkgdir/usr/share/licenses/$pkgname" &&
	install -d "$pkgdir/usr/share/applications" &&
	cp -r "$srcdir/scilab-$pkgver/bin" "$pkgdir/usr" &&
	cp -r "$srcdir/scilab-$pkgver/include" "$pkgdir/usr" &&
	cp -r "$srcdir/scilab-$pkgver/share" "$pkgdir/usr" &&
	cp -r "$srcdir/scilab-$pkgver/lib/scilab" "$pkgdir/usr/lib" &&
	cp -r "$srcdir/scilab-$pkgver/lib/pkgconfig" "$pkgdir/usr/lib" &&
	cp -r "$srcdir/scilab-$pkgver/lib/thirdparty" "$pkgdir/usr/lib/scilab" &&
	cp -r "$srcdir/scilab-$pkgver/thirdparty" "$pkgdir/usr/share/scilab" &&
	install --mode=644 "$srcdir/scilab.desktop" "$pkgdir/usr/share/applications" &&
	install --mode=644 "$srcdir/scilab-$pkgver/COPYING" "$pkgdir/usr/share/licenses/$pkgname" || return 1
}
