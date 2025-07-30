# Maintainer: Doridian <archlinux@doridian.net>

pkgname=docker-sriov-plugin
pkgver=1.9.1
pkgrel=1
pkgdesc='Docker networking plugin for SRIOV and passthrough interfaces'
arch=('x86_64' 'i686')
url="https://github.com/FoxDenHome/${pkgname}"
license=('Apache-2.0')
depends=()
makedepends=('go')
source=(
    "${pkgname}-${pkgver}.tar.gz::${url}/archive/refs/tags/v${pkgver}.tar.gz"
)
sha256sums=(
    'c8b7c345ea8a8b2530fede768a4af51641b966fdd44cb1b23b1efb30a5d00e20'
)

prepare() {
    cd "${srcdir}"
    tar -xf "${pkgname}-${pkgver}.tar.gz"
    cd "${pkgname}-${pkgver}"
    go mod download
}

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    go build -trimpath -o docker-sriov-plugin
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    install -Dm755 docker-sriov-plugin -t "${pkgdir}/usr/bin/"
    install -Dm644 docker-sriov-plugin.service -t "${pkgdir}/usr/lib/systemd/system/"
}
