pkgname=ollama
pkgver=0.0.13
pkgrel=1
pkgdesc='Get up and running with Llama 2 and other large language models locally'
arch=('x86_64')
url="https://github.com/jmorganca/ollama"
license=('MIT')
makedepends=('go')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/jmorganca/ollama/archive/v${pkgver}.tar.gz")
sha256sums=('b0c0e8bc237525032db26a8837f943e4a647ebc4f6a6a1655fd0e7dbda300326')

build() {
  cd "$pkgname-$pkgver"
  export CGO_CPPFLAGS="${CPPFLAGS}"
  export CGO_CFLAGS="${CFLAGS}"
  export CGO_CXXFLAGS="${CXXFLAGS}"
  export CGO_LDFLAGS="${LDFLAGS}"
  export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -mod=readonly -modcacherw"
  go build .
}

check() {
  cd "$pkgname-$pkgver"
  go test .
}

package() {
  cd "$pkgname-$pkgver"
  install -Dm755 $pkgname "$pkgdir"/usr/bin/$pkgname
}
