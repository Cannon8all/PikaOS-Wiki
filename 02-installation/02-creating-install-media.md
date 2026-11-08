# PikaOS Install Media Creation Guide

---

## Table of Contents

- [Why Verify the ISO?](#why-verify-the-iso)
- [Pre-flight Checklist](#pre-flight-checklist)
- [Verify ISO Integrity (Recommended)](#verify-iso-integrity-recommended)
- [Writing the ISO to USB Drive](#writing-the-iso-to-usb-drive)
- [Tool Comparison Table](#tool-comparison-table)
- [Troubleshooting Common Issues](#troubleshooting-common-issues)
- [Expected Write Times](#expected-write-times)
- [After Writing: Verify Bootability](#after-writing-verify-bootability)
- [USB Drive Requirements](#usb-drive-requirements)
- [Related Guides](#related-guides)
- [Quick Reference: Recommended Workflow](#quick-reference-recommended-workflow)

---

**Create bootable USB drives for PikaOS installation using your preferred tool.** This comprehensive guide covers ISO verification, multiple writing methods, and troubleshooting common issues encountered during media preparation.

---

## Why Verify the `ISO`?

**`ISO` integrity verification is critical** before creating install media:

- **File Integrity:** Confirms download completed without corruption
- **Authenticity:** Verifies official PikaOS image, not tampered
- **Reliability:** Prevents installation failures due to bad data

> 💡 **Tip:** Always verify the `ISO` checksum before writing to `USB`! A corrupted `ISO` will cause installation failures and wasted time.

---

## Pre-flight Checklist

**Before creating install media, ensure you have:**

| Item | Status | Notes |
| :--- | :---: | :--- |
| **Correct PikaOS edition downloaded** | ☐ | GNOME, KDE, Hyprland, Niri, or COSMIC |
| **`USB` drive ≥8GB capacity** | ☐ | `USB` 3.0+ recommended for speed |
| **BIOS Secure Boot disabled** | ☐ | Required for initial installation |
| **Important data backed up** | ☐ | `USB` will be completely erased |

> ⚠️ **Warning:** All data on the `USB` drive will be permanently erased during creation. Back up any important files first.

---

## Verify `ISO` Integrity (Recommended)

### Step 1: Get the Published `MD5` Checksum

**Procedure:**
1. Go to the [official PikaOS download page](https://pika-os.com/download)
2. Right-click your chosen download button
3. Select **Copy link address**
4. Open a new browser tab and paste URL
5. Change `.iso` extension to `.md5`
6. Press **Enter** — you'll see the checksum text

*Expected result:* A single line with 32-character hash string like `a1b2c3d4e5f6789012345678901234`

---

### Step 2: Generate Local MD5 Hash

**Open terminal and run:**
```bash
cd ~/Downloads
md5sum pikaos-gnome-2024.iso
```

*Expected output:*
```
a1b2c3d4e5f6789012345678901234  pikaos-gnome-2024.iso
```

---

### Step 3: Compare Checksums

| Result | Action Required |
| :---: | :--- |
| **✅ Match** | Download is authentic and complete — proceed to `USB` creation |
| **❌ Mismatch** | Delete file, re-download `ISO` from official source |

> ⚠️ **Warning:** Never install from an `ISO` with mismatched checksums. This indicates corruption or potential tampering. Do not proceed until you have a verified download.

---

## Writing the `ISO` to `USB` Drive

### Method 1: GNOME Disks (GUI - Recommended for Linux)

**Best for:** Beginners and GNOME desktop users

**Procedure:**
1. Open **Disks** application from your menu
2. Select your `USB` drive in the left panel
3. Click **⋮** menu → **Restore Disk Image...**
4. Browse to select your PikaOS `ISO` file
5. Click **Start Restoring**
6. Confirm when prompted

*Expected result:* Progress bar shows writing status, completion message appears when done.

> 💡 **Tip:** GNOME Disks automatically verifies the write after completion, providing extra assurance.

---

### Method 2: Balena Etcher (Cross-Platform)

**Best for:** Users on Windows, macOS, or Linux who prefer GUI tools

**Procedure:**
1. Download and install [Balena Etcher](https://www.balena.io/etcher/)
2. Launch Etcher application
3. Click **Flash from file** → Select your `ISO`
4. Click **Select target** → Choose `USB` drive
5. Click **Flash!** to begin writing

*Expected result:* Three progress bars show validation, flashing, and completion with success message.

> 💡 **Tip:** Balena Etcher automatically validates the write process, reducing user error.

---

### Method 3: dd Command (Terminal - Advanced)

**Best for:** Experienced users who prefer command-line tools or scripting automation

**Procedure:**
```bash
# Identify your USB device (look for size match)
lsblk

# Unmount the USB if mounted
sudo umount /dev/sdX1

# Write ISO to USB (replace X with correct letter, e.g., sdb)
sudo dd if=pikaos-gnome-2024.iso of=/dev/sdX bs=4M status=progress conv=fdatasync

# Eject safely after completion
sudo eject /dev/sdX
```

*Expected output:*
```
pikaos-gnome-2024.iso: 2.1 GB written in 3m 45s (6.2 MB/s)
dd: writing to '/dev/sdb': Broken pipe
```

> 💡 **Tip:** The `status=progress` flag shows real-time progress, and `conv=fdatasync` ensures data is fully written before completion.

**Critical warnings for dd method:**
- Double-check device name (`/dev/sdX`) — writing to wrong device can destroy data!
- Never run as root without necessity
- Have backups of important data on target system

---

### Method 4: Ventoy (Multi-Boot USB)

**Best for:** Users wanting multiple ISOs on one portable drive

**Procedure:**
1. Download [Ventoy](https://www.ventoy.net/en/download.html)
2. Install Ventoy to your `USB` drive (**this will erase all data!**)
3. Copy PikaOS `ISO` file(s) directly to the `USB`'s FAT32 partition
4. Boot from `USB` → Ventoy boot menu appears → Select PikaOS `ISO`

*Expected result:* Ventoy boot menu with all ISOs listed, select PikaOS to install.

> 💡 **Tip:** Ventoy is excellent for tech enthusiasts who maintain a multi-boot recovery drive with various Linux distributions.

---

## Tool Comparison Table

| Tool | Platform | Best For | Difficulty | Auto-Verify |
| :--- | :---: | :--- | :---: | :---: |
| **GNOME Disks** | Linux (GNOME) | Beginners, GNOME users | Easy | ✅ Yes |
| **Balena Etcher** | Windows/macOS/Linux | Cross-platform GUI | Easy | ✅ Yes |
| **dd command** | Linux/Unix | Advanced use, scripting | Medium | ❌ No |
| **Ventoy** | All platforms | Multi-boot USB setup | Medium | ⚠️ Partial |

> 💡 **Tip:** For first-time users, GNOME Disks or Balena Etcher provide the best balance of ease and reliability.

---

## Troubleshooting Common Issues

### Issue: "Device is busy" error with dd or Disks

**Cause:** `USB` partition is mounted and in use

**Solution:** Unmount the `USB` drive first
```bash
sudo umount /dev/sdX1
```
Replace `sdX1` with your actual partition (check with `lsblk`).

---

### Issue: Balena Etcher fails validation

**Cause:** `ISO` may be corrupted or Ventoy-formatted drive detected

**Solution:** 
1. Re-download `ISO` from official source
2. Verify `MD5` checksum first
3. Try different `USB` port or drive

---

### Issue: `USB` not detected after writing

**Possible causes:**
- Wrong `USB` port (try different one, prefer `USB` 2.0)
- Drive too slow for write speed
- `ISO` was corrupted during download

**Solution:** Verify `MD5` checksum, try slower write speed or different tool (Ventoy often works where others fail).

---

### Issue: "No bootable device found" after writing

**Cause:** BIOS/UEFI settings incorrect or `USB` not properly written

**Solutions:**
1. Ensure Secure Boot is disabled in firmware
2. Check boot order prioritizes `USB`
3. Try `UEFI` vs Legacy mode (or vice versa)
4. Re-write using different method

> 💡 **Tip:** MSI motherboards may require enabling `BOOTX64` Mode (`MSI` Compatibility Mode) in `UEFI` settings.

---

## Expected Write Times

**Write times vary based on USB speed and ISO size:**

| ISO Size | USB 2.0 | USB 3.0/3.1 | USB 3.2 Gen1 |
| :--- | :---: | :---: | :---: |
| **2 GB** | ~35 minutes | ~5 minutes | ~3 minutes |
| **4 GB** | ~70 minutes | ~10 minutes | ~6 minutes |
| **8 GB** | ~2.5 hours | ~20 minutes | ~12 minutes |

> 💡 **Tip:** Use a `USB` 3.0+ drive and port for fastest writing times! `USB` 3.0 drives are inexpensive and save significant time.

---

## After Writing: Verify Bootability

**Before installing, test that your USB boots correctly:**

1. Insert `USB` into target system
2. Reboot and access boot menu (typically `F12`, `Esc`, or `Del`)
3. Select `USB` drive from boot options
4. **Expected result:** PikaOS boot menu appears with bird logo

*If it doesn't boot:*
- Re-write the `ISO` using a different method
- Verify `MD5` checksum first
- Check BIOS/`UEFI` settings (Secure Boot disabled, `UEFI` mode)
- Try a different `USB` port or drive

---

## USB Drive Requirements

**Minimum specifications for reliable installation:**

| Requirement | Minimum | Recommended | Notes |
| :--- | :---: | :---: | :--- |
| **Capacity** | 8 GB | 16 GB+ | Larger drives allow multiple ISOs |
| **USB Version** | 2.0 | 3.0 or higher | Faster write times with USB 3.0+ |
| **Brand Quality** | Generic | SanDisk, Samsung, Kingston | Avoid cheap no-name brands |

> 💡 **Tip:** Reuse old USB drives for test installations, but always verify integrity before critical installs.

---

## Related Guides

* [**Booting the Installer**](03-booting-the-installer.md) — Boot modes, BIOS settings, troubleshooting boot issues
* [**Guided Installation**](04-guided-install.md) — Automated partitioning with advanced options
* [**Post-Install Setup**](05-post-install-setup.md) — Initial configuration after installation
* [**BIOS Checklist**](../01-getting-started/03-bios-checklist.md) — Configure BIOS settings before installation

---

## Quick Reference: Recommended Workflow

1. **Download ISO** from official PikaOS site
2. **Verify MD5 checksum** before proceeding
3. **Choose writing tool** based on your experience level
4. **Write to USB drive** (8GB+ recommended)
5. **Test bootability** on target system
6. **Configure BIOS/UEFI** settings as needed
7. **Begin installation** once boot menu appears

> 💡 **Tip:** Once your bootable USB is ready, you're almost there! The next step is configuring your BIOS settings properly. Check our [BIOS Checklist](../01-getting-started/03-bios-checklist.md) to ensure Secure Boot is disabled before proceeding with installation!
