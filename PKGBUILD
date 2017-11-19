# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://projects.archlinux.org/svntogit/packages.git/tree/trunk?h=packages/pcmciautils
# 						Maintainer: Tom Gundersen <teg@jklm.no>
# 						Contributor: Tobias Powalowski <tpowa@archlinux.org>

pkgname=pcmciautils
pkgver=018
pkgrel=8
pkgdesc="Utilities for inserting and removing PCMCIA cards"
arch=('x86_64')
url="http://kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html"
license=('GPL')
groups=('base')
conflicts=('pcmcia-cs')
source=(https://sources.archlinux.org/other/${pkgname}/${pkgname}-$pkgver.tar.xz
        initcpio-install-pcmcia)
options=(!makeflags)
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

build() {
  cd "${pkgname}-$pkgver"
  sed -i -e 's,/lib/udev,/usr/lib/udev,g' Makefile
  sed -i -e 's,/sbin,/usr/bin,g' Makefile
  make
}

package() {
  make -C "${pkgname}-$pkgver" DESTDIR="$pkgdir" install

  # install the mkinitpcio hook
  install -Dm644 initcpio-install-pcmcia "$pkgdir/usr/lib/initcpio/install/pcmcia"
}
md5sums=('2e9469c44dcb790d2b497723c2fa0566'
         '041af04025daee5b3b05812ac3896c8f')
