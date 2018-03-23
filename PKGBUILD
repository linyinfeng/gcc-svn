# Maintainer: Lin Yinfeng <lin.yinfeng@outlook.com>
pkgname=gcc-svn
pkgver=VERSION
pkgrel=1
pkgdesc="GCC svn"
arch=(any)
url=""
license=('GPL')
groups=()
depends=()
makedepends=(svn gcc glibc awk binutils make perl)
optdepends=()
provides=()
conflicts=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=("trunk::svn+svn://gcc.gnu.org/svn/gcc/trunk")
noextract=()
md5sums=('SKIP')

# Cancel all flags and let configure and make decide them
CPPFLAGS= CFLAGS= CXXFLAGS= LDFLAGS= DEBUG_CFLAGS= DEBUG_CXXFLAGS=

pkgver() {
    cd "$srcdir/trunk"
    printf "r%s" "$(svnversion | tr -d 'A-z')"
}

build() {
    cd "$srcdir/trunk"
    ./contrib/download_prerequisites

    cd ..
    mkdir -p build
    cd build
    ../trunk/configure --prefix="/opt/$pkgname" --enable-checking=release
    make
}

package() {
    cd "$srcdir/build"
    make DESTDIR="$pkgdir/" install
}
