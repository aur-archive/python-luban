# Contributor: Lex Black <autumn-wind at web dot de>
# Contributor: Tianjiao Yin <ytj000@gmail.com>
# Contributor: tocer <tocer.deng@gmail.com>

pkgname=python-luban
pkgver=1.0.1
pkgrel=3
pkgdesc="generic (web/native) user interface language"
arch=("any")
url="http://lubanui.org"
license=('custom')
depends=('python-cherrypy>=3.2.0' 'python-docutils')
makedepends=('python-setuptools')
source=("http://dev.danse.us/packages/luban-$pkgver.tar.gz"
        "fix_python_v3.3_1.patch"
        "fix_python_v3.3_2.patch")
md5sums=('58ea0c260d324eb2e1dd88ead7e24c3c'
         'f98fd230f80ab71b13e19417b9060c97'
         '017fb17bb8679a3ebc0630d26fc73713')


prepare() {
  cd $srcdir/luban-$pkgver/EXPORT/packages
  patch -p 1 < $srcdir/fix_python_v3.3_1.patch
  cd luban/timber
  patch -p 2 < $srcdir/fix_python_v3.3_2.patch
}

package() {
  cd $srcdir/luban-$pkgver
  python setup.py install --root=$pkgdir/ --prefix=/usr --optimize=1
  install -D -m644 LICENSE $pkgdir/usr/share/licenses/$pkgname/LICENSE
}
