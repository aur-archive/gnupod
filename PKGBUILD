# Maintainer: Brandon Invergo  <brandon@invergo.net>
pkgname=gnupod
pkgver=0.99.8
pkgrel=4
pkgdesc="A collection of Perl-Scripts which allow you to use your iPod under GNU/Linux"
url="http://www.gnu.org/software/gnupod/"
arch=('any')
license=("GPL3")
depends=('perl-timedate' 'perl-digest-sha1' 'perl-mp3-info' 'perl-unicode-string' 'perl-xml-parser')
source=("http://blinkenlights.ch/$pkgname-dist/stable/$pkgname-$pkgver.tgz")
md5sums=('978c9f813e6930b780e81eb30a742ebe')

package() {
  cd "$srcdir/$pkgname-$pkgver"

  # Create pkg dirs
  install -d "$pkgdir/usr/bin"
  install -d "$pkgdir/usr/share/man/man1"
  install -d "$pkgdir/usr/lib/perl5/vendor_perl/GNUpod"

  # Ignore brain-dead install script, and do the Arch thing
  install -m755 src/*.pl "$pkgdir/usr/bin"
  install -m644 man/* "$pkgdir/usr/share/man/man1"
  install -m444 src/ext/* "$pkgdir/usr/lib/perl5/vendor_perl/GNUpod"

  # Tidy up after ignoring brain-dead install script :P
  cd "$pkgdir/usr/bin"
  for i in *; do
    sed -i "s:##__PERLBIN__###:\!/usr/bin/perl:;s:###__VERSION__###:$pkgver:" $i ;
  done
}
