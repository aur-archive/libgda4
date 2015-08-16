# Maintainer: tobias <tobias@archlinux.org>
# Contributor: Tobias Kieslich <tobias@justdreams.de>

pkgname=libgda4
pkgver=4.2.10
pkgrel=1
pkgdesc="Data abstraction layer with mysql, pgsql, xml, sqlite providers"
arch=('i686' 'x86_64')
url="http://www.gnome-db.org"
license=('GPL')
depends=('gtksourceview2' 'libunique' 'libxslt' 'libsoup'
         'libmysqlclient' 'postgresql-libs' 'python2' 'libgnome-keyring'
         'hicolor-icon-theme' 'desktop-file-utils')
makedepends=('intltool' 'gobject-introspection' )
install=libgda.install
source=(http://ftp.gnome.org/pub/GNOME/sources/libgda/${pkgver%.*}/libgda-${pkgver}.tar.xz)
sha256sums=('cfaf228c62fbdb461c3bfedad919d5dfeb6a2e624c223910e275a53b97d3a431')

build() {
  cd "${srcdir}"/libgda-${pkgver}

  sed -i '1s/python$/&2/' libgda-report/RML/trml*/trml*.py
  ./configure --prefix=/usr --sysconfdir=/etc \
      --with-bdb=/usr --with-bdb-libdir-name=lib \
      --disable-static \
      --disable-gtk-doc 
  make
}

package() {
  cd "${srcdir}"/libgda-${pkgver}

  make DESTDIR="${pkgdir}" install

  rm -rf "${pkgdir}"/usr/share/icons
  rm -rf "${pkgdir}"/usr/share/gtk-doc
  rm -rf "${pkgdir}"/usr/bin/{gda-list-config,gda-list-server-op,gda-sql}
  rm -rf "${pkgdir}"/usr/share/man/man1/gda-sql.1
}
