# Maintainer: Hu Butui <hot123tea123@gmail.com>

_realname=json
pkgbase=mingw-w64-${_realname}
pkgname=("${MINGW_PACKAGE_PREFIX}-${_realname}")
pkgver=3.10.4
pkgrel=1
pkgdesc="JSON for Modern C++"
arch=('any')
mingw_arch=('mingw32' 'mingw64' 'ucrt64' 'clang64' 'clang32')
url="https://github.com/nlohmann/json"
license=('MIT')
makedepends=("${MINGW_PACKAGE_PREFIX}-cmake")
source=("${_realname}-${pkgver}.tar.gz::https://github.com/nlohmann/json/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('1155fd1a83049767360e9a120c43c578145db3204d2b309eba49fbbedd0f4ed3')

build() {
  MSYS2_ARG_CONV_EXCL="-DCMAKE_INSTALL_PREFIX=" \
  ${MINGW_PREFIX}/bin/cmake.exe \
    -B "${srcdir}/build-${MINGW_CHOST}" \
    -DBUILD_SHARED_LIBS=OFF \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=${MINGW_PREFIX} \
    -DJSON_BuildTests=OFF \
    -DJSON_Install=ON \
    -G'MSYS Makefiles' \
    -S ${_realname}-${pkgver}
  ${MINGW_PREFIX}/bin/cmake.exe --build "${srcdir}/build-${MINGW_CHOST}"
}

package() {
  DESTDIR="${pkgdir}" \
  ${MINGW_PREFIX}/bin/cmake.exe \
    --build "${srcdir}/build-${MINGW_CHOST}" \
    --target install
}
