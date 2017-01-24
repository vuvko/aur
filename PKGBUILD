# $Id: PKGBUILD 194152 2016-10-31 13:48:24Z spupykin $
# Maintainer Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Alessio 'mOLOk' Bolognino <themolok@gmail.com>

pkgname=perl-gnome2-wnck
pkgver=0.16
pkgrel=11
pkgdesc="Perl interface to the Window Navigator Construction Kit"
arch=('i686' 'x86_64')
license=("GPL" "PerlArtistic")
url="http://search.cpan.org/dist/Gnome2-Wnck"
depends=('gtk2-perl' 'libwnck')
makedepends=('perl-extutils-depends' 'perl-extutils-pkgconfig')
options=('!emptydirs')
source=("http://search.cpan.org/CPAN/authors/id/T/TS/TSCH/Gnome2-Wnck-${pkgver}.tar.gz")
md5sums=('439f4569ffd7af96ef1d3feaab23760e')

build() {
  cd Gnome2-Wnck-${pkgver}
  PERL_MM_USE_DEFAULT=1 perl Makefile.PL INSTALLDIRS=vendor
  make
}

package() {
  cd Gnome2-Wnck-${pkgver}
  make install DESTDIR="$pkgdir"
# template start; name=perl-binary-module-dependency; version=1;
if [[ $(find "$pkgdir/usr/lib/perl5/" -name "*.so") ]]; then
	_perlver_min=$(perl -e '$v = $^V->{version}; print $v->[0].".".($v->[1]);')
	_perlver_max=$(perl -e '$v = $^V->{version}; print $v->[0].".".($v->[1]+1);')
	depends+=("perl>=$_perlver_min" "perl<$_perlver_max")
fi
# template end;
}
