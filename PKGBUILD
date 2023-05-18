# Maintainer:

pkgname=shadowsocks-rust
pkgver=1.15.3
pkgrel=2
pkgdesc='A Rust port of shadowsocks https://shadowsocks.org/'
arch=('any')
url='https://github.com/shadowsocks/shadowsocks-rust'
license=('MIT')
depends=('openssl')
makedepends=('rust' 'libsodium' 'git')
optdepends=('v2ray-plugin-git: support SIP003 plugin'
            'simple-obfs: support simple obfuscating tool')
provides=('shadowsocks-rust-git' 'shadowsocks-rust-bin')
conflicts=('shadowsocks-rust-git' 'shadowsocks-rust-bin')
source=(
  "${pkgname}::git+${url}.git#tag=v${pkgver}"
  'shadowsocks-rust@.service'
  'shadowsocks-rust-server@.service'
  'shadowsocks-rust-manager@.service'
  'sysusers'
  'config.json'
  'config_ext.json'
)

sha512sums=('SKIP'
            '430503b00615b6b441179f76dfa3cf267d1b3a5af8ddd502a2f25bb1000bcf4a2565334baa3d37396b806b920579a01f36736e529b30c7176d909d0ed3079f00'
            'a745c520e8f75e02ef9c455be8c80c449bd5b0b83b3f99d3782ac73db0ebfaa44bb98cd1d5707a6e06776244d024a16d43ad5965d413afc847205e13b3e8c467'
            'b1d2543e99fc6450e84cdfb487e4aacc4acc72a681d9e72d5d3772023df18aab7dac36826e45b1ad21288f8839a857f55f4a53dcefe952d97a74d47f27ea1650'
            '2f9ad26dde4ba8ae069faa96158d880adad300306848a575e612183bbada1b4198840420e91bc20ba02c27adb07defe2843f1790e4e5ed0a9a41db7d6aa927e3'
            'SKIP'
            'SKIP')
build() {
  cd "${srcdir}/${pkgname}"
  #export RUSTFLAGS="-C target-cpu=native"
  cargo build --release -F local-redir -F local-tun
}

package() {
  cd "${srcdir}"
  install -Dm755 "${pkgname}/target/release/sslocal" "${pkgdir}/usr/bin/sslocal-rust"
  install -Dm755 "${pkgname}/target/release/ssserver" "${pkgdir}/usr/bin/ssserver-rust"
  install -Dm755 "${pkgname}/target/release/ssurl" "${pkgdir}/usr/bin/ssurl-rust"
  install -Dm755 "${pkgname}/target/release/ssmanager" "${pkgdir}/usr/bin/ssmanager-rust"
  install -Dm755 "${pkgname}/target/release/ssservice" "${pkgdir}/usr/bin/ssservice-rust"
  install -Dm644 "shadowsocks-rust@.service" "${pkgdir}/usr/lib/systemd/system/shadowsocks-rust@.service"
  install -Dm644 "shadowsocks-rust-server@.service" "${pkgdir}/usr/lib/systemd/system/shadowsocks-rust-server@.service"
  install -Dm644 "shadowsocks-rust-manager@.service" "${pkgdir}/usr/lib/systemd/system/shadowsocks-rust-manager@.service"
  install -Dm644 "sysusers" "${pkgdir}"/usr/lib/sysusers.d/${pkgname}.conf
  install -Dm644 "config_ext.json" "${pkgdir}/etc/shadowsocks/config_ext_rust.json.example"
  install -Dm644 "config.json" "${pkgdir}/etc/shadowsocks/config_rust.json.example"
}
