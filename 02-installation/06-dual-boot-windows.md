# Dual Boot with Windows

---

## Table of Contents

- [Prepare Windows](#prepare-windows)
- [Start the PikaOS Installer](#start-the-pikaos-installer)
  - [Required BIOS Settings](#required-bios-settings)
- [Partition the Disk](#partition-the-disk)
  - [EFI System Partition](#efi-system-partition)
  - [Boot partition](#boot-partition)
  - [Root partition](#root-partition)
  - [Home partition (optional)](#home-partition-optional)
- [Install PikaOS](#install-pikaos)
- [Post-Installation Setup](#post-installation-setup)
  - [Update Your System](#update-your-system)
  - [Install Gaming Tools (Optional)](#install-gaming-tools-optional)
  - [Set Up Secure Boot (Optional)](#set-up-secure-boot-optional)
  - [Configure Your Display](#configure-your-display)
- [Dual-Boot Tips](#dual-boot-tips)
  - [Boot Order](#boot-order)
  - [Updating Windows](#updating-windows)
  - [File Sharing Between Windows and Linux](#file-sharing-between-windows-and-linux)
- [Related Guides](#related-guides)

---

> ⚠️ **Before you start:** Partitioning your disk carries a risk of data loss. **Back up your important files before proceeding.**

---

## Prepare Windows

1. Open the **Windows Disk Partition Manager** (search for "Create and format hard disk partitions" in the Start menu).
2. **Right-click and shrink your C: volume**

   Free up space for PikaOS. Decide how much space you want to dedicate to PikaOS and shrink the volume by that amount.

_In the example below we shrunk the `C:` drive 50GB for PikaOS and is now an Unallocated partition_
3. Close the partition manager and **shut down Windows**.
4. Boot into your **PikaOS live USB/medium**.

---

## Start the PikaOS Installer

### Required BIOS Settings

Before installing, make sure your `BIOS`/`UEFI` is configured correctly:

| Setting | Value |
| :--- | :--- |
| Secure Boot | **Disabled** for best compatibility with Windows games that need it, or **Enabled** if you plan to use [PikaOS Secure Boot](../07-guides/04-secure-boot.md) later (Windows will still boot fine) |
| `CSM` (Compatibility Support Module) | **Disabled** |
| Boot Mode | `UEFI` (must be enabled) |

> 🔒 **Note about Secure Boot:** If you enable Secure Boot in your firmware, you can later set it up on PikaOS using the [pika-secureboot](../07-guides/04-secure-boot.md) package. This allows Linux gaming and anti-cheat systems to work properly while keeping Windows games secure.

Once set, boot into your PikaOS live medium.

1. From the live desktop, select **Install Distro to System**.
2. Choose your **language**, **keyboard layout**, and **timezone**.
3. When asked how to partition the drive, select **Manually Partition the Drive**.
4. Click **Open Disk Partitioning Utility** in the bottom-left corner.

---

## Partition the Disk

In the Disk Partitioner, right-click your **free space** (the space you freed up from Windows) and select **New** to create each of the following partitions, in order:

### EFI System Partition

- Size: `512 MiB`
- Filesystem: `EFI System Partition`

### Boot partition

- Size: `1024 MiB` (1 GB)
- Filesystem: `ext4`

### Root partition

- Size: remaining free space (or leave some free space aside if you plan to add a separate Home partition)
- Filesystem: `ext4`

### Home partition (optional)

- Size: e.g., `50 GB` or less (if you want a separate home partition)
- Filesystem: `ext4`

---

## Install PikaOS

Click **Apply**. The installer will write files and install the bootloader.

When complete, reboot into your new system!

---

## Post-Installation Setup

After booting into PikaOS for the first time, follow these steps:

### Update Your System

```bash
pikman upgrade
```

### Install Gaming Tools (Optional)

If you want to game on Linux, install our gaming utilities:

```bash
pikman i pika-gameutils-meta
```

This installs `Steam`, `ProtonPlus`, `Gamescope`, `MangoHud` and more.

### Set Up Secure Boot (Optional)

If you enabled Secure Boot in your firmware, set it up on PikaOS:

```bash
sudo `pika-secureboot` enable
```

Then follow the [`pika-secureboot` Setup Guide](../07-guides/04-secure-boot.md) to complete enrollment.

### Configure Your Display

Run `pikman` and navigate to **Graphics** → **Display Server** to choose between `X11` or `Wayland`.

---

## Dual-Boot Tips

### Boot Order

Make sure PikaOS appears in your boot menu (`rEFInd` handles this by default). You should see entries for:

- Windows Boot Manager
- PikaOS (your main bootloader)
- PikaOS `Secure Boot` (if you enabled it)

### Updating Windows

When Windows updates, the system partition may shrink. Monitor its size and adjust if needed.

### File Sharing Between Windows and Linux

Mount your Windows partition in PikaOS:

```bash
sudo mkdir -p /mnt/windows
sudo mount -t `ntfs-3g` /dev/sdX1 /mnt/windows
# Replace /dev/sdX1 with your actual Windows partition
```

You can add this to `/etc/fstab` for auto-mount at boot.

---

## Related Guides

* [**BIOS Checklist**](../01-getting-started/03-bios-checklist.md) — Configure BIOS settings before installation
* [**Booting the Installer**](03-booting-the-installer.md) — Boot modes, BIOS settings, troubleshooting boot issues
* [**Guided Installation**](04-guided-install.md) — Automated partitioning with advanced filesystem options
* [**Post-Install Setup**](05-post-install-setup.md) — Essential initial configuration steps after installation completes
* [**Secure Boot Setup**](../07-guides/04-secure-boot.md) — Enable Secure Boot for enhanced security (optional)