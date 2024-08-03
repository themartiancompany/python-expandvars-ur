# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com># Maintainer:

_py='python'
_pkg=expandvars
pkgname="${_py}-${_pkg}"
pkgver=0.12.0
pkgrel=2
pkgdesc='Expand system variables Unix style'
arch=(
  any
)
_http="https://github.com"
_ns='sayanarijit'
url="${_http}/${_ns}/${_pkg}"
license=(
  BSD
)
depends=(
  "${_py}"
)
makedepends=(
  "${_py}-build"
  "${_py}-hatchling"
  "${_py}-installer"
)
checkdepends=(
  "${_py}-pytest"
)
source=(
  "${url}/archive/v${pkgver}/${_pkg}-${pkgver}.tar.gz"
)
sha256sums=(
  'dea375871e614bf2d2e5568f96d1101ab42985559cf48c0428d3591b5b59024c'
)

build() {
  cd "${_pkg}-${pkgver}"
  "${_py}" \
    -m build \
    --wheel \
    --no-isolation
}

check() {
  cd \
    "${_pkg}-${pkgver}"
  pytest \
    -v
}

package() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      installer \
    --destdir="${pkgdir}" \
    dist/*.whl
  install \
    -Dm644 \
    LICENSE \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}"
}

# vim: ft=sh syn=sh et
