# Maintainer: Giancarlo Razzolini <grazzolini@archlinux.org>
pkgname=dracut
pkgver=060
pkgrel=2
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
  'asciidoc'
  'bash-completion'
  'git'
)
optdepends=(
  'binutils: --uefi option support'
  'bluez: bluetooth (keyboard)'
  'btrfs-progs: scan for Btrfs on block devices'
  'busybox: allows use of busybox (on your own risk)'
  'bzip2: bzip2 compression'
  'cifs-utils: support CIFS'
  'connman: support for connman networking'
  'cryptsetup: support for encrypted with LUKS filesystems'
  'dash: allows use of dash (on your own risk)'
  'dhclient: legacy networking support'
  'dmraid: dmraid dracut module support'
  'e2fsprogs: ext2/3/4 filesystem support'
  'elfutils: strip binaries to reduce initramfs size'
  'f2fs-tools: fsfs filesystem support'
  'fuse3: live on NTFS (dmsquash-live-ntfs module)'
  'gzip: gzip compression'
  'iproute2: legacy networking support'
  'iputils: networking support'
  'lvm2: support Logical Volume Manager'
  'lzop: lzop compression'
  'mdadm: support MD devices, also known as software RAID devices'
  'multipath-tools: dmraid dracut module support'
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
  'rng-tools: enable rngd service to help generating entropy early during boot'
  'sbsigntools: uefi_secureboot_cert/key configuration option support'
  'squashfs-tools: support for building a squashed initramfs'
  'tar: live tar image'
  'tpm2-tools: tpm2 support for e.g. LUKS'
  'xz: xz compression'
)
provides=('initramfs')
backup=('etc/dracut.conf')
source=(
  "${pkgname}-${pkgver}::git+${url}#tag=${pkgver}"
  dracut-systemd-255-pcrphase.patch::https://github.com/dracut-ng/dracut-ng/commit/b63e90ab4e34b35ba0ce009992b0fc019eca3761.patch
  dracut-systemd-255-hibernate-resume.patch::https://github.com/dracutdevs/dracut/pull/2527/commits/a2fe89116db4b286fbf515f26bd1773b5e6ee8ad.patch
)
sha512sums=('8dbdd67d0b86555aac4c2f315c809861c82358d3899ecdf3008e6203b9f32eac2e8a969fe972e9ce63316aeb0d3242e0e997d21c24bee8666ef3d3e7ddda067e'
            '6b00c3d37440feb294219477f79edcbb074b69863e0234edbc7966df11cb6e7d51cf1ea3c086b3014748f6e96bbeab5e4f1916c3b14316e1b2a8aa1e4f4ee563'
            'bba154e13463fb759e1cfd5f461b2b4e786ad8c6f4cacacbd918e911efc7d5a5368300676d6e6d8e9b7b2f4333314886bb1e34daac9f0c73c1c441baf7918063')
b2sums=('41593a6205cf0a66ad49d903cf73e20b6a0b90628e185f93eb29d09df7d7dbcc342759901d204fb3d2c98ec6b8550ac14dbaef43c8243c0d9190b06a56a92a91'
        '863a685ab41ed9d891257c4b18e311e5d6849c8eb30ba489252b4d9cda462c4c6d50bfcc8edece891c34f012b6dd7120c1d3cc8cb08758ef6696d3b15c0f0d81'
        'bd8dc23e1dafa9a76b79af40be5267ee96934c08950b6eae70d5794a9f3038cb0cb7d54593463f42325ddae637cb6ddf21af52bd9fd6e639f7fdc7acc5abf21e')

prepare() {
  cd ${pkgname}-${pkgver}

  patch -Np1 < ../dracut-systemd-255-pcrphase.patch
  patch -Np1 < ../dracut-systemd-255-hibernate-resume.patch
}

build() {
  local prefix=/usr sysconfdir=/etc

  cd ${pkgname}-${pkgver}

  ./configure \
    --sysconfdir=${sysconfdir} \
    --prefix=${prefix} \
    --libdir=${prefix}/lib \
    --systemdsystemunitdir=${prefix}/lib/systemd/system \
    --bashcompletiondir=$(pkg-config --variable=completionsdir bash-completion)
  make
}

package() {
  cd ${pkgname}-${pkgver}

  DESTDIR="$pkgdir" make install
}
