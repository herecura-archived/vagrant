# Maintainer: Jochen Schalanda <jochen+aur@schalanda.name>
# Contributor: Mathieu Clabaut <mathieu.clabaut@gmail.com>
# Contributor: helios <aur@wiresphere.de>
pkgname=vagrant
pkgver=1.7.3
pkgrel=1
pkgdesc="Tool for building and distributing virtualized development environments"
arch=('i686' 'x86_64')
url="http://vagrantup.com/"
license=('MIT')
options=(!strip)
optdepends=('net-tools: NFS shared folder support')
source=(
	"https://dl.bintray.com/mitchellh/${pkgname}/${pkgname}_${pkgver}_i686.rpm"
	"https://dl.bintray.com/mitchellh/${pkgname}/${pkgname}_${pkgver}_x86_64.rpm"
	'zsh-vagrant'
)
noextract=(
	"${pkgname}_${pkgver}_i686.rpm"
	"${pkgname}_${pkgver}_x86_64.rpm"
)

prepare() {
	bsdcpio -id < "${pkgname}_${pkgver}_${CARCH}.rpm"
}

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

sha256sums=('052e4c48f27a2491a3072a833724019a0ce50e2aa988ea56a71ba005e539b912'
            'ce7e47f7e1761fd57383f6c07d93961efa9076790e9de470b44a0795bc739baf'
            'e859db50cf6cf15b4fbde37a8528fe1191585c8961c28494d428394ccce54db2')
