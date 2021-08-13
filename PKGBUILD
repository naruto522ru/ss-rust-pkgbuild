# Maintainer :
_pkgname_dl=shadowsocks
_pkgname=shadowsocks-rust
pkgname=shadowsocks-rust-bin
pkgver=1.11.2
pkgrel=1
pkgdesc='A Rust port of shadowsocks https://shadowsocks.org/'
arch=('x86_64')
url='https://github.com/shadowsocks/shadowsocks-rust'
license=('MIT')
depends=('openssl')
#makedepends=()
conflicts=("shadowsocks-rust" "shadowsocks-git")
source=(
  "${_pkgname}-v${pkgver}.tar.xz::${url}/releases/download/v${pkgver}/${_pkgname_dl}-v${pkgver}.${arch}-unknown-linux-gnu.tar.xz"
  "https://raw.githubusercontent.com/naruto522ru/ss-rust-pkgbuild/binary/shadowsocks-rust%40.service"
  "https://raw.githubusercontent.com/naruto522ru/ss-rust-pkgbuild/binary/shadowsocks-rust-server%40.service"
  "https://raw.githubusercontent.com/naruto522ru/ss-rust-pkgbuild/binary/shadowsocks-rust-manager%40.service"
  "https://raw.githubusercontent.com/naruto522ru/ss-rust-pkgbuild/binary/sysusers"
  "https://raw.githubusercontent.com/naruto522ru/ss-rust-pkgbuild/binary/config.json"
  "https://raw.githubusercontent.com/naruto522ru/ss-rust-pkgbuild/binary/config_ext.json"
)
sha512sums=('26834fd2c30565edaf130443f428296e3383366ece4774e6e9628f69ad7cf9ea9dc2ee9246c2bb1b22c7b9d270ed34a73e10076aa8f8b24c2f9bb3ccb43e7d1d'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP')
package() {
  cd "${srcdir}/"
  install -Dm755 "sslocal" "${pkgdir}/usr/bin/sslocal-rust"
  install -Dm755 "ssserver" "${pkgdir}/usr/bin/ssserver-rust"
  install -Dm755 "ssurl" "${pkgdir}/usr/bin/ssurl-rust"
  install -Dm755 "ssmanager" "${pkgdir}/usr/bin/ssmanager-rust"
  install -Dm644 "shadowsocks-rust@.service" "${pkgdir}/usr/lib/systemd/system/shadowsocks-rust@.service"
  install -Dm644 "shadowsocks-rust-server@.service" "${pkgdir}/usr/lib/systemd/system/shadowsocks-rust-server@.service"
  install -Dm644 "shadowsocks-rust-manager@.service" "${pkgdir}/usr/lib/systemd/system/shadowsocks-rust-manager@.service"
  install -Dm644 "sysusers" "${pkgdir}"/usr/lib/sysusers.d/${pkgname}.conf
  install -Dm644 "config_ext.json" "${pkgdir}/etc/shadowsocks/config_ext_rust.json.example"
  install -Dm644 "config.json" "${pkgdir}/etc/shadowsocks/config_rust.json.example"
}

