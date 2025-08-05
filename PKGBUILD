# Maintainer: Panda <panda@bredos.org

pkgname=bredos-dracut
pkgver=1.0.0
pkgrel=1
pkgdesc="Dracut configuration for BredOS"
arch=('any')
url="https://github.com/BredOS/bredos-dracut"
license=('GPL-3.0')
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
  'tpm2-tools'
  'util-linux'
  'dracut'
)

provides=('initramfs')
backup=( 'etc/bredos-dracut.conf')
source=(
  "dracut-rebuild"
  "dracut-install"
  "dracut-remove"
  "90-dracut-install.hook"
  "60-dracut-remove.hook"
  "bredos-dracut.conf"
  "snapshot-overlay.sh"
  "module-setup.sh")

md5sums=('384bc7adc6676bca16c253d4f8733a9e'
         'fce3afd1af44c77c240d2b780b102779'
         'ca9090e658ffef409c53bf1a8069d4c6'
         '7d90a4cacd95f060a61f006b5edb6b9a'
         '4b26a0fe783a440d64985792e43272c3'
         'c74caf995580c863eedd88021166a745'
         'ab4a096b84dac5ab56e3d320f20ce88d'
         'c3be5d4fdee8cd4c3eff510a97f9641a')


package() {
  install -Dm644 "${srcdir}/90-dracut-install.hook" "${pkgdir}/usr/share/libalpm/hooks/90-dracut-install.hook"
  install -Dm644 "${srcdir}/60-dracut-remove.hook"  "${pkgdir}/usr/share/libalpm/hooks/60-dracut-remove.hook"
  install -Dm755 "${srcdir}/dracut-install"         "${pkgdir}/usr/share/libalpm/scripts/dracut-install"
  install -Dm755 "${srcdir}/dracut-remove"          "${pkgdir}/usr/share/libalpm/scripts/dracut-remove"
  install -Dm755 "${srcdir}/dracut-rebuild"         "${pkgdir}/usr/bin/dracut-rebuild"
  install -Dm644 "${srcdir}/bredos-dracut.conf"     "${pkgdir}/etc/bredos-dracut.conf"
  install -Dm755 "${srcdir}/snapshot-overlay.sh"    "${pkgdir}/usr/lib/dracut/modules.d/91btrfs-snapshot-overlay/snapshot-overlay.sh"
  install -Dm755 "${srcdir}/module-setup.sh"        "${pkgdir}/usr/lib/dracut/modules.d/91btrfs-snapshot-overlay/module-setup.sh"
  # ln -sf /dev/null /etc/pacman.d/hooks/90-mkinitcpio-install.hook
  # ln -sf /dev/null /etc/pacman.d/hooks/60-mkinitcpio-remove.hook
  #Disable the mkinitcpio hooks
  mkdir -p "${pkgdir}/etc/pacman.d/hooks"
  ln -sf /dev/null "${pkgdir}/etc/pacman.d/hooks/90-mkinitcpio-install.hook"
  ln -sf /dev/null "${pkgdir}/etc/pacman.d/hooks/60-mkinitcpio-remove.hook"
}
