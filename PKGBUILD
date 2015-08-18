# $Id$
# Contributor: Evangelos Foutras <evangelos@foutrelis.com>
# Contributor: tobias <tobias funnychar archlinux.org>
# Maintainer: Aaditya Bagga <aaditya_gnulinux@zoho.com>

pkgname=xfce4-session-nosystemd
_prgname=xfce4-session
pkgver=4.11.0
pkgrel=2
pkgdesc="A session manager for Xfce, with logind systemd disabled"
arch=('i686' 'x86_64')
url="http://www.xfce.org/"
license=('GPL2')
groups=('xfce4')
depends=('libxfce4ui' 'libwnck' 'libsm' 'xorg-iceauth' 'upower' 'xorg-xinit'
         'xorg-xrdb' 'hicolor-icon-theme')
conflicts=('xfce4-session')
provides=('xfce4-session')
makedepends=('intltool' 'xfce4-dev-tools')
optdepends=('gnome-keyring: for keyring support when GNOME compatibility is enabled'
            'xscreensaver: for locking screen with xflock4'
            'gnome-screensaver: for locking screen with xflock4'
            'xlockmore: for locking screen with xflock4'
	    'consolekit: for rebooting or shutting down as normal user')
replaces=('xfce-utils')
install=$_prgname.install
source=(http://archive.xfce.org/src/xfce/$_prgname/4.11/$_prgname-$pkgver.tar.bz2)
sha256sums=('c68905b5124382e30e90f7e4f080fd7e24d58a065991eba9cfcb99e5d59a7c8e')

prepare() {
  cd "$srcdir/$_prgname-$pkgver"

  # Use logind interfaces for suspend and hibernate
  # https://bugzilla.xfce.org/show_bug.cgi?id=9952
  #patch -Np1 -i "$srcdir/xfce4-session-4.10.1-logind-support-for-suspend-hibernate.patch"

  xdt-autogen
}

build() {
  cd "$srcdir/$_prgname-$pkgver"

  ./configure \
    --prefix=/usr \
    --sysconfdir=/etc \
    --libexecdir=/usr/lib/xfce4 \
    --localstatedir=/var \
    --disable-static \
    --disable-systemd \
    --disable-debug
  make
}

package() {
  cd "$srcdir/$_prgname-$pkgver"
  make DESTDIR="$pkgdir" install
}

# vim:set ts=2 sw=2 et:
