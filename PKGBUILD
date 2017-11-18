# Maintainer: Jochen Schalanda <jochen+aur@schalanda.name>
# Contributor: Mathieu Clabaut <mathieu.clabaut@gmail.com>
# Contributor: helios <aur@wiresphere.de>
pkgname=vagrant
pkgver=2.0.1
pkgrel=2
pkgdesc="Tool for building and distributing virtualized development environments"
arch=('x86_64')
url="http://vagrantup.com/"
license=('MIT')
options=(!strip)
depends=('net-tools')
source_x86_64=("https://releases.hashicorp.com/$pkgname/$pkgver/${pkgname}_${pkgver}_x86_64.rpm")
source=(
	'zsh-vagrant'
)
sha256sums=('e859db50cf6cf15b4fbde37a8528fe1191585c8961c28494d428394ccce54db2')
sha256sums_x86_64=('df28c4ba7420dc6983955cf3af66dddddd892ad852154e9b9dbcd1acbebc083c')

package() {
	mv $srcdir/{opt,usr} $pkgdir

    # remove breaking embedded libcurl
    rm "$pkgdir/opt/vagrant/embedded/lib/libcurl"*

	# zsh completion
	install -dm0755 "${pkgdir}/usr/share/zsh/site-functions"
	install -m0644 ${srcdir}/zsh-vagrant "${pkgdir}/usr/share/zsh/site-functions/_vagrant"

	# bash completion
	install -dm0755 "${pkgdir}/usr/share/bash-completion/completions"
	ln -sf "/opt/$pkgname/embedded/gems/gems/$pkgname-$pkgver/contrib/bash/completion.sh" \
		"${pkgdir}/usr/share/bash-completion/completions/vagrant"
}

