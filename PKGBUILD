# Maintainer: Tomislav Ivek <tomislav.ivek@gmail.com>

pkgname=('conan')
pkgver=0.22.1
pkgrel=2
pkgdesc="A distributed, open source, C/C++ package manager."
arch=('any')
url="https://conan.io"
license=('MIT')
makedepends=('python-setuptools')
depends=('python-pyjwt>=1.4.0' 'python-pyjwt<1.5.0'
         'python-requests>=2.7.0' 'python-requests<2.14.0'
         'python-colorama>=0.3.3' 'python-colorama<0.4.0'
         'python-yaml>=3.11' 'python-yaml<3.13.0'
         'python-patch=1.16'
         'python-fasteners>=0.14.1'
         'python-six>=1.10.0'
         'python-node-semver=0.1.1'
         'python-bottle>=0.12.8' 'python-bottle<0.13'
         'python-distro>=1.0.2' 'python-distro<1.1.0'
         'python-pluginbase>=0.5' 'python-pluginbase<1.0'
         'python-pylint>=1.6.4' 'python-pylint<1.6.6'
         'python-future=0.16.0')
source=("https://github.com/conan-io/conan/archive/${pkgver}.tar.gz" "pylint-1.6.4.patch")
sha512sums=('cadd12cfcf483d67eb818ddb6d1bc66fe5a58ec5bddd4cd0075f0aa36cd24b5487dffa0eb52cdb49abe4e4240e70c8aaf24d44b0a02f50016e015e08e86d06e7'
            '2d4ccf533f3d6efb478cdcecc6b1e320fa1dcfe8328c7f288bfc735c99a5ae5741446a1df69cd8dbb166fd84f801bb473d1f15026ca8773f73f7640475a40aa6')

prepare() {
 cd $pkgname-$pkgver
  patch -Np1 -i "${srcdir}/pylint-1.6.4.patch"
  }
  

build() {
  cd "$srcdir/conan-$pkgver"
  python setup.py build
}

package() {
  cd "$srcdir/conan-$pkgver"
  python setup.py install --optimize=1 --root=${pkgdir}
  install -m755 -d "${pkgdir}/usr/share/licenses/conan"
  install -m644 LICENSE.md "${pkgdir}/usr/share/licenses/conan/"
  install -m755 -d "${pkgdir}/usr/share/doc/conan"
  install -m644 contributors.txt "${pkgdir}/usr/share/doc/conan/"
}
