pkgname=amule-wx28
provides=('amule')
replaces=('amule')
conflicts=('amule')
pkgver=10834
pkgrel=1
pkgdesc="An eMule-like client for ed2k p2p network. Compiled with wxGTK 2.8."
arch=('i686' 'x86_64')
url="http://www.amule.org"
license=('GPL')
depends=('wxgtk2.8' 'gd' 'geoip' 'libupnp' 'crypto++' 'libsm')
makedepends=('wxgtk2.8' 'gd' 'geoip' 'libupnp' 'crypto++' 'libsm')
install=amule.install
source=("http://amule.sourceforge.net/tarballs/aMule-SVN-r${pkgver}.tar.bz2"
        'amuled.systemd'
        'amuleweb.systemd')
md5sums=('80e6375acbdc287b15cc92131bf9e027'
         '59772c41860e238f1c822feb8ca8d47f'
         '05975c5d94bfc41fddb894d98b1115d5')

build() {
  cd "${srcdir}/aMule-SVN-r${pkgver}"

  ./configure --prefix=/usr \
              --mandir=/usr/share/man \
              --enable-cas \
              --enable-wxcas \
              --enable-amule-daemon \
              --enable-amulecmd \
              --enable-amule-gui \
              --enable-alc \
              --enable-alcc \
              --enable-webserver \
              --disable-debug \
              --enable-optimize \
              --enable-ccache \
              --enable-geoip \
              --enable-upnp \
	      --with-wxversion=2.8
  make
}

package() {
  cd "${srcdir}/aMule-SVN-r${pkgver}"

  make DESTDIR=${pkgdir} install

  install -D -m644 "${srcdir}/amuled.systemd" "${pkgdir}/usr/lib/systemd/system/amuled.service"
  install -D -m644 "${srcdir}/amuleweb.systemd" "${pkgdir}/usr/lib/systemd/system/amuleweb.service"
}
