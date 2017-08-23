# Maintainer: Jochen Schalanda <jochen+aur@schalanda.name>
# Contributor: Mathieu Clabaut <mathieu.clabaut@gmail.com>
# Contributor: helios <aur@wiresphere.de>
pkgname=vagrant
pkgver=1.9.8
pkgrel=1
pkgdesc="Tool for building and distributing virtualized development environments"
arch=('i686' 'x86_64')
url="http://vagrantup.com/"
license=('MIT')
options=(!strip)
depends=('net-tools')
source_i686=("https://releases.hashicorp.com/$pkgname/$pkgver/${pkgname}_${pkgver}_i686.rpm")
source_x86_64=("https://releases.hashicorp.com/$pkgname/$pkgver/${pkgname}_${pkgver}_x86_64.rpm")
source=(
	'zsh-vagrant'
)
sha256sums=('e859db50cf6cf15b4fbde37a8528fe1191585c8961c28494d428394ccce54db2')
sha256sums_i686=('34e84aced68e9f645e85ff4b56e49c99631e7bd5025f438067611da8e7d09ff1')
sha256sums_x86_64=('ecd58653b384224a121ad139c028468eafb66ead7f5e804ca45fb2e2014d462e')

package() {
	mv $srcdir/{opt,usr} $pkgdir

	# zsh completion
	install -dm0755 "${pkgdir}/usr/share/zsh/site-functions"
	install -m0644 ${srcdir}/zsh-vagrant "${pkgdir}/usr/share/zsh/site-functions/_vagrant"

	# bash completion
	install -dm0755 "${pkgdir}/usr/share/bash-completion/completions"
	ln -sf "/opt/$pkgname/embedded/gems/gems/$pkgname-$pkgver/contrib/bash/completion.sh" \
		"${pkgdir}/usr/share/bash-completion/completions/vagrant"
}

