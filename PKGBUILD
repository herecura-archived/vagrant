# Maintainer: Jochen Schalanda <jochen+aur@schalanda.name>
# Contributor: Mathieu Clabaut <mathieu.clabaut@gmail.com>
# Contributor: helios <aur@wiresphere.de>
pkgname=vagrant
pkgver=1.8.3
pkgrel=1
pkgdesc="Tool for building and distributing virtualized development environments"
arch=('i686' 'x86_64')
url="http://vagrantup.com/"
license=('MIT')
options=(!strip)
optdepends=('net-tools: NFS shared folder support')
source_i686=("https://releases.hashicorp.com/$pkgname/$pkgver/${pkgname}_${pkgver}_i686.rpm")
source_x86_64=("https://releases.hashicorp.com/$pkgname/$pkgver/${pkgname}_${pkgver}_x86_64.rpm")
source=(
	'zsh-vagrant'
)
sha256sums=('e859db50cf6cf15b4fbde37a8528fe1191585c8961c28494d428394ccce54db2')
sha256sums_i686=('c7e504843575950e09e9bbe30b85f2d52433f9368ba1a1bf352538f376be96da')
sha256sums_x86_64=('93258d6e534faa0a0e2ea571649b258f44e8da035d823d29e585821b24475883')

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

