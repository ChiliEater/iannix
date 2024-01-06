# Maintainer: VirtualTam <<virtualtam@flibidi.net>>
pkgname=iannix
pkgver=0.9.20.b.r19.g7d1870e
pkgrel=1
pkgdesc="A graphical sequencer, based on Iannis Xenakis' works, for digital art (Qt5)."
arch=('i686' 'x86_64')
url="http://www.iannix.org/"
license=('GPL3')
depends=('alsa-lib' 'gdk-pixbuf2' 'glu' 'qt5-script' 'qt5-tools')
makedepends=('gcc' 'git')
optdepends=('ffmpeg: record and convert audio streams'
            'libfreenect: XBox Kinect'
            'libwacom: Wacom tablets and trackpads')
provides=('iannix')
conflicts=('iannix-git' 'iannix-qt5-git')
_gitname=iannix
source=("${_gitname}::git+http://github.com/iannix/IanniX.git" "desktop.patch")
sha256sums=('SKIP' 'SKIP')

pkgver() {
  cd ${_gitname}
  git describe --long --tags | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
    cd ${_gitname}
    patch -Np1 -i "${srcdir}/desktop.patch"
}

build() {
  cd ${_gitname}
  PREFIX="/usr" qmake-qt5
  make
}

package() {
  cd ${_gitname}
  make INSTALL_ROOT="${pkgdir}" install
}
