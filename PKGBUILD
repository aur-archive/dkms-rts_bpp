# Maintainer: coudu <coudu@wanadoo.fr>
# Contributor: Lekensteyn <lekensteyn@gmail.com>

pkgname=dkms-rts_bpp
_pkgname=rts_bpp
pkgver=1.1
pkgrel=6
pkgdesc="A kernel module for Realtek Card Reader RTL8411 Device 5289, dkms version"
url="http://www.realtek.com.tw"
license=("GPL")
arch=('i686' 'x86_64')
provides=('rts_bpp')
conflicts=('rts_bpp')
depends=('dkms')
source=("https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/971876/+attachment/2991730/+files/${_pkgname}.tar.bz2" 'set_max_lun_id_to_avoid_bad_lun_target_message.patch' 'rtsx-remove-devinit.patch' 'dkms.conf.in' "81-udisks-udisks2-${_pkgname}.rules" "remove_time_macro.patch")
md5sums=('85990e67ce6a10ae501ffeab4cb0b813'
         '6fc2803f4f558d4a9d3c58feb3a89f55'
         'cc3df93be0dcd1a37c9363be93f874b5'
         '56d2fb0184d7eb17cec3d553b870d185'
         '2cb27673c68f68b10199fc6ec9c05a24'
		 '5e75baeca78fb6354d7afb567c53e454')
install=${pkgname}.install

build() {
	cd ${srcdir}/${_pkgname}
	patch -i ../set_max_lun_id_to_avoid_bad_lun_target_message.patch
        patch -i ../rtsx-remove-devinit.patch
}

package() {
	install -dm755 "${pkgdir}/usr/lib/udev/rules.d/"
        install -D -m644 ${srcdir}/81-udisks-udisks2-${_pkgname}.rules "${pkgdir}/usr/lib/udev/rules.d/"
        install -dm755 "${pkgdir}/usr/src/${_pkgname}-${pkgver}/"
        cp -a ${srcdir}/${_pkgname}/*  ${pkgdir}/usr/src/${_pkgname}-${pkgver}
        sed "s/#MODULE_VERSION#/${pkgver}/" "${srcdir}/dkms.conf.in" > "${pkgdir}/usr/src/${_pkgname}-${pkgver}/dkms.conf"
}

