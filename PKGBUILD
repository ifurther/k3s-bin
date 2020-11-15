# Maintainer: duxet <duxetlg@gmail.com>
pkgbase=k3s
pkgname=("$pkgbase-server" "$pkgbase-agent")
pkgver=1.19.3+k3s1
pkgrel=1
pkgdesc="Lightweight Kubernetes"
url="https://k3s.io"
license=('Apache')
arch=('x86_64' 'armv7h' 'aarch64')
conflicts=('k3s-git')
install=k3s.install
makedepends=(
  "go"
)
optdepends=(
  "wireguard-go-git"
  "wirequard-tools"
)
source=(
  "k3s.service"
  "k3s.service.env"
  "k3s-agent.service"
  "k3s-agent.service.env"
  "ufw-k3s"
)

source_x86_64=(
  "k3s-${pkgver}-x86_64::https://github.com/rancher/k3s/releases/download/v${pkgver}/k3s"
)

source_armv7h=(
  "k3s-${pkgver}-armv7h::https://github.com/rancher/k3s/releases/download/v${pkgver}/k3s-armhf"
)

source_aarch64=(
  "k3s-${pkgver}-aarch64::https://github.com/rancher/k3s/releases/download/v${pkgver}/k3s-arm64"
)

sha256sums=('f4ae496b69b3dd376a28298df50297728a47761b041be522adf2537aa8a8c3d8'
            '667199fa6b811dde3aef3e626e2695a566ad64c9a03d19d0c94a1f104a7612d0'
            'ca0c1f7cc935378dafd80962ce77c13ca1a21a972e0ea98859f98dd9e357353e'
            '1a18868b8f51b179418d02dc5a77e3bfae8659b5ecb99589e2fe9ac24877b816'
            '4fdae1e0972ac95cf7a4272e0dae872409d708388c244aabd3ab9e460ac571a8')
sha256sums_x86_64=('3b031d78f9edeed6718b5cd1070e4bd46524faa90a82d64f6f28008f6192c5dc')
sha256sums_armv7h=('2a4e1d6f37219b9daa4c2e5d16d8181c004fa00ea5b081756182027f7810f4fd')
sha256sums_aarch64=('92ed9560b700bcd79b49e1f5229a6b6b6afce7facc676abf936bd32550dfa315')




package_k3s-server() {
  install -Dm 755 $srcdir/k3s-${pkgver}-${CARCH} $pkgdir/usr/bin/k3s

  install -dm 755 $pkgdir/usr/lib/systemd/system
  install -dm 755 $pkgdir/etc/systemd/system
  install -dm 755 $pkgdir/etc/ufw/applications.d

  install -m 644 $srcdir/k3s.service $pkgdir/usr/lib/systemd/system/k3s.service
  install -m 400 $srcdir/k3s.service.env $pkgdir/etc/systemd/system/k3s.service.env
  install -m 644 $srcdir/ufw-k3s $pkgdir/etc/ufw/applications.d/ufw-k3s
  
  backup=("etc/systemd/system/k3s.service.env")

}

package_k3s-agent() {
  install -Dm 755 $srcdir/k3s-${pkgver}-${CARCH} $pkgdir/usr/bin/k3s

  install -dm 755 $pkgdir/usr/lib/systemd/system
  install -dm 755 $pkgdir/etc/systemd/system
  install -dm 755 $pkgdir/etc/ufw/applications.d

  install -m 644 $srcdir/k3s-agent.service $pkgdir/usr/lib/systemd/system/k3s-agent.service
  install -m 400 $srcdir/k3s-agent.service.env $pkgdir/etc/systemd/system/k3s-agent.service.env
  install -m 644 $srcdir/ufw-k3s $pkgdir/etc/ufw/applications.d/ufw-k3s
  
  backup=("etc/systemd/system/k3s-agent.service.env")

}

