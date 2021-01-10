#!/bin/sh
# Maintainer: Johan Nilsson
# Contributor: Rokas Kupstys (Original creator)
_pkgbase=naga
pkgname=${_pkgbase}-dkms
pkgver=1
pkgrel=1
pkgdesc="Razer Naga keypad remap module (DKMS)"
arch=('i686' 'x86_64')
url="https://github.com/joppefan/naga-dkms"
license=('GPL2')
depends=('dkms')
conflicts=("${_pkgbase}")
install=${pkgname}.install
source=('naga.c'
        'dkms.conf'
        'naga-dkms.install'
        'Makefile'
)
sha256sums=('97002bcc8fdf69ee3c5efca0850ac8b3a6ffb0cad228c827036cc91af9894ff3'
            'bc05aa364ff818d1c7d06a0afd68793aae2c01997441b780aef81e304584ef76'
            '93b93b6e453a1f2b31a0db956d259a5d2142a75f930e01502c38c0fedbfe272b'
            'e49974880fe56036f35a3c5dd51d870cb74a0317a0aee8139156a0974c33ac13')

package() {
  cd "${srcdir}"

  local install_dir="${pkgdir}/usr/src/${_pkgbase}-${pkgver}"

  # Copy dkms.conf
  install -Dm644 dkms.conf "${install_dir}/dkms.conf"

  # Copy sources (including Makefile)
  cp -rL ./* "${install_dir}"

  # Set name and version
  sed -e "s/@_PKGBASE@/${_pkgbase}/" \
      -e "s/@PKGVER@/${pkgver}/" \
      -i "${install_dir}/dkms.conf"
}
