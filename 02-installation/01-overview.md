# Installation overview

This page lists the steps to install PikaOS in order, with a link to the page that covers each one.

## 1. Choose and download an edition

Pick a desktop environment and download its ISO. Use the NVIDIA ISO for RTX cards and GTX 1650 or newer.

[Editions](../01-getting-started/02-editions.md)

## 2. Check your UEFI settings

Make sure Secure Boot and CSM are both disabled in your UEFI settings before continuing.

[BIOS checklist](../01-getting-started/04-bios-checklist.md)

## 3. Verify the ISO (optional)

Compare the MD5 checksum of your download with the published one. Never install an ISO where the checksums do not match.

[Creating install media](02-creating-install-media.md)

## 4. Write the ISO to a USB drive

Write the ISO with one of the listed tools (Linux, Windows, cross platform and Android methods), then boot from the USB device.

[Creating install media](02-creating-install-media.md)

## 5. Boot the installer

Wait for the bird logo, press Enter, then select Install Distro to System. MSI systems need BOOTX64 Mode (MSI Compatibility Mode).

[Booting the installer](03-booting-the-installer.md)

## 6. Partition the drive and install

- Automatic partitioning, with advanced options for filesystem, home directory separation, swap and boot options: [Guided install](04-guided-install.md)
- Dual boot alongside an existing Windows install, partitioning manually: [Dual boot with Windows](06-dual-boot-windows.md)
- Manual partitioning (planned)

## 7. First boot

Reboot, complete the first boot wizard, and you will be greeted by the Welcome app.

[Post-install setup](05-post-install-setup.md)
