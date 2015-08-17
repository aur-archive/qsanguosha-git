# Author: Moligaloo <Moligaloo@gmail.com>
# Maintainer: Iven Hsu <ivenvd@gmail.com>
# Contributor: Yangtse <yangtsesu@gmail.com> 
# Contributor: Vehiclee <>
# Contributor: abf <zouxiaomingabf@gmail.com>

pkgname=qsanguosha-git
_gitname=QSanguosha
pkgver=5085.4786b1c
pkgrel=1
pkgdesc="An open source online version of the famous board game Sanguosha"
arch=('i686' 'x86_64')
url="https://github.com/Moligaloo/QSanguosha"
license=('GPL2')
depends=('qt4' 'phonon' 'plib' 'lua' 'fmodex')
makedepends=('gcc' 'make' 'git' 'swig')
conflicts=(qsanguosha)
provides=(qsanguosha)
options=(!strip)
source=('git://github.com/gaodayihao/QSanguosha.git' 'qsanguosha' 'qsanguosha.desktop' 'sgs.png')
md5sums=('SKIP'
'49ccb51ea1ba979f8c8b469b122f69d6'
'c8180a5a852ea23f194f49e60e2b0b02'
'c727b12c3a46b56fd0151eae5ef4c6c5')

pkgver() {
  cd $_gitname
  echo $(git rev-list --count master).$(git rev-parse --short master)
}

build() {
    cd ${srcdir}/${_gitname}/swig
    swig -c++ -lua sanguosha.i
    cd ${srcdir}/${_gitname}
    qmake-qt4 QSanguosha.pro
    make
    lrelease-qt4 QSanguosha.pro
}

package() {
    cd ${srcdir}/${_gitname}
    mkdir -p ${pkgdir}/opt/qsanguosha
    cp -R {lib,font,doc,audio,diy,etc,extension-doc,QSanguosha,qt_zh_CN.qm,backdrop,image,lang,scenarios,lua,sanguosha.qm,sanguosha.qss,skins} ${pkgdir}/opt/qsanguosha/
    install -D -m755 ${srcdir}/qsanguosha "${pkgdir}/usr/bin/qsanguosha"
    install -D -m644 ${srcdir}/qsanguosha.desktop "${pkgdir}/usr/share/applications/qsanguosha.desktop"
    install -D -m644 ${srcdir}/sgs.png "${pkgdir}/usr/share/pixmaps/QSanguosha.png"
}

