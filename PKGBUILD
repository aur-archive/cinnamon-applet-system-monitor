# Maintainer: ktalog <thektalog@gmail.com>
pkgname=cinnamon-applet-system-monitor
pkgver=1.2.0
pkgrel=3
pkgdesc="Display system informations in Cinnamon panel, such as memory usage, cpu usage, network rates"
arch=('any')
url="http://cinnamon-spices.linuxmint.com/applets/view/90"
license=('GPL3')
depends=('cinnamon' 'libgtop' 'networkmanager')
makedepends=('patch')
install=gschemas.install
source=('http://cinnamon-spices.linuxmint.com/uploads/applets/9Z6K-B8UW-ZWCY.zip'
		'applet.patch')
md5sums=('69a32eb34a5a671aebd31ce2aee0c233'
		 'f20c35d44319e718918f36eef89a114c')

package() {

	_applet_name="system-monitor@ebbes"
	cd ${srcdir}/$_applet_name/

	#apply patch
	patch applet.js ../applet.patch
	# Python2 fix
	sed -i 's|python|python2|' "config.py"

	cinnamon_dir="$pkgdir/usr/share/cinnamon/applets/$_applet_name"
	gschema_dir="$pkgdir/usr/share/glib-2.0/schemas"

	mkdir -p $cinnamon_dir
	mkdir -p $gschema_dir

	install -m0644 org.cinnamon.applets.system-monitor.gschema.xml $gschema_dir
	install -m0644 *.{js,json,py,css,compiled} README $cinnamon_dir
}
