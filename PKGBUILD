#!/bin/bash

# Adapted from the original PKGBUILD by Andrew Steinke <rkcf@rkcf.me> and Joshua Leahy <jleahy@gmail.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# [ToDo]: Add files: User documentation
# [ToDo]: Add files: Tooling
# [FixMe]: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/python-freetype-py/discussions>

_prefix=python
_relname=freetype-py

pkgname=${_prefix}-${_relname}
pkgver=2.2.0
pkgrel=3
pkgdesc="FreeType Python bindings"
arch=("any")
url="https://github.com/rougier/freetype-py/"
license=(
  "BSD"
)
depends=(
  "python"
  "freetype2"
)
makedepends=(
  "python-setuptools"
  "python-setuptools-scm")
source=(
  "https://files.pythonhosted.org/packages/source/f/${_relname}/${_relname}-$pkgver.zip"
)
sha512sums=(
  "d8bfd785b488dfe5cf06a19d2f4f6cd8c77dbd3ba6de3aa250fb7c22fe75087e1ef2b8fbff5ca40c17d671ee2f155bb74619a26c9c87fefd75d6e5e13ba259eb"
)

build() {

  cd "$srcdir/${_relname}-$pkgver"

  python setup.py build
}

package() {

  cd "$srcdir/${_relname}-$pkgver"

  python setup.py install --root="$pkgdir/" --skip-build --optimize=1

  install -Dm644 "LICENSE.txt" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
