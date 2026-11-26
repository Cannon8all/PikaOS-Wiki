# PikaOS Prepare USB and Boot Guide

---

## Table of Contents

- [Why Verify the ISO?](#why-verify-the-iso)
- [Pre-flight Checklist](#pre-flight-checklist)
- [Verify ISO Integrity (Recommended)](#verify-iso-integrity-recommended)
- [Writing the ISO to USB Drive](#writing-the-iso-to-usb-drive)
- [Tool Comparison Table](#tool-comparison-table)
- [Troubleshooting Common Issues](#troubleshooting-common-issues)
- [After Writing: Verify Bootability](#after-writing-verify-bootability)
- [Quick Reference: Recommended Workflow](#quick-reference-recommended-workflow)
- [Quick Boot Procedure](#quick-boot-procedure)
  - [Standard Installation Flow](#standard-installation-flow)
- [Important Information for MSI Systems](#important-information-for-msi-systems)
  - [MSI-Specific Boot Procedure](#msi-specific-boot-procedure)
- [Boot Menu Access by Manufacturer](#boot-menu-access-by-manufacturer)
- [Detailed Boot Process](#detailed-boot-process)
  - [Step 1: Prepare Your System](#step-1-prepare-your-system)
  - [Step 2: Access Boot Menu or BIOS](#step-2-access-boot-menu-or-bios)
  - [Step 3: Select Boot Device](#step-3-select-boot-device)
  - [Step 4: PikaOS Boot Menu](#step-4-pikaos-boot-menu)
  - [Step 5: Installer Environment Loads](#step-5-installer-environment-loads)
- [Troubleshooting Boot Issues](#troubleshooting-boot-issues)
  - [Issue: No bootable device found or black screen on USB boot](#issue-no-bootable-device-found-or-black-screen-on-usb-boot)
  - [Issue: Black screen after selecting boot option](#issue-black-screen-after-selecting-boot-option)
  - [Issue: System boots to existing OS instead of USB](#issue-system-boots-to-existing-os-instead-of-usb)
  - [Issue: USB appears in boot menu but wont boot](#issue-usb-appears-in-boot-menu-but-wont-boot)
  - [Issue: Installer hangs during boot sequence](#issue-installer-hangs-during-boot-sequence)
- [Boot Mode Comparison](#boot-mode-comparison)
- [Advanced Boot Parameters](#advanced-boot-parameters)
  - [Available Kernel Parameters](#available-kernel-parameters)
  - [How to Use Custom Parameters](#how-to-use-custom-parameters)
- [Quick Reference: Successful Boot Checklist](#quick-reference-successful-boot-checklist)
- [Special Cases: Manufacturer-Specific Notes](#special-cases-manufacturer-specific-notes)
  - [ASUS Systems](#asus-systems)
  - [Dell Systems](#dell-systems)
  - [HP Systems](#hp-systems)
  - [Lenovo Systems](#lenovo-systems)
- [Related Guides](#related-guides)

---

**Create bootable USB drives for PikaOS installation using your preferred tool, and successfully boot from it.** This guide covers ISO verification, USB writing methods, boot procedures, BIOS/UEFI configuration, and troubleshooting for both media preparation and the boot process.

---

## Part 1: Preparing Your USB Drive

### Why Verify the ISO?

**ISO integrity verification is critical** before creating install media:

- **File Integrity:** Confirms download completed without corruption
- **Authenticity:** Verifies official PikaOS image, not tampered
- **Reliability:** Prevents installation failures due to bad data

> 💡 **Tip:** Always verify the ISO checksum before writing to USB! A corrupted ISO will cause installation failures and wasted time.

---

### Pre-flight Checklist

**Before creating install media, ensure you have:**

| Item                                  | Status | Notes                                 |
|:------------------------------------- |:------:|:------------------------------------- |
| **Correct PikaOS edition downloaded** | ☐      | GNOME, KDE, Hyprland, Niri, or COSMIC |
| **USB drive ≥8GB capacity**         | ☐      | USB 3.0+ recommended for speed      |
| **BIOS Secure Boot disabled**         | ☐      | Required for initial installation     |
| **Important data backed up**          | ☐      | USB will be completely erased       |

> ⚠️ **Warning:** All data on the USB drive will be permanently erased during creation. Back up any important files first.

---

### Verify ISO Integrity (Recommended)

#### Step 1: Get the Published MD5 Checksum

**Procedure:**

1. Go to the [official PikaOS download page](https://pika-os.com/download)
2. Right-click your chosen download button
3. Select **Copy link address**
4. Open a new browser tab and paste URL
5. Change `.iso` extension to `.md5`
6. Press **Enter** — you'll see the checksum text

*Expected result:* A single line with 32-character hash string like `a1b2c3d4e5f6789012345678901234`

---

#### Step 2: Generate Local MD5 Hash

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

#### Step 3: Compare Checksums

| Result         | Action Required                                                |
|:--------------:|:-------------------------------------------------------------- |
| **✅ Match**    | Download is authentic and complete — proceed to USB creation |
| **❌ Mismatch** | Delete file, re-download ISO from official source            |

> ⚠️ **Warning:** Never install from an ISO with mismatched checksums. This indicates corruption or potential tampering. Do not proceed until you have a verified download.

---

### Writing the ISO to USB Drive

#### Method 1: GNOME Disks (GUI - Recommended for Linux)

**Best for:** Beginners and GNOME desktop users

**Procedure:**

1. Open **Disks** application from your menu
2. Select your USB drive in the left panel
3. Click **⋮** menu → **Restore Disk Image...**
4. Browse to select your PikaOS ISO file
5. Click **Start Restoring**
6. Confirm when prompted

*Expected result:* Progress bar shows writing status, completion message appears when done.

> 💡 **Tip:** GNOME Disks automatically verifies the write after completion, providing extra assurance.

---

#### Method 2: Balena Etcher (Cross-Platform)

**Best for:** Users on Windows, macOS, or Linux who prefer GUI tools

**Procedure:**

1. Download and install [Balena Etcher](https://www.balena.io/etcher/)
2. Launch Etcher application
3. Click **Flash from file** → Select your ISO
4. Click **Select target** → Choose USB drive
5. Click **Flash!** to begin writing

*Expected result:* Three progress bars show validation, flashing, and completion with success message.

> 💡 **Tip:** Balena Etcher automatically validates the write process, reducing user error.

---

#### Method 3: dd Command (Terminal - Advanced)

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

#### Method 4: Ventoy (Multi-Boot USB)

**Best for:** Users wanting multiple ISOs on one portable drive

**Procedure:**

1. Download [Ventoy](https://www.ventoy.net/en/download.html)
2. Install Ventoy to your USB drive (**this will erase all data!**)
3. Copy PikaOS ISO file(s) directly to the USB's FAT32 partition
4. Boot from USB → Ventoy boot menu appears → Select PikaOS ISO

*Expected result:* Ventoy boot menu with all ISOs listed, select PikaOS to install.

> 💡 **Tip:** Ventoy is excellent for tech enthusiasts who maintain a multi-boot recovery drive with various Linux distributions.

---

### Tool Comparison Table

| Tool              | Platform            | Best For                | Difficulty | Auto-Verify |
|:----------------- |:-------------------:|:----------------------- |:----------:|:-----------:|
| **GNOME Disks**   | Linux (GNOME)       | Beginners, GNOME users  | Easy       | ✅ Yes       |
| **Balena Etcher** | Windows/macOS/Linux | Cross-platform GUI      | Easy       | ✅ Yes       |
| **dd command**    | Linux/Unix          | Advanced use, scripting | Medium     | ❌ No        |
| **Ventoy**        | All platforms       | Multi-boot USB setup    | Medium     | ⚠️ Partial   |

> 💡 **Tip:** For first-time users, GNOME Disks or Balena Etcher provide the best balance of ease and reliability.

---

### Troubleshooting Common Issues

#### Issue: "Device is busy" error with dd or Disks

**Cause:** USB partition is mounted and in use

**Solution:** Unmount the USB drive first

```bash
sudo umount /dev/sdX1
```

Replace `sdX1` with your actual partition (check with `lsblk`).

---

#### Issue: Balena Etcher fails validation

**Cause:** ISO may be corrupted or Ventoy-formatted drive detected

**Solution:** 

1. Re-download ISO from official source
2. Verify MD5 checksum first
3. Try different USB port or drive

---

#### Issue: USB not detected after writing

**Possible causes:**

- Wrong USB port (try different one, prefer USB 2.0)
- Drive too slow for write speed
- ISO was corrupted during download

**Solution:** Verify MD5 checksum, try slower write speed or different tool (Ventoy often works where others fail).

---

#### Issue: "No bootable device found" after writing

**Cause:** BIOS/UEFI settings incorrect or USB not properly written

**Solutions:**

1. Ensure Secure Boot is disabled in firmware
2. Check boot order prioritizes USB
3. Try UEFI vs Legacy mode (or vice versa)
4. Re-write using different method

> 💡 **Tip:** MSI motherboards may require enabling BOOTX64 Mode (MSI Compatibility Mode) in UEFI settings.

---

### After Writing: Verify Bootability

**Before installing, test that your USB boots correctly:**

1. Insert USB into target system
2. Reboot and access boot menu (typically F12, Esc, or Del)
3. Select USB drive from boot options
4. **Expected result:** PikaOS boot menu appears with bird logo

*If it doesn't boot:*

- Re-write the ISO using a different method
- Verify MD5 checksum first
- Check BIOS/UEFI settings (Secure Boot disabled, UEFI mode)
- Try a different USB port or drive

---

### Quick Reference: Recommended Workflow

1. **Download ISO** from official PikaOS site
2. **Verify MD5 checksum** before proceeding
3. **Choose writing tool** based on your experience level
4. **Write to USB drive** (8GB+ recommended)
5. **Test bootability** on target system
6. **Configure BIOS/UEFI** settings as needed
7. **Begin installation** once boot menu appears

> 💡 **Tip:** Once your bootable USB is ready, you're almost there! Continue reading below for the complete boot procedure.

---

## Part 2: Booting the Installer

### Quick Boot Procedure

#### Standard Installation Flow

1. **Insert bootable USB drive** into your system
2. **Reboot the computer** (do not start from within OS)
3. **Wait for PikaOS bird logo** to appear on screen
4. **Press Enter** to load the installer environment
5. **Select "Install Distro to System"** when menu appears
6. **Follow guided steps** until installation completes
7. **Reboot your system** when prompted

---

### Important Information for MSI Systems

**MSI motherboards and laptops require special configuration** to boot PikaOS installer properly:

#### MSI-Specific Boot Procedure

1. Access BIOS/UEFI settings during startup (press Del or F2)
2. Navigate to **Advanced Mode** → **Boot Settings**
3. Enable **BOOTX64 Mode (MSI Compatibility Mode)**
4. Save changes and reboot with USB inserted
5. Select USB from boot menu when prompted

> 💡 **Tip:** This setting is specifically required for MSI hardware to properly recognize UEFI boot loaders. Without it, you may see "No bootable device" errors even with correct BIOS configuration.

---

### Boot Menu Access by Manufacturer

**Different systems use different keys to access boot menu or BIOS settings:**

| Manufacturer | Boot Menu Key | BIOS Entry Key | Special Notes                          |
|:------------ |:-------------:|:--------------:|:-------------------------------------- |
| **ASUS**     | F8, F11       | Del, F2        | May require Shift+Click Shutdown first |
| **MSI**    | F11           | Del, F2        | Enable BOOTX64 Mode for PikaOS       |
| **Gigabyte** | F12           | Del            | Easy BIOS available on newer models    |
| **Dell**     | F12           | F2, F12        | Press multiple times during startup    |
| **HP**       | F9, Esc       | Esc, then F10  | May require Fn key combination         |
| **Lenovo**   | F12, Fn+F12   | F2, Enter      | Novo button on some models             |
| **Acer**     | F12           | Del, F2        | May need to enable Boot Menu first     |
| **Aspire**   | F2            | Del, F2        | Check for Easy Boot option             |

> 💡 **Tip:** Watch for on-screen prompts during startup. Most systems display a brief message like "Press F12 for Boot Menu" when powering on.

---

### Detailed Boot Process

#### Step 1: Prepare Your System

**Before attempting to boot from USB:**

| Task                          | Status | Notes                               |
|:----------------------------- |:------:|:----------------------------------- |
| **USB drive prepared**      | ☐      | Written with PikaOS ISO, verified |
| **BIOS Secure Boot disabled** | ☐      | Required for initial installation   |
| **CSM/Legacy mode off**       | ☐      | UEFI-only boot required           |
| **SATA set to AHCI**          | ☐      | Proper drive detection needed       |

> ⚠️ **Warning:** If you're dual-booting with Windows, disable Fast Startup in Windows first. Otherwise the system may not fully shut down and BIOS changes won't take effect.

---

#### Step 2: Access Boot Menu or BIOS

**During system startup (immediately after powering on):**

1. **Watch for manufacturer logo** — this is when to start pressing keys
2. **Press boot menu key repeatedly** — don't wait, start early
3. **If no response**, restart and try BIOS entry key instead
4. **Navigate BIOS settings** if you need to modify boot configuration

*Expected result:* Either boot menu appears with USB option, or BIOS/UEFI interface loads.

---

#### Step 3: Select Boot Device

**From boot menu:**

- Use arrow keys to navigate options
- Look for entry containing "USB", your drive brand name, or "UEFI: [Drive Name]"
- Press **Enter** to select

*Expected result:* PikaOS bird logo appears on screen.

> 💡 **Tip:** If you see Windows Boot Manager instead of USB options, Secure Boot may still be enabled or boot order needs adjustment in BIOS settings.

---

#### Step 4: PikaOS Boot Menu

**After successful USB boot detection:**

You'll see the PikaOS boot menu with bird logo featuring:

- **Install Distro to System** (default) — Full graphical installer
- **Try PikaOS without installing** — Live session for testing
- **Boot from hard drive** — Return to existing OS
- **Advanced options** — Kernel parameters, recovery modes

**Select "Install Distro to System"** and press Enter.

---

#### Step 5: Installer Environment Loads

**After selecting installation option:**

1. Wait for loading animation (bird logo with progress indicator)
2. System loads into live desktop environment
3. Welcome screen appears with installation options
4. Click **"Install Distro to System"** button

*Expected result:* Graphical installer window opens, ready for partitioning choices.

> 💡 **Tip:** Loading time varies by hardware (5-15 minutes typical). Be patient — don't interrupt the process.

---

### Troubleshooting Boot Issues

#### Issue: No bootable device found or black screen on USB boot

**Possible causes and solutions:**

| Cause                      | Solution                         |
|:-------------------------- |:-------------------------------- |
| **Secure Boot enabled**    | Disable in BIOS/UEFI settings  |
| **CSM/Legacy mode active** | Switch to UEFI-only mode       |
| **Wrong boot method**      | Try different USB writing tool |
| **Corrupted ISO**        | Re-download and verify checksum  |

> 💡 **Tip:** For MSI systems specifically, ensure BOOTX64 Mode is enabled in BIOS Advanced options.

---

#### Issue: System boots to existing OS instead of USB

**Causes and solutions:**

| Cause                              | Solution                                 |
|:---------------------------------- |:---------------------------------------- |
| **Boot order incorrect**           | Change BIOS boot priority, put USB first |
| **Fast Startup enabled (Windows)** | Disable in Windows power settings        |
| **Secure Boot interfering**        | Disable Secure Boot in BIOS              |
| **USB not detected as bootable**   | Re-write using different tool            |

**How to disable Windows Fast Startup:**

1. Open Control Panel → Power Options
2. Click "Choose what power buttons do"
3. Click "Change settings that are currently unavailable"
4. Uncheck "Turn on fast startup"
5. Save changes and perform complete shutdown

---

### Advanced Boot Parameters

**For experienced users who need custom boot configurations:**

#### How to Use Custom Parameters

1. At PikaOS boot menu, press Tab or `e` to edit boot options
2. Locate line starting with linux or kernel
3. Add your parameter(s) at end of line (space-separated)
4. Press F10 or Ctrl+X to boot with modified parameters

> 💡 **Tip:** Boot parameters are temporary and only affect the current boot session. They don't modify installed system configuration.

---

### Quick Reference: Successful Boot Checklist

Before installation, ensure these conditions are met:

- [ ] USB drive properly written with verified ISO
- [ ] BIOS Secure Boot disabled
- [ ] CSM/Legacy mode disabled (UEFI only)
- [ ] SATA operation set to AHCI
- [ ] Boot menu accessible from system
- [ ] MSI BOOTX64 Mode enabled (if applicable)
- [ ] Windows Fast Startup disabled (if dual-booting)

> 💡 **Tip:** If you've verified all settings above and still can't boot, try a different USB port or write tool. Hardware compatibility varies across systems.

---

### Special Cases: Manufacturer-Specific Notes

#### ASUS Systems

- May require disabling "Fast Boot" in BIOS
- Some models need "Secure Boot Control" explicitly set to "Other OS"
- Use F8 or F11 for boot menu access

#### Dell Systems

- Press F12 multiple times immediately after power-on
- Some business models have additional security settings that may block USB boot
- Check "Boot Sequence" in BIOS for UEFI/Legacy options

#### HP Systems

- May require Esc key first, then F10 for BIOS
- Some models have "Secure Boot" under Security tab
- Try both F9 and F12 for boot menu access

#### Lenovo Systems

- Novo button (physical button on side) provides direct boot menu
- F2 or Enter to enter BIOS settings
- May need to enable "Boot from USB" in Startup tab

---

## Related Guides

* [**Guided Installation**](03-guided-install.md) — Automated partitioning with advanced options
* [**Post-Install Setup**](04-post-install.md) — Initial configuration after installation
* [**BIOS Checklist**](../01-getting-started/03-bios-checklist.md) — Configure BIOS settings before installation
* [**Common Troubleshooting Steps**](../08-common-faults/01-common-troubleshooting-steps.md) — Comprehensive troubleshooting guide