# Maintainer: Pest <forum@devault.cc>
pkgname=devault
pkgver=1.0.5
pkgrel=1
pkgdesc="QT Wallet for the dvt blockchain"
arch=('x86_64')
license=('MIT')
url="https://github.com/devaultcrypto/"
source=("https://github.com/devaultcrypto/devault/archive/v1.0.5.tar.gz"
        "devault.desktop"
        "devault.png"
        "LICENSE"
       )
depends=('boost-libs' 'qt5-base' 'qrencode' 'libevent' 'zeromq' 'miniupnpc')
makedepends=('python' 'libevent' 'git' 'boost' 'libsodium' ) 
build() {
	cd "$srcdir/$pkgname-$pkgver"
	./autogen.sh
	sed -i 's+/usr/local+/usr/+g' configure
	./configure
	make -j4
}
package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir/" install
  install -d "$pkgdir/usr/share/applications" "$pkgdir/usr/share/icons/hicolor/256x256/apps" \
  "$pkgdir/usr/share/licenses/$pkgname"
  cp "$srcdir/devault.desktop" "$pkgdir/usr/share/applications/"
  cp "$srcdir/devault.png" "$pkgdir/usr/share/icons/hicolor/256x256/apps/"
  install -Dm644 "$srcdir/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
sha256sums=('6cc634175eaf2375b16cc9eb7f128491da9eee6090610cd9edd78503bc1de195'
            '83881b19c0a50912e2444a734896fe7e700815534f3c0c22618ffce527859259'
            'fa1a318a314e83b9a4b8ee7f8f0b67c97d93cea3bfbad9b8022c18e4f8008f99'
            '295d5d4cb7332a084b0d1e1f25cb50c22a178a303d0a1a609546d56261b50266')