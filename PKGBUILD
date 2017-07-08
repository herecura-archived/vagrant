# Maintainer: Jochen Schalanda <jochen+aur@schalanda.name>
# Contributor: Mathieu Clabaut <mathieu.clabaut@gmail.com>
# Contributor: helios <aur@wiresphere.de>
pkgname=vagrant
pkgver=1.9.7
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
sha256sums_i686=('7dbf96cb46890bd86c89be7b00f4df717dc866997e0ec2f82c45a9fa6352a006')
sha256sums_x86_64=('0ee22a74afb6e8fd58908a05db4be7055e5bbf177b4c79ca681d768ef164282f')

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

