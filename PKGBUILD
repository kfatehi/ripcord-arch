# Basing this off upwork-appimage.git and gulden-appimage
# https://aur.archlinux.org/cgit/aur.git/tree/PKGBUILD?h=gulden-appimage
# https://aur.archlinux.org/cgit/aur.git/tree/PKGBUILD?h=upwork-appimage
_pkgname=ripcord
_upkgname=Ripcord
pkgname=ripcord-appimage
pkgver=0.2.83
pkgrel=1
pkgdesc="A desktop chat client for Discord (and soon Slack)"
arch=('x86_64')
url='https://cancel.fm/ripcord/'
license=('unknown')
options=('!strip') # need to disable binary stripping in order for the appimage not to get corrupted
depends=('p7zip')

noextract=("$_upkgname-$pkgver-${CARCH}.AppImage")

source_x86_64=("https://cancel.fm/dl/${_upkgname}-${pkgver}-${CARCH}.AppImage")
md5sums_x86_64=('5a7a7c702aabd093577f43fb6b90b062')

prepare() {
  cd "${srcdir}"

  # Extract relevant files from AppImage, redirect to /dev/null to avoid spamming the terminal
  7z x -y "${srcdir}/$_upkgname-$pkgver-$CARCH.AppImage" "${_upkgname}_Icon.png" > /dev/null
  7z x -y "${srcdir}/$_upkgname-$pkgver-$CARCH.AppImage" "${_upkgname}.desktop" > /dev/null
  sed -i "s/Exec=Ripcord/Exec=\/opt\/appimages\/$_upkgname-$pkgver-$CARCH.AppImage/" "${_upkgname}.desktop"
}

package() {
  cd "${srcdir}"
  install -Dm644 "${_upkgname}_Icon.png" "$pkgdir/usr/share/pixmaps/$_pkgname.png"
  install -Dm644 "${_upkgname}.desktop" "$pkgdir/usr/share/applications/$_pkgname.desktop"
  install -Dm755 "${_upkgname}-$pkgver-$CARCH.AppImage" "$pkgdir/opt/appimages/$_upkgname-$pkgver-$CARCH.AppImage"
}
