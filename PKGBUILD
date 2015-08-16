# Maintainer: Bastien Dejean <nihilhill@gmail.com>

_pkgname=mldonkey
pkgname=${_pkgname}-bskv
pkgver=3.1.3
pkgrel=2
pkgdesc='A multi-network P2P client'
arch=('i686' 'x86_64')
url="http://${_pkgname}.sourceforge.net"
license=('GPL')
depends=('zlib')
makedepends=('ocaml')
provides=("$_pkgname")
conflicts=("$_pkgname")
backup=("etc/conf.d/${_pkgname}")
install=${_pkgname}.install
source=("http://downloads.sourceforge.net/sourceforge/${_pkgname}/${_pkgname}-${pkgver}.tar.bz2"
        "${_pkgname}d"
        "${_pkgname}.conf"
        "${_pkgname}.service"
        "${_pkgname}.tmpfiles")
md5sums=('671f60467a918a9b7c2affef63ff5c25'
         'aa0731149fed0813740c2da4e610fd0a'
         '65aafb5e5563961c916c6d9510bd69cd'
         '9d37df25afdefc8ee27b01e2b99e1ab3'
         'cb8336207bbbe280bedf15d548aab90f')

build() {
    cd "${srcdir}/${_pkgname}-${pkgver}"
    ./configure --prefix=/usr --enable-minimum
    make
}

package() {
    cd "${srcdir}/${_pkgname}-${pkgver}"
    make DESTDIR="$pkgdir" install
    install -d     "$pkgdir/var/lib/${_pkgname}"
    install -Dm644 "$srcdir/${_pkgname}-${pkgver}/icons/rsvg/type_source_normal.svg" \
                   "$pkgdir/usr/share/icons/${_pkgname}.svg"
    install -Dm755 "$srcdir/${_pkgname}d" "$pkgdir/etc/rc.d/${_pkgname}"
    install -Dm644 "$srcdir/${_pkgname}.conf" "$pkgdir/etc/conf.d/${_pkgname}"
    install -Dm644 "$srcdir/${_pkgname}.service" "$pkgdir/usr/lib/systemd/system/${_pkgname}.service"
    install -Dm644 "$srcdir/${_pkgname}.tmpfiles" "$pkgdir/usr/lib/tmpfiles.d/${_pkgname}.conf"
}
