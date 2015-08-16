# $Id$
# Maintainer: Hanspeter Portner <ventosus (at) airpost.net>

pkgname=lua5.2
pkgver=5.2.1
pkgrel=6
pkgdesc="A powerful light-weight programming language designed for extending applications." 
arch=('i686' 'x86_64')
url="http://www.lua.org/"
depends=('readline')
license=('MIT')
options=('!makeflags' '!emptydirs')
source=('http://www.lua.org/ftp/lua-5.2.1.tar.gz'
        '01_Makefile.patch'
        '02_Makefile.patch')
md5sums=(
'ae08f641b45d737d12d30291a5e5f6e3'
'dfdc07c4af1f403336fc4e047f679540'
'bd2f1fd3efdfab7d7ac6b8ef0ce822f2')

build() { 
  cd "${srcdir}/lua-5.2.1"
	cd doc
	cp lua.1 lua5.2.1
	cp luac.1 luac5.2.1
	cd ..
	patch -p0 < "${srcdir}/01_Makefile.patch"
	cd src
  patch -p0 < "${srcdir}/02_Makefile.patch"
	cd ..
	make INSTALL_DATA="cp -d" INSTALL_TOP="${pkgdir}/usr" linux
}

package() {
  cd "${srcdir}/lua-5.2.1"
	make INSTALL_DATA="cp -d" INSTALL_TOP="${pkgdir}/usr" install
	head -n 405 doc/readme.html | tail -n 22 > COPYRIGHT
	install -D -m644 COPYRIGHT "${pkgdir}/usr/share/licenses/${pkgname}/COPYRIGHT"
}
