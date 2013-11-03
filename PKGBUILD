# Maintainer: Kirill "reflexing" Churin <reflexing@reflexing.ru>
# Contributor: Andrej Gelenberg <andrej.gelenberg@udo.edu>

pkgname=keepass
pkgver=2.24
pkgrel=1
pkgdesc='KeePass Password Safe, the free, open source, light-weight and easy-to-use password manager'
arch=('any')
url='http://keepass.info/'
license=('GPL')
depends=('mono>=2.6' 'desktop-file-utils' 'xdg-utils' 'shared-mime-info' 'hicolor-icon-theme')
optdepends=('xdotool: if you want to use auto-type'
            'xsel: clipboard operations in order to work around Mono clipboard bugs')
install="$pkgname.install"
source=("http://downloads.sourceforge.net/keepass/KeePass-$pkgver.zip"
        'keepass'
        'keepass.1'
        'keepass.desktop'
        'keepass.xml'
        'KeePass.config.xml'
        'KeePass_6_256x256x32.png'
        'KeePass_7_48x48x32.png'
        'KeePass_8_32x32x32.png'
        'KeePass_9_16x16x32.png')

package() {
  cd "$srcdir"

  install -dm755 "$pkgdir"/usr/bin
  install -dm755 "$pkgdir"/usr/share/keepass/XSL

  install -Dm755 keepass "$pkgdir"/usr/bin/keepass
  install -Dm755 KeePass.exe "$pkgdir"/usr/share/keepass/KeePass.exe
  install -Dm755 KeePass.config.xml "$pkgdir"/usr/share/keepass/KeePass.config.xml
  install -Dm755 KeePass.exe.config "$pkgdir"/usr/share/keepass/KeePass.exe.config
  install -Dm755 KeePass.chm "$pkgdir"/usr/share/keepass/KeePass.chm

  install -m644 XSL/* "$pkgdir"/usr/share/keepass/XSL

  install -Dm644 keepass.1 "$pkgdir"/usr/share/man/man1/keepass.1

  # Proper installation of .desktop file
  desktop-file-install -m 644 --dir "$pkgdir"/usr/share/applications/ keepass.desktop

  # Install Icons (got from source package with "icotool -x KeePass.ico")
  for size in 16 32 48 256; do
    install -Dm644 \
    KeePass_*_${size}x${size}x32.png \
    "$pkgdir"/usr/share/icons/hicolor/${size}x${size}/apps/keepass.png
  done

  # Needed for postinst with xdg-utils
  install -Dm644 keepass.xml "$pkgdir"/usr/share/mime/packages/keepass.xml
}

md5sums=('800452a0d9ba78769c63d42fe04fcd74'
         'daa5d6c01c11cf38c6f5cc207333aa9a'
         'a2a0dff1ebf0aaf6cbfb6f8566f4a010'
         'e910fabacfd7a5f7caa7c1fac0b5254e'
         '1d7545e79e7aa1107a9f78cb46ced251'
         'ac0f1e104f82d295c27646bfff39fecc'
         '490859f348e492b5e33739262ff07f00'
         '5b060d5376e94f6743e787a46f53e9a3'
         '17044c8d69ad5275a2a57843b19ad89d'
         '4dfb6d0d6535c6d57ee88a4de7119095')
