# Maintainer: Jochen Schalanda <jochen+aur@schalanda.name>
# Contributor: Mathieu Clabaut <mathieu.clabaut@gmail.com>
# Contributor: helios <aur@wiresphere.de>
pkgname=vagrant
pkgver=2.0.0
pkgrel=2
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
    'https://github.com/hashicorp/vagrant/commit/83310f8a56cfea8a543d17f9af4b18caa13ed98a.patch'
)
sha256sums=('e859db50cf6cf15b4fbde37a8528fe1191585c8961c28494d428394ccce54db2'
            '44c13bd3e222e618e94ba66ebaf94a5c630bf94c55ebcfb19ba266e8549fb70b')
sha256sums_i686=('7913f4f5072f2e7be93949f53a4bb13adf811745547abe5387156d244c20640b')
sha256sums_x86_64=('0877da75b4c8433e2c48bafd5a01abf455140511b897ee85fe02d9dadc31df11')

package() {
	mv $srcdir/{opt,usr} $pkgdir

    (
        cd "$pkgdir/opt/vagrant/embedded/gems/gems/vagrant-$pkgver"
        patch -p1 -i "$srcdir/83310f8a56cfea8a543d17f9af4b18caa13ed98a.patch"
    )

	# zsh completion
	install -dm0755 "${pkgdir}/usr/share/zsh/site-functions"
	install -m0644 ${srcdir}/zsh-vagrant "${pkgdir}/usr/share/zsh/site-functions/_vagrant"

	# bash completion
	install -dm0755 "${pkgdir}/usr/share/bash-completion/completions"
	ln -sf "/opt/$pkgname/embedded/gems/gems/$pkgname-$pkgver/contrib/bash/completion.sh" \
		"${pkgdir}/usr/share/bash-completion/completions/vagrant"
}

