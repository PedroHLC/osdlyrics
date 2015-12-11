pkgname=osdlyrics-wip
provides=osdlyrics
conflicts=('osdlyrics' 'osdlyrics-pedrohlc' 'osdlyrics-git')
_pkgver=0.4.99
pkgver=$_pkgver
pkgrel=1
pkgdesc="A lyric show compatible with various media players + experimental ViewLyrics source + bug fixes"
arch=('i686' 'x86_64')
url="http://code.google.com/p/osd-lyrics/"
license=('GPL3')
depends=('dbus-glib' 'desktop-file-utils' 'gtk2' 'hicolor-icon-theme' 'libnotify'
         'python2-dbus' 'python2-chardet' 'python2-gobject2' 'python2-pycurl'
         'sqlite')
makedepends=('intltool')
optdepends=('gobject-introspection-runtime: proxy detection on Gnome'
            'kdebindings-python2: proxy detection on KDE'
            'python2-mpd: to interface with MPD')
install=$provides.install



pkgver() {
    cd ..
    printf "$_pkgver.r%s" "$(git rev-list --count HEAD)"
}

build()
{
    cd ..
    ./autogen.sh
    ./configure --prefix=/usr PYTHON=/usr/bin/python2
    make
}

package()
{
    cd ..
    make DESTDIR="$pkgdir" install
}
