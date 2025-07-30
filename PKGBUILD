# Maintainer: Doridian <archlinux@doridian.net>

pkgname=docker-sriov-plugin-git
pkgver=0.6.r16.gb8d6f3f
pkgrel=1
pkgdesc='Docker networking plugin for SRIOV and passthrough interfaces'
arch=('x86_64' 'i686')
gomodname='github.com/FoxDenHome/docker-sriov-plugin'
url="https://${gomodname}"
license=('Apache-2.0')
depends=()
makedepends=('go' 'git')
source=(
    "$pkgname::git+${url}.git"
)
sha256sums=(
    'SKIP'
)

pkgver() {
    cd "$pkgname"
    git describe --long --tags | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
    cd "${srcdir}/${pkgname}"
    go build -trimpath -o docker-sriov-plugin
}

package() {
    cd "${srcdir}/${pkgname}"
    install -Dm755 docker-sriov-plugin -t "${pkgdir}/usr/bin/"
    install -Dm644 docker-sriov-plugin.service -t "${pkgdir}/usr/lib/systemd/system/"
}
