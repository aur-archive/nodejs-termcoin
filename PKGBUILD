# Maintainer: WorMzy Tykashi <wormzy.tykashi@gmail.com>

pkgname=nodejs-termcoin
_npmname=${pkgname#nodejs-}
pkgver=0.0.4
pkgrel=2
pkgdesc="A bitcoin wallet for your terminal"
arch=(any)
url="https://github.com/chjj/termcoin"
license=('MIT')
depends=('nodejs' 'nodejs-blessed>=0.0.29')
optdepends=('bitcoin-daemon: bitcoind RPC server'
            'qrencode: generating and rendering QR codes'
            'xsel: clipboard support for X11'
            'xclip: clipboard support for X11')
source=(${_npmname}-${pkgver}.tar.gz::"https://github.com/chjj/${_npmname}/archive/v${pkgver}.tar.gz")
noextract=(${_npmname}-${pkgver}.tar.gz)
md5sums=('36f73575ca945ca692d3fe649a59b9fa')

package() {
  npm install --user root -g --prefix "$pkgdir/usr" "${_npmname}-${pkgver}.tar.gz"
  
  # remove redundant depends
  rm -r "$pkgdir/usr/lib/node_modules/$_npmname/node_modules/"

  # copy license to standard location
  install -D -m644 "$pkgdir/usr/lib/node_modules/$_npmname/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"

  # move manpage
  install -d -m755 "$pkgdir/usr/share/man"
  mv "$pkgdir/usr/lib/node_modules/$_npmname/man" "$pkgdir/usr/share/man/man1"
}
