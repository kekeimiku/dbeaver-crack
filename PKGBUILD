# Maintainer: John Sivak <jsivak@winterjewel.com>
# Previous Maintainer: Joseph Post <joe@jcpst.com>
# Previous Maintainer: Stephan Wienczny <stephan@wienczny.de>
# Crack Maintainer: keke <kekelanact@gmail.com>

pkgname=dbeaver-ee
pkgver=21.2.0
pkgrel=1
pkgdesc="A universal database tool for developers and database administrators. Enterprise Edition includes NoSQL database support"
arch=('x86_64')
url="http://dbeaver.com/"
license=("Commercial")
depends=('gtk3' 'gtk-update-icon-cache')
install=dbeaver-ee.install

source=(dbeaver-ee.desktop dbeaver-ee.install
       "https://github.com/kekeimiku/dbeaver-crack/releases/download/21.2.0-1/dbeaver-agent.jar")
source_x86_64=("http://dbeaver.com/files/${pkgver}/dbeaver-ee-${pkgver}-linux.gtk.x86_64.tar.gz"
	       "https://github.com/kekeimiku/dbeaver-crack/releases/download/21.2.0-1/jre.tar.gz")
sha256sums=('453912912ae8377b16ef74a3e7d93ea588792ee8f7054a573e9fe9b93cd9265f'
            '0c2a75baa39459fa56159e982d9f28c966837561bd52dffd24bac87b8d65555f'
	    'ba948b068b4458401da36450bca3f686048daf5cd65be550fedd711422d37a55')
sha256sums_x86_64=(
    '9e05ced14ed0047d37c911c29c5e5a32af25a176d3631f3db2e163b2164d9e0b'
    'dc61abee78bd64ec801c2e5d1aecdb7753c7dcba92a31898ba37a6bb6325b6ec')

noextract=("dbeaver-ee-${pkgver}-linux.gtk.x86_64.tar.gz")

prepare() {
    mkdir -p $srcdir/$pkgname
    cd $srcdir/$pkgname
    tar -xf "$srcdir/dbeaver-ee-${pkgver}-linux.gtk.x86_64.tar.gz"
    tar -xf "$srcdir/jre.tar.gz"
}

package() {
    cd $pkgdir
    mkdir -p opt/
    mkdir -p usr/bin
    mkdir -p usr/share/applications
    mkdir -p usr/share/icons/hicolor/48x48/apps
    cp -r $srcdir/$pkgname/dbeaver opt/$pkgname

    rm opt/$pkgname/dbeaver.ini
    rm -rf opt/$pkgname/jre
    cp -r $srcdir/jre opt/$pkgname/
    cp $startdir/dbeaver.ini opt/$pkgname/
    cp $startdir/dbeaver-agent.jar opt/$pkgname/
    
    chmod +x opt/$pkgname/dbeaver
    cp opt/$pkgname/icon.xpm usr/share/icons/hicolor/48x48/apps/${pkgname}.xpm
    ln -s /opt/${pkgname}/dbeaver usr/bin/dbeaver-ee
    install -m 644 $srcdir/dbeaver-ee.desktop $pkgdir/usr/share/applications/
}
