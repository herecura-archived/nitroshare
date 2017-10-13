# Maintainer: Sid Karunaratne <sid at karunaratne dot net>
# Contributor: Nathan Osman <nathan at quickmediasolutions dot com>

pkgname='nitroshare'
pkgver=0.3.4
pkgrel=1
pkgdesc='Network File Transfer Application'
url='https://nitroshare.net'
arch=('i686' 'x86_64')
license=('MIT')
makedepends=('cmake')
depends=('qt5-base' 'qt5-tools' 'qt5-svg')
optdepends=(
    'libappindicator-gtk2: export a menu into the Unity Menu bar'
    'qhttpengine: allow local applications access'
)
source=(
    "$pkgname-$pkgver.tar.gz::https://github.com/nitroshare/nitroshare-desktop/archive/$pkgver.tar.gz"
)
sha256sums=('29874e5909c29211a3c9e13f8c0f49b901ec2996e5d60d80af80d2fb80c3d7ec')

build() {
    cd "$pkgname-desktop-$pkgver"
    cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr .
    make
}

package() {
    cd "$pkgname-desktop-$pkgver"
    make DESTDIR="$pkgdir" install

    # license
    install -Dm644 \
        "LICENSE.txt" \
        "$pkgdir/usr/share/licenses/$pkgname/LICENSE.txt"
}
