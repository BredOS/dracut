# Maintainer: Giancarlo Razzolini <grazzolini@archlinux.org>
# Maintainer: Frederik Schwan <freswa@archlinux.org>
pkgname=dracut
pkgver=108
pkgrel=1
pkgdesc="An event driven initramfs infrastructure"
arch=('x86_64')
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
backup=('etc/dracut.conf')
source=(
  "${pkgname}-${pkgver}::git+${url}#tag=${pkgver}"
  dracut-{install,remove}.script
  90-dracut-install.hook
  60-dracut-remove.hook
)
sha512sums=('c9ffe67819c704d225efca3617b0dec79359ab049f826f5545d5ed5548943633f67e5c57831ce4fde1a294139d3e40d7df8f6b5a616415a8293fede1faba88a1'
            '0f91f0d4378fd9f67f1fd05080aa013b65ce48661aad4ffc07e090dee88ee789daddfa85393c49e8fd5e2ea82bf00ac482fef71523198336750bef59508408d2'
            'ed249af85fd15b79299e99b9b587fe962158d803cc1365d903a6202331cc0befaa309e36d4922bd859824295cd023bd75f959f5ad783d230550f6ce371baac67'
            'a560fba9fdb66c733e15ff299676747f94a98a6da19b1d01293bb01d7e4a1b227e34c0f6c37e2e6924d1e42c028b0006b2b7a6cb8a5797777c6538fd0923356f'
            '5f8f6f04081061d36cd331737b40a8f523319f0d05d92308c0967de97266c27d3dd901da49ce0850f12c2cd95e5eb19ba6219b5d8a1d075c010420be1900f803')
b2sums=('0188ecf5d3c7bc182dd30df570ce41b1cd20b5957ac056edfa6968ee5885298f046385bdbc63f36fa5ccc11aa66cb801e9043c9b6c570d3ca0448d5f35d07699'
        '5468c20cd1d723509bf1d79dd5691d5e81eb19bc2e506c77eb8ee39b1b93ae195a34bb1e24a1db6a844b43999859491a3bf3c84dbef12b19a41d10a10ee8465c'
        '06e6ef68f1116d348ce4f11960a9b583af703b93ae0172c5d3d237dcdd4ca4614f2cb0f761ff12079b8c40f349e39d096ed404dee38732d4cc704e8af7ca23f1'
        '5e0e702553060dbc94a378a1b3b7caa52590a33f33d78767a4c3ef0a5360d11520084e91f59b941a62bea8abfcd017cd64132c5f3d42d93319683283a22e0875'
        'a3bc75e55af379ddd3fee1dd7c6855fcb42366f42d9e10c1725b8e38f81c3eee0a4131badcf6ba2c4addf78aae4084528407af38295ab2b7e62ab16e3fe0b599')

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
  install -Dm755 "${srcdir}"/dracut-install.script "${pkgdir}"/usr/share/libalpm/scripts/dracut-install
  install -Dm755 "${srcdir}"/dracut-remove.script "${pkgdir}"/usr/share/libalpm/scripts/dracut-remove
  install -Dm644 -t "${pkgdir}"/usr/share/libalpm/hooks "${srcdir}"/*.hook
}
