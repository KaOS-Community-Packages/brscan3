license=('GPL' 'custom:Brother')
arch=('x86_64')
pkgname=brscan3
pkgver=0.2.11_5
pkgrel=2
pkgdesc="SANE drivers from Brother for brscan3 compatibile models"
depends=('sane' 'sed' 'libusb-compat')
makedepends=('sane')
url="http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html"
install=brscan3.install

pkg="${pkgname}-${pkgver/_/-}.x86_64.rpm"
pkg_md5sum="87b964de68fdcba45d622247bf687323"

source=("http://pub.brother.com/pub/com/bsc/linux/dlf/$pkg" "http://www.brother.com/agreement/English_sane/agree.html" "brscan3.rules")
md5sums=($pkg_md5sum 'ccffb9a6f6d436b21be25b0241068981' '76537a0eb5b68c48b57b4409397a4fa5')

package() {
  cp -r $srcdir/usr $pkgdir
  install -d -m755 $pkgdir/etc/udev/rules.d
  install -D -m644 $srcdir/brscan3.rules $pkgdir/etc/udev/rules.d
  install -D -m644 $srcdir/agree.html $pkgdir/usr/share/licenses/$pkgname/LICENSE.html
  mv $pkgdir/usr/lib64 $pkgdir/usr/lib
  cd $pkgdir/usr/lib
  ln -sf libbrscandec3.so.1.0.0 libbrscandec3.so.1
  ln -sf libbrscandec3.so.1 libbrscandec3.so
  cd $pkgdir/usr/lib/sane
  ln -sf libsane-brother3.so.1.0.7 libsane-brother3.so.1
  ln -sf libsane-brother3.so.1 libsane-brother3.so
}