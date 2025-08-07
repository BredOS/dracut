# Maintainer: Giancarlo Razzolini <grazzolini@archlinux.org>
# Maintainer: Frederik Schwan <freswa@archlinux.org>
pkgname=dracut
pkgver=108
pkgrel=1
pkgdesc="An event driven initramfs infrastructure, BredOS version"
arch=('aarch64')
url="https://github.com/dracut-ng/dracut-ng"
license=('GPL-2.0-or-later')
depends=(
  'bash'
  'coreutils'
  'cpio'
  'filesystem'
  'findutils'
  'gawk'
  'grep'
  'kmod'
  'pkgconf'
  'procps-ng'
  'sed'
  'systemd'
  'util-linux'
)
makedepends=(
  'asciidoctor'
  'bash-completion'
  'git'
  'rust'
)
conflicts=('bredos-dracut')
replaces=('bredos-dracut')
optdepends=(
  'binutils: --uefi option support'
  'biosdevname: BIOS network device renaming'
  'bluez: bluetooth (keyboard)'
  'btrfs-progs: scan for Btrfs on block devices'
  'busybox: allows use of busybox (on your own risk)'
  'bzip2: bzip2 compression'
  'cifs-utils: support CIFS'
  'connman: support for connman networking'
  'cryptsetup: support for encrypted with LUKS filesystems'
  'dash: allows use of dash (on your own risk)'
  'dbus: dbus-daemon dracut module'
  'dbus-broker: dbus-broker dracut module'
  'dhclient: legacy networking support'
  'dmraid: dmraid dracut module support'
  'e2fsprogs: ext2/3/4 filesystem support'
  'elfutils: strip binaries to reduce initramfs size'
  'erofs-utils: support for building an erofs initramfs'
  'f2fs-tools: fsfs filesystem support'
  'fuse3: live on NTFS (dmsquash-live-ntfs module)'
  'gnupg: gpg for crypto operations and smartcards'
  'gzip: gzip compression'
  'iproute2: legacy networking support'
  'iputils: networking support'
  'jq: NVMe-oF support (nvmf module)'
  'lvm2: support Logical Volume Manager'
  'lzop: lzop compression'
  'mdadm: support MD devices, also known as software RAID devices'
  'memstrack: memstrack module support'
  'multipath-tools: multipath dracut module support'
  'nbd: support network block devices'
  'ndctl: NVDIMM support'
  'networkmanager: networkmanager support'
  'nfs-utils: support NFS'
  'ntfs-3g: live on NTFS (dmsquash-live-ntfs module)'
  'nvme-cli: NVMe-oF support (nvmf module)'
  'open-iscsi: support iSCSI (iscsi module)'
  'openssh: install ssh and scp along with config files and specified keys (ssh-client module)'
  'pigz: faster gzip compression'
  'plymouth: plymouth boot splash'
  'qrencode: systemd-bsod'
  'rng-tools: enable rngd service to help generating entropy early during boot'
  'rsyslog: enable logging with rsyslog'
  'sbsigntools: uefi_secureboot_cert/key configuration option support'
  'systemd-ukify: Unified Kernel Image'
  'squashfs-tools: support for building a squashed initramfs'
  'tar: live tar image'
  'tpm2-tools: tpm2 support for e.g. LUKS'
  'xz: xz compression'
)
provides=('initramfs')
backup=('etc/dracut.conf' 'etc/bredos-dracut.conf')
source=(
  "${pkgname}-${pkgver}::git+${url}#tag=${pkgver}"
  90-dracut-install.hook
  60-dracut-remove.hook
  dracut-install
  dracut-remove
  dracut-rebuild
  bredos-dracut.conf
  snapshot-overlay.sh
  module-setup.sh
)
sha512sums=('c9ffe67819c704d225efca3617b0dec79359ab049f826f5545d5ed5548943633f67e5c57831ce4fde1a294139d3e40d7df8f6b5a616415a8293fede1faba88a1'
            'a560fba9fdb66c733e15ff299676747f94a98a6da19b1d01293bb01d7e4a1b227e34c0f6c37e2e6924d1e42c028b0006b2b7a6cb8a5797777c6538fd0923356f'
            '5f8f6f04081061d36cd331737b40a8f523319f0d05d92308c0967de97266c27d3dd901da49ce0850f12c2cd95e5eb19ba6219b5d8a1d075c010420be1900f803'
            'fc5b59e830ca3061623ab76fa9d493edd096384c3d8b72666f862a6e0f1ae56423edbc63c1b7e9c0ea45f77df71aceaf4985338f4de8002db75d04afc9d2893f'
            'ad7406ef9fec8d3dbf008a533ce38b2f98a374cd3f5a2bbee6006f86469c2e51d074d623f9824da27282a5884ca1baa8354b2a7a82bb6e3df7456147293e695f'
            '8a4c9ac056bee6e7e22057cbf7179a32759767694a955372f68d43b26be62e9e8381c6264fc4884c4b04e39ffd6c1a2cc0d7e947b5796b4d89278455f3843cb9'
            'f70ba8247bfa98792250c36b4b860ab554edeed0319beac5260f967aa4bf24510ba8ac3977694cf8a8d26d4bab10d2350b138fcaf6cf76c7c832dbd56bec5c77'
            'ee103a605f1378dd7077fa33b710ba41ff7bd72befc0e211d9ccfe8ca5db74173bbd0566ec2929cd6bbafa4c2c287bd88a7b544edf0bbeca56181ae4382def09'
            '461231a756b6bc250fb973a5b4b6fbc0b2d6f8dae0dbc89a37bab17745dcfe38d9ae6cfe58bd4b9c4661e5f0024577ad9e4aa1d3c16169e7a83744da4b9068a5')
