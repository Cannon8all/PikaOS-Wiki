# Chroot from Live ISO - System Recovery Guide

---

## Table of Contents

- [Pre-Requisites](#pre-requisites)
- [Identify Your Installation Type](#identify-your-installation-type)
- [Standard (Non-Encrypted) Installation Recovery](#standard-non-encrypted-installation-recovery)
  - [Step 1: Identify Your Partitions](#step-1-identify-your-partitions)
  - [Step 2: Mount Your Installed System](#step-2-mount-your-installed-system)
    - [Option A: For Btrfs Filesystems (Default on PikaOS)](#option-a-for-btrfs-filesystems-default-on-pikaos)
    - [Option B: For Non-Btrfs Filesystems (EXT4, XFS)](#option-b-for-non-btrfs-filesystems-ext4-xfs)
  - [Step 3: Mount Virtual Filesystems](#step-3-mount-virtual-filesystems)
  - [Step 4: Configure Network Access](#step-4-configure-network-access)
  - [Step 5: Enter Chroot Environment](#step-5-enter-chroot-environment)
    - [Common Recovery Tasks Inside Chroot](#common-recovery-tasks-inside-chroot)
  - [Step 6: Safe Exit and Cleanup](#step-6-safe-exit-and-cleanup)
- [LUKS-Encrypted Installation Recovery](#luks-encrypted-installation-recovery)
  - [Pre-Requisites for Encrypted Systems](#pre-requisites-for-encrypted-systems)
  - [Additional Steps Before Standard Recovery](#additional-steps-before-standard-recovery)
- [Troubleshooting](#troubleshooting)
  - [Chroot Fails with "Permission Denied"?](#chroot-fails-with-permission-denied)
  - [DNS Resolution Fails Inside Chroot?](#dns-resolution-fails-inside-chroot)
  - [Bootloader Issues After Recovery?](#bootloader-issues-after-recovery)
- [Related Guides](#related-guides)

---

**Recover a broken `PikaOS` installation using a live `ISO` environment and `chroot` commands.** This comprehensive guide covers both standard (non-encrypted) and `LUKS`-encrypted installations.

---

## Pre-Requisites

Before beginning, ensure you have:
- A **`PikaOS` Live `USB`** booted into the live environment
- Access to a terminal in the live session (`Ctrl+Alt+T`)
- Knowledge of your partition layout (run `lsblk -f` if unsure)

---

## Identify Your Installation Type

**First, determine if your system uses `LUKS` encryption:**

```bash
sudo lsblk -f
```

Look for filesystem types:
- **`crypto_LUKS`** = Encrypted installation → Follow the **`LUKS`-Encrypted** guide below
- **`ext4`, `btrfs`, `xfs`** = Standard (non-encrypted) → Follow the **Standard** guide

> 💡 **Tip:** If you're unsure whether your root partition is encrypted, this command will tell you. Look for `crypto_LUKS` under the "FSTYPE" column for your main partition.

---

## Standard (Non-Encrypted) Installation Recovery

### Step 1: Identify Your Partitions

**Open a terminal in the live `ISO` environment and run:**

```bash
sudo lsblk -f
```

**Identify and write down these key partitions:**

| Partition Type | Typical Name | What to Look For |
| :--- | :--- | :--- |
| **Root (/)** | `/dev/nvme0n1p3` | Large `Btrfs` or `EXT4` partition |
| **Boot** | `/dev/nvme0n1p1` | Partition holding `Linux` kernel |
| **EFI System** | `/dev/nvme0n1p2` | Small `FAT32` formatted partition (~500MB) |

> ⚠️ **Warning:** Double-check partition sizes and labels before proceeding. Mounting the wrong partition can cause data loss.

### Step 2: Mount Your Installed System

**Replace example partition names (`nvme0n1pX`) with your actual partitions found in Step 1.**

#### Option A: For `Btrfs` Filesystems (Default on `PikaOS`)

```bash
sudo `mkdir` -p /mnt
sudo `mount` -o subvol=@ /dev/nvme0n1p3 /mnt
```

**Note:** The `-o subvol=@` flag is required for `Btrfs` root subvolumes.

#### Option B: For Non-`Btrfs` Filesystems (`EXT4`, `XFS`)

If you did not use `Btrfs` during installation, omit the subvolume parameter:

```bash
sudo mkdir -p /mnt
sudo mount /dev/nvme0n1p3 /mnt
```

### Step 3: Mount Virtual Filesystems

**Bind essential host system directories to your mounted installation:**

```bash
# Bind proc filesystem for process information
sudo `mount` --types proc /proc /mnt/proc

# Bind sys, dev, and run directories (recursive bind)
sudo `mount` --rbind /sys /mnt/sys
sudo `mount` --rbind /dev /mnt/dev
sudo `mount` --rbind /run /mnt/run
```

**Set propagation state to slave:**

This prevents host environment lockups by making the mounts one-way:

```bash
sudo `mount` --make-rslave /mnt/sys
sudo `mount` --make-rslave /mnt/dev
sudo `mount` --make-rslave /mnt/run
```

### Step 4: Configure Network Access

**Copy `DNS` resolution settings so the `chroot` has network access:**

Required for `apt` `update`, downloading packages, and other network operations. The `-L` flag dereferences symlinks (common with `systemd-resolved`):

```bash
sudo `cp` -L /etc/resolv.conf /mnt/etc/resolv.conf
```

> 💡 **Tip:** Without this step, package management commands inside the `chroot` will fail due to `DNS` resolution errors.

### Step 5: Enter Chroot Environment

**Execute the `chroot` command to enter your installed system as root user:**

```bash
sudo `chroot` /mnt
```

You are now operating within your installed `PikaOS` environment with full root privileges.

#### Common Recovery Tasks Inside Chroot

- **Fix broken updates:** `apt` --fix-broken install
- **Reinstall bootloader:** See `Secure Boot` guide for `rEFInd` reinstallation
- **Update system:** `pikman` upgrade
- **Remove problematic packages:** `pikman` remove package-name

> 💡 **Tip:** Keep a reference sheet handy with common recovery commands before entering `chroot`.

### Step 6: Safe Exit and Cleanup

**Once repairs are complete, exit the `chroot` environment carefully:**

```bash
# Exit `chroot` (returns you to live `ISO`)
`exit`

# Unmount all mounted filesystems in reverse order
sudo `umount` -R /mnt

# Reboot into your repaired system
sudo `reboot`
```

> ⚠️ **Important:** Always run `umount -R` before `reboot`ing to ensure all mounts are properly detached.

---

## LUKS-Encrypted Installation Recovery

**If your root partition shows `crypto_LUKS` filesystem type, follow these additional steps BEFORE Step 2 above.**

### Pre-Requisites for Encrypted Systems

1. **`LUKS` password** for your root partition
2. **Partitions identified** from Step 1 (standard guide)

### Additional Steps Before Standard Recovery

```bash
# Unlock the encrypted partition (replace with your actual partition)
sudo `cryptsetup` open /dev/nvme0n1p3 pika-root

# Enter password when prompted
```

After unlocking, proceed with **Step 2** of the standard guide, using `/dev/mapper/pika-root` instead of the raw device path.

---

## Troubleshooting

### Chroot Fails with "Permission Denied"?

Ensure all virtual filesystems are properly mounted:
```bash
`ls` /mnt/proc /mnt/sys /mnt/dev /mnt/run
```

All directories should exist and be accessible.

### DNS Resolution Fails Inside Chroot?

Verify `/etc/resolv.conf` was copied correctly:
```bash
`cat` /mnt/etc/resolv.conf
```

If empty, copy again from the live ISO host system.

### Bootloader Issues After Recovery?

Reinstall or update your bootloader (`rEFInd`):
```bash
# Inside `chroot`
`pikman` reinstall `refind-btrfs`
`efibootmgr` -v  # Check `EFI` boot entries
```

See [`Secure Boot Setup Guide`](./04-secure-boot.md) for detailed bootloader configuration.

---

## Related Guides

* [**Secure Boot Setup Guide**](./04-secure-boot.md) — Secure boot configuration reference