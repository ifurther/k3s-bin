# Maintainer: duxet <duxetlg@gmail.com>
<<<<<<< HEAD
pkgbase=k3s
pkgname=("$pkgbase-server" "$pkgbase-agent")
=======
pkgname=k3s-bin
>>>>>>> upstream/master
pkgver=1.20.4+k3s1
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
sha256sums_x86_64=('1c7b68b0b7d54f21a9c1727545a7db181668115f161a3986bc137261dd817e98')
sha256sums_armv7h=('6567e3773022bd1a44514ddfb4da74efd2ec6cbb6b30ea5f89e70c4590173763')
sha256sums_aarch64=('d84a07f1438352d26f9fbcf1c3e839d6523d3e1231030b7a9b2b639b8a7dfc30')




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