b2sums=('0188ecf5d3c7bc182dd30df570ce41b1cd20b5957ac056edfa6968ee5885298f046385bdbc63f36fa5ccc11aa66cb801e9043c9b6c570d3ca0448d5f35d07699'
        '5e0e702553060dbc94a378a1b3b7caa52590a33f33d78767a4c3ef0a5360d11520084e91f59b941a62bea8abfcd017cd64132c5f3d42d93319683283a22e0875'
        'a3bc75e55af379ddd3fee1dd7c6855fcb42366f42d9e10c1725b8e38f81c3eee0a4131badcf6ba2c4addf78aae4084528407af38295ab2b7e62ab16e3fe0b599'
        '586aea4d37fd341ad72a0168c60042207e8778b53094bbe7a17e399788ef97d8d48ac285abb37d73d546a43bd50af81e09a099259454bfcadaedb389bea3ccd5'
        '5113d170e6a4ae50f6797f20d8929ddeb0cd4a398fe0ede0aea0114d28300ae8da1586c4b26f7345b91162394046ea76fbe88970039315db20ef80b9659cd6de'
        '04ebb800b852a35b15b8288f61cf78aeccc3bdd12e8b9d7e33cd0bb85bc662cc803f2c6fa11fa5deecd2f77295272eb12bfa29803c4adb224daf3694d60ed7d8'
        'd3279ddcc2bf6a5614f24b2f15a494879ebeb44fec462822d20e69472853d3cac77af15e0fd82fe6e8fa4e030c196f3a87908d7967854345be3a56869ecd80ab'
        '9e7129ecffa900e55c4c3f16b473b3448b788e8b7c498213529aeaf67b7a2f1ba1899be9f66a9fb5487d8c1bec52aebe66a8363c27ff0b999a6c2ab97f9b4b08'
        '373a60e5d9d0973a6d343a290da0632cce2cf86346b08bae553d3148f40472d43f8348106abeaab7b4bbca4c7165c487e863b9a9baf6c2b335351fee96bdfdf1')

build() {
  cd ${pkgname}-${pkgver}

  ./configure  \
    --sysconfdir=/etc

  make
}

package() {
  cd ${pkgname}-${pkgver}

  DESTDIR="$pkgdir" make install

  # pacman hooks
  install -Dm644 "${srcdir}/90-dracut-install.hook" "${pkgdir}/usr/share/libalpm/hooks/90-dracut-install.hook"
  install -Dm644 "${srcdir}/60-dracut-remove.hook"  "${pkgdir}/usr/share/libalpm/hooks/60-dracut-remove.hook"
  install -Dm755 "${srcdir}/dracut-install"         "${pkgdir}/usr/share/libalpm/scripts/dracut-install"
  install -Dm755 "${srcdir}/dracut-remove"          "${pkgdir}/usr/share/libalpm/scripts/dracut-remove"
  install -Dm755 "${srcdir}/dracut-rebuild"         "${pkgdir}/usr/bin/dracut-rebuild"
  install -Dm644 "${srcdir}/bredos-dracut.conf"     "${pkgdir}/etc/bredos-dracut.conf"
  install -Dm755 "${srcdir}/snapshot-overlay.sh"    "${pkgdir}/usr/lib/dracut/modules.d/91btrfs-snapshot-overlay/snapshot-overlay.sh"
  install -Dm755 "${srcdir}/module-setup.sh"        "${pkgdir}/usr/lib/dracut/modules.d/91btrfs-snapshot-overlay/module-setup.sh"

  #Disable the mkinitcpio hooks
  mkdir -p "${pkgdir}/etc/pacman.d/hooks"
  ln -sf /dev/null "${pkgdir}/etc/pacman.d/hooks/90-mkinitcpio-install.hook"
  ln -sf /dev/null "${pkgdir}/etc/pacman.d/hooks/60-mkinitcpio-remove.hook"
}
