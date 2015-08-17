# Maintainer: Sander Boom <sander at inflowmotion dot nl>
# Contributor: realitygaps <realitygaps at yahoo dot com>

pkgname=sublime-text-3
pkgver=3.3065
pkgrel=1
pkgdesc="Sophisticated text editor for code, html and prose"
arch=('i686' 'x86_64')
url="http://www.sublimetext.com/3"
license=('custom')
depends=(libpng gtk2)
conflicts=(sublime-text-nightly)
provides=(sublime-text-nightly)
install=${pkgname}.install

_archurl='x64'

[[ "${CARCH}" = i686 ]] && _archurl='x32'

source=(
  "http://c758482.r82.cf2.rackcdn.com/sublime_text_3_build_${pkgver:2}_${_archurl}.tar.bz2"
  "sublime_text_3.desktop"
)
md5sums=('466ae754d2cd6aa80dd8dd8b571b4cac'
         '8ebb76a015353df90d9feba935921693')

[[ "${CARCH}" = i686 ]] && md5sums[0]='d0456b04a1f425f9119aa0615fbc4ceb'

package() {
  cd "${srcdir}"

  install -dm755 "${pkgdir}/opt"
  cp --preserve=mode -r "sublime_text_3" "${pkgdir}/opt/sublime_text_3"

  for res in 128x128 16x16 256x256 32x32 48x48; do
    install -dm755 "${pkgdir}/usr/share/icons/hicolor/${res}/apps"
    ln -s "/opt/sublime_text_3/Icon/${res}/sublime-text.png" "${pkgdir}/usr/share/icons/hicolor/${res}/apps/sublime-text.png"
  done

  install -dm755 "${pkgdir}/usr/share/applications"
  install -Dm644 "sublime_text_3.desktop" "${pkgdir}/usr/share/applications/sublime_text_3.desktop"

  install -dm755 "${pkgdir}/usr/bin"
  ln -s "/opt/sublime_text_3/sublime_text" "${pkgdir}/usr/bin/subl3"
}
