# Merged with official ABS milou PKGBUILD by João, 2021/03/05 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: zan <zan@420blaze.it>
# Contributor: Antonio Rojas < nqn1976 @ gmail.com >

pkgname=milou-git
pkgver=5.21.80_r728.gc7bb4d0
pkgrel=1
pkgdesc="A dedicated search application built on top of Baloo"
arch=($CARCH)
url='https://kde.org/plasma-desktop/'
license=(LGPL)
depends=(krunner-git kitemmodels-git)
makedepends=(git extra-cmake-modules-git kdoctools-git)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
groups=(plasma-git)
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(PROJECT_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
