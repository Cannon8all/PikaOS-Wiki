# PikaOS Installation Overview Guide

---

## Table of Contents

- [Phase 1: Before You Install — What You Need](#phase-1-before-you-install---what-you-need)
- [Phase 2: Installation Process](#phase-2-installation-process)
- [Phase 3: First Boot & Setup](#phase-3-first-boot-setup)
- [Quick Reference Summary](#quick-reference-summary)
- [Related Guides](#related-guides)

---

## Phase 1: Before You Install — What You Need

> ⚠️ **Before you begin:** Complete every item below. Skipping a step is the most common cause of installation failures.

---

### Required

| # | Item | Details |
|---|---|---|
| 1 | **A PikaOS ISO** | Choose your edition and GPU variant — see [Editions Guide](../01-getting-started/02-editions.md) |
| 2 | **USB drive (8 GB+)** | Will be erased — back up any data on it first |
| 3 | **A verified download** | Check the ISO checksum — see [Preparing USB and Booting](02-prepare-usb-and-boot.md#verify-iso-integrity-recommended) |
| 4 | **Correct BIOS/UEFI settings** | Secure Boot disabled, CSM disabled, UEFI-only, SATA set to AHCI — see [BIOS Checklist](../01-getting-started/03-bios-checklist.md) |
| 5 | **Backed-up personal files** | The installer erases the target drive |

---

## Phase 2: Installation Process

### Step 1: Write ISO to USB Drive

**Windows:**

- **[Rufus](https://rufus.ie)** — Fast, reliable, no installation required
- **[Balena Etcher](https://www.balena.io/etcher)** — Simple GUI, cross-platform

**Linux:**

- **GNOME Disks** — Pre-installed on GNOME desktops; use "Restore Disk Image" (the disk icon with an arrow)
- **[Fedora Media Writer](https://docs.fedoraproject.org/en-US/fedora-media-writer/)** — Also works for non-Fedora ISOs; simple and reliable

> ⚠️ **Warning:** Using dd incorrectly can erase your hard drive. If you're not comfortable with the command line, use one of the tools above instead.

---

### Step 2: Boot the Installer

**Access boot menu:**

- Restart computer and press boot key (F12, F10, Esc, or Del)
- Select USB drive from boot options
- Boot into PikaOS live environment

> 💡 **Tip:** If Secure Boot is enabled, you may need to disable it temporarily for the installer to boot.

---

### Step 3: Partition and Install

**Using the installer:**

1. Launch **Install PikaOS to Hard Drive**
2. Choose installation type (guided or manual partitioning)
3. Select target drive and partitions
4. Begin installation process

> 💡 **Tip:** See the [Guided Installation Guide](03-guided-install.md) for detailed step-by-step instructions.

---

## Phase 3: First Boot & Setup

### Step 1: Complete First-Boot Wizard

On first boot after installation, complete the setup wizard:

1. Create user account
2. Configure system settings
3. Choose desktop environment preferences

---

### Step 2: Run System Updates

After initial setup, update your system to get latest packages:

```bash
pikman upgrade
```

> 💡 **Tip:** Install updates before using the system for best compatibility and security.

---

## Related Guides

* [**BIOS Checklist**](../01-getting-started/03-bios-checklist.md) — Prepare your system before installation
* [**Preparing USB and Booting**](02-prepare-usb-and-boot.md) — Write ISO to USB, verify checksum, boot the installer
* [**Post-Install Setup**](04-post-install.md) — Configure your new system
