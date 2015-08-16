# Maintainer: Felix Yan <felixonmars@gmail.com>
# Contributor: Jove Yu <yushijun110 [at] gmail.com>

pkgname=kingsoft-office
pkgver=9.1.0.4751_a15
_pkgver=9.1.0.4751~a15_x86
pkgrel=2
pkgdesc="Kingsoft Office (WPS Office) is an office productivity suite"
arch=('i686' 'x86_64')
license=("custom")
url="http://wps-community.org/"
conflicts=('wps-office')
options=('!emptydirs')
install=${pkgname}.install
source=("http://kdl.cc.ksosoft.com/wps-community/download/a15/wps-office_${_pkgver}.tar.xz")
sha1sums=('966c56181cb448178243090811aea1cc2429567b')

if [ "$CARCH" = "i686" ]; then
    depends=('fontconfig' 'libpng12' 'glib2' 'libsm' 'libxext' 'libxrender' 'glu' 'libxml2')
    optdepends=('cups: for printing support')
elif [ "$CARCH" = "x86_64" ]; then
    depends=('lib32-fontconfig' 'lib32-libpng12' 'lib32-glib2' 'lib32-libsm' 'lib32-libxext' 'lib32-libxrender' 'lib32-glu' 'lib32-libxml2')
    optdepends=('lib32-libcups: for printing support')
fi
depends+=('desktop-file-utils' 'shared-mime-info' 'xdg-utils')

PKGEXT=".pkg.tar"

package() {
  #bsdtar -xf data.tar.xz
  cd wps-office_${_pkgver}

  install -d "$pkgdir/opt/kingsoft/wps-office"
  cp -r office6 "$pkgdir/opt/kingsoft/wps-office"

  install -d "$pkgdir/usr/bin"
  install -m755 wps wpp et wps_error_check.sh "$pkgdir/usr/bin"

  install -d "$pkgdir/usr/share/applications"
  cp -r resource/applications/* "$pkgdir/usr/share/applications"

  install -d "$pkgdir/usr/share/icons"
  cp -r resource/icons/* "$pkgdir/usr/share/icons"

  install -d "$pkgdir/usr/share/mime"
  cp -r resource/mime/* "$pkgdir/usr/share/mime"

  #cp -r "$srcdir/usr/share" "$pkgdir/usr/"

  install -d "$pkgdir/usr/share/fonts/wps-office"
  cp -r fonts/* "$pkgdir/usr/share/fonts/wps-office"

  install -Dm644 office6/mui/default/EULA.txt "$pkgdir/usr/share/licenses/$pkgname/EULA.txt"
}
