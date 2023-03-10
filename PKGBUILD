# Maintainer: Maarten de Vries <maarten@de-vri.es>

pkgname=codemeter-runtime
pkgver=7.60.5598.500
pkgrel=2
pkgdesc='codemeter runtime (server and cli tools, no GUI)'
license=('custom')
url='http://www.codemeter.de/'

arch=(x86_64)
backup=('etc/wibu/CodeMeter/Server.ini')
install="$pkgname.install"

depends=(
	'libusb'
	'fakeroot'
)

source=(
	"codemeter_7.60.5598.500_amd64.deb"
	"codemeter.service"
	"sysusers.conf"
)

sha512sums=(
	'2e3ddaf72b7f3a09dc8c077fe6c349201eb77783fed8b9f185a92eb4c8f1dfbe645a85010a2abfcabd53ee613a6e28e3d91f99b3399dc26a19bd5c07e51a6dad'
	'7497cde13f40ae3cbc02b821f4aee1da02c6955ef278aa5f01779a988e5d07193a69be64fb9b529358764b58dc29ad451c0fca10659c40cfa499e03f41f31362'
	'0acee8febd3f5763ee493c42fbd1a435b1c2572e9cab68c9da81f858dd6c7d4d5aad88deffd5b454b95f0e7492faf786f779c4c883b20ff8ea4e7006f2c3a46b'
)

prepare() {
	bsdtar -xf data.tar.*
}

package() {
	install -d "$pkgdir/etc"
	install -d "$pkgdir/usr/bin"
	install -d "$pkgdir/usr/lib"
	install -d "$pkgdir/usr/lib32"
	install -d "$pkgdir/usr/share"
	install -d "$pkgdir/var/lib"
	install -d "$pkgdir/var/log"

	# Created by CodeMeterLin -x on debian.
	install -d "$pkgdir/var/spool/ctmp"

	cp -a "$srcdir/etc/wibu"                   "$pkgdir/etc/"
	cp -a "$srcdir/usr/bin/"*                  "$pkgdir/usr/bin/"
	cp -a "$srcdir/usr/sbin/"*                 "$pkgdir/usr/bin/"
	cp -a "$srcdir/usr/lib/x86_64-linux-gnu/"* "$pkgdir/usr/lib/"
	cp -a "$srcdir/usr/share/"*                "$pkgdir/usr/share/"
	cp -a "$srcdir/var/lib/CodeMeter"          "$pkgdir/var/lib/"
	cp -a "$srcdir/var/log/CodeMeter"          "$pkgdir/var/log/"

	ln -fs '/usr/share/licenses/common/LGPL2.1/license.txt' "$pkgdir/usr/share/doc/CodeMeter/lgpl-2.1.txt"

	install -D "$srcdir/sysusers.conf"     "$pkgdir/usr/lib/sysusers.d/$pkgname.conf"
	install -D "$srcdir/codemeter.service" "$pkgdir/usr/lib/systemd/system/codemeter.service"

}
