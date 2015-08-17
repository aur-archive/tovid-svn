# Maintainer: Keerthi <keerthi.linux@gmail.com>

arch=('i686' 'x86_64')
pkgname=tovid-svn
pkgver=3493
pkgrel=1
pkgdesc="A suite of utilities designed to make VCD, SVCD, and DVD authoring a little less painful. (project moved, current version is tovid-git)"
url="http://www.tovid.org"
license="GPL"
depends=('mplayer' 'mjpegtools' 'ffmpeg' 'wxpython' 'python2-cairo' \
'imagemagick' 'dvdauthor' 'dvd+rw-tools' 'vcdimager' 'transcode' 'sox' 'normalize' 'python2-pillow')
makedepends=('txt2tags' 'subversion')
conflicts=('tovid')
source=()
md5sums=()
_svntrunk=http://tovid.googlecode.com/svn/trunk/
_svnmod=tovid

build() {
  cd $srcdir
  
  if [ -d $_svnmod/.svn ]; then
    cd $_svnmod && svn up -r $pkgver
  else
    svn co $_svntrunk --config-dir ./ -r $pkgver $_svnmod
  fi
                
  msg "SVN checkout done or server timeout"
  msg "Building..."
                    
  cp -r $_svnmod $_svnmod-build
  cd $_svnmod-build/$_svnmod
                        
  ./setup.py build
}

package() {
  cd $srcdir
  cd $_svnmod-build/$_svnmod
  ./setup.py install --prefix=/usr --root="$pkgdir"
  rm -rf $srcdir/$_svnmod-build
}


