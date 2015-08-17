# Contributor: cromo <dawid@klej.net>
# Contributor: SanskritFritz (gmail)

pkgname=plasmoid-embed-win
pkgver=1079983
pkgrel=2
pkgdesc="Displays any application in a plasmoid window"
arch=(i686 x86_64)
url="http://ksvladimir.blogspot.com/2008/06/converting-any-window-into-plasmoid.html"
license="GPL"
depends=('kdelibs' 'kdebase-workspace')
makedepends=('cmake' 'gcc>=4.*' 'automoc4' 'subversion')
source=()
md5sums=()

_svntrunk="svn://anonsvn.kde.org/home/kde/trunk/playground/base/plasma/applets/embed-win"
_svnmod="embed-win"

build()
{
	cd $startdir/src
	if [ -d $_svnmod/.svn ]; then
		(cd $_svnmod && svn up)
	else
		svn co $_svntrunk --config-dir ./ $_svnmod
	fi

	msg "SVN checkout done or server timeout"

	if [ -d $_svnmod-build ]; then
		rm -rf $_svnmod-build
	fi
	cp -r $_svnmod $_svnmod-build

	cd $_svnmod-build

	mkdir cmake-build
	cd cmake-build
	cmake ../ \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-DCMAKE_BUILD_TYPE=Release || return 1
	make || return 1
	make DESTDIR=$startdir/pkg install || return 1
}

