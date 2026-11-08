# PikaOS Installation Overview Guide

---

## Table of Contents

- [Phase 1: Preparation (Before You Begin)](#phase-1-preparation-before-you-begin)
- [Phase 2: Installation Process](#phase-2-installation-process)
- [Phase 3: First Boot & Setup](#phase-3-first-boot-setup)
- [Quick Reference Summary](#quick-reference-summary)
- [Related Guides](#related-guides)

---


## Phase 1: Preparation (Before You Begin)

### Step 1: Choose and Download Edition

Select the PikaOS edition that matches your needs:

| Edition | Best For | Size | Notes |
| --- | :--- | :---: | --- |
| **Standard** | Most users, general use | ~3 GB | Balanced features and performance |
| **Gaming** | Gaming-focused systems | ~4 GB | Includes gaming tools and drivers |
| **Minimal** | Advanced users, minimal installs | ~1.5 GB | Empty desktop, install only what you need |

> 💡 **Tip:** Download from the official PikaOS website to ensure authenticity and avoid tampered `ISO`s.

---

### Step 2: Verify UEFI/BIOS Settings

Before installing, verify your firmware settings:

**Required settings:**
- **UEFI Mode:** Enable (not Legacy/`CSM`)
- **Secure Boot:** Can be enabled or disabled (PikaOS supports both)
- **Boot Mode:** `UEFI` only

**Recommended for best compatibility:**
| System Type | BIOS Setting | Notes |
| --- | :--- | --- |
| **Standard Desktops** | Secure Boot: Disabled initially | Enable after installation if desired |
| **Gaming Laptops** | May need to disable Fast Boot or Hybrid Graphics | Check manufacturer documentation |
| **AMD Ryzen** | Ensure SVM Mode is enabled for virtualization features | Improves performance in VMs |

> 💡 **Tip:** See the [BIOS Checklist Guide](../01-getting-started/03-bios-checklist.md) for detailed firmware configuration instructions.

---

### Step 3: Verify `ISO` Checksum (Optional)

Verify the downloaded `ISO` integrity to prevent installation failures from corrupted downloads:

**Why verify?**
- Ensures file wasn't corrupted during download
- Confirms `ISO` hasn't been tampered with
- Prevents installation failures due to bad data

**Verification commands:**
```bash
sha256sum pikaos-*.iso
# Compare output with official hash from download page
```

> 💡 **Tip:** Only proceed if checksum matches. Mismatched hashes indicate corrupted or tampered files.

---

## Phase 2: Installation Process

### Step 4: Write ISO to USB Drive

**Windows:**
- **[Rufus](https://rufus.ie)** — Fast, reliable, no installation required
- **[Balena Etcher](https://www.balena.io/etcher)** — Simple GUI, cross-platform

**Linux:**
- **GNOME Disks** — Pre-installed on GNOME desktops; use "Restore Disk Image" (the disk icon with an arrow)
- **[Fedora Media Writer](https://docs.fedoraproject.org/en-US/fedora-media-writer/)** — Also works for non-Fedora ISOs; simple and reliable

> ⚠️ **Warning:** Using `dd` incorrectly can erase your hard drive. If you're not comfortable with the command line, use one of the tools above instead.

---

### Step 5: Boot the Installer

**Access boot menu:**
- Restart computer and press boot key (F12, F10, Esc, or Del)
- Select USB drive from boot options
- Boot into PikaOS live environment

> 💡 **Tip:** If Secure Boot is enabled, you may need to disable it temporarily for the installer to boot.

---

### Step 6: Partition and Install

**Using the installer:**

1. Launch **Install PikaOS to Hard Drive**
2. Choose installation type (guided or manual partitioning)
3. Select target drive and partitions
4. Begin installation process

> 💡 **Tip:** See the [Guided Installation Guide](04-guided-install.md) for detailed step-by-step instructions.

---

## Phase 3: First Boot & Setup

### Step 7: Complete First-Boot Wizard

On first boot after installation, complete the setup wizard:

1. Create user account
2. Configure system settings
3. Choose desktop environment preferences

---

### Step 8: Run System Updates

After initial setup, update your system to get latest packages:

```bash
pikman upgrade
```

> 💡 **Tip:** Install updates before using the system for best compatibility and security.

---

## Related Guides

* [**BIOS Checklist**](../01-getting-started/03-bios-checklist.md) — Prepare your system before installation
* [**Creating Install Media**](02-creating-install-media.md) — USB drives on any OS
* [**Booting the Installer**](03-booting-the-installer.md) — Boot successfully from media
* [**Post-Install Setup**](05-post-install-setup.md) — Configure your new system
