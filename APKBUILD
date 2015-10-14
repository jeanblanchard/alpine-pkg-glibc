# Maintainer: Glider Labs <team@gliderlabs.com>

pkgname="glibc"
pkgver="2.22"
pkgrel="3"
pkgdesc="GNU C Library compatibility layer"
arch="x86_64"
url="https://github.com/gliderlabs/alpine-glibc"
license="GPL"
source="http://mirrors.kernel.org/archlinux/core/os/x86_64/glibc-${pkgver}-${pkgrel}-${arch}.pkg.tar.xz
ld.so.conf"
subpackages="$pkgname-bin"
triggers="$pkgname-bin.trigger=/usr/glibc/usr/lib"

package() {
  mkdir -p "$pkgdir"/usr/glibc
  mkdir "$pkgdir"/etc
  mkdir "$pkgdir"/lib64
  cp -a "$srcdir"/usr "$pkgdir"/usr/glibc/usr
  rm -rf "$pkgdir"/usr/glibc/usr/lib/systemd \
    "$pkgdir"/usr/glibc/usr/lib/gconv \
    "$pkgdir"/usr/glibc/usr/lib/locale \
    "$pkgdir"/usr/glibc/usr/lib/tmpfiles.d \
    "$pkgdir"/usr/glibc/usr/lib/getconf \
    "$pkgdir"/usr/glibc/usr/lib/audit \
    "$pkgdir"/usr/glibc/usr/lib/*.a \
    "$pkgdir"/usr/glibc/usr/bin/* \
    "$pkgdir"/usr/glibc/usr/include \
    "$pkgdir"/usr/glibc/usr/share
  "$srcdir"/usr/bin/ldconfig -r "$pkgdir" -C /etc/ld.so.cache /usr/glibc/usr/lib
  ln -s /usr/glibc/usr/lib/ld-linux-x86-64.so.2 ${pkgdir}/lib64/ld-linux-x86-64.so.2
}

bin() {
  mkdir -p "$subpkgdir"/usr/glibc/usr/bin \
    "$subpkgdir"/etc
  cp -a "$srcdir"/usr/bin/* "$subpkgdir"/usr/glibc/usr/bin/
  cp -La "$srcdir"/ld.so.conf "$subpkgdir"/etc/
}

md5sums="2f403116022721e2b61272e579b333b7  glibc-2.22-3-x86_64.pkg.tar.xz
fda27293b95f89c7a61a0d379d1c3bde  ld.so.conf"
