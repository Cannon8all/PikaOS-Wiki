# PikaOS Installer Boot Guide

---

## Table of Contents

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
- [Related Guides](#related-guides)
- [Quick Reference: Successful Boot Checklist](#quick-reference-successful-boot-checklist)
- [Special Cases: Manufacturer-Specific Notes](#special-cases-manufacturer-specific-notes)
  - [ASUS Systems](#asus-systems)
  - [Dell Systems](#dell-systems)
  - [HP Systems](#hp-systems)
  - [Lenovo Systems](#lenovo-systems)

---

**Complete guide to successfully booting the PikaOS installer from USB.** This comprehensive guide covers boot procedures, special requirements for different hardware manufacturers, troubleshooting boot issues, and important BIOS/UEFI configuration steps.

---

## Quick Boot Procedure

### Standard Installation Flow

1. **Insert bootable USB drive** into your system
2. **Reboot the computer** (do not start from within OS)
3. **Wait for PikaOS bird logo** to appear on screen
4. **Press `Enter`** to load the installer environment
5. **Select "Install Distro to System"** when menu appears
6. **Follow guided steps** until installation completes
7. **Reboot your system** when prompted

> 💡 **Tip:** Booting from USB requires a full system restart, not just a reboot from within an existing OS. For systems with Fast Startup enabled in Windows, perform a complete shutdown first.

---

## Important Information for `MSI` Systems

**MSI motherboards and laptops require special configuration** to boot PikaOS installer properly:

### `MSI`-Specific Boot Procedure

1. Access BIOS/`UEFI` settings during startup (press `Del` or `F2`)
2. Navigate to **Advanced Mode** → **Boot Settings**
3. Enable **`BOOTX64` Mode (`MSI` Compatibility Mode)**
4. Save changes and reboot with USB inserted
5. Select USB from boot menu when prompted

> 💡 **Tip:** This setting is specifically required for `MSI` hardware to properly recognize `UEFI` boot loaders. Without it, you may see "No bootable device" errors even with correct BIOS configuration.

---

## Boot Menu Access by Manufacturer

**Different systems use different keys to access boot menu or BIOS settings:**

| Manufacturer | Boot Menu Key | BIOS Entry Key | Special Notes |
| :--- | :---: | :---: | :--- |
| **ASUS** | F8, F11 | Del, F2 | May require Shift+Click Shutdown first |
| **`MSI`** | F11 | Del, F2 | Enable `BOOTX64` Mode for PikaOS |
| **Gigabyte** | F12 | Del | Easy BIOS available on newer models |
| **Dell** | F12 | F2, F12 | Press multiple times during startup |
| **HP** | F9, Esc | Esc, then F10 | May require Fn key combination |
| **Lenovo** | F12, Fn+F12 | F2, Enter | Novo button on some models |
| **Acer** | F12 | Del, F2 | May need to enable Boot Menu first |
| **Aspire** | F2 | Del, F2 | Check for Easy Boot option |

> 💡 **Tip:** Watch for on-screen prompts during startup. Most systems display a brief message like "Press F12 for Boot Menu" when powering on.

---

## Detailed Boot Process

### Step 1: Prepare Your System

**Before attempting to boot from USB:**

| Task | Status | Notes |
| :--- | :---: | :--- |
| **`USB` drive prepared** | ☐ | Written with PikaOS `ISO`, verified |
| **BIOS Secure Boot disabled** | ☐ | Required for initial installation |
| **CSM/Legacy mode off** | ☐ | `UEFI`-only boot required |
| **SATA set to AHCI** | ☐ | Proper drive detection needed |

> ⚠️ **Warning:** If you're dual-booting with Windows, disable Fast Startup in Windows first. Otherwise the system may not fully shut down and BIOS changes won't take effect.

---

### Step 2: Access Boot Menu or BIOS

**During system startup (immediately after powering on):**

1. **Watch for manufacturer logo** — this is when to start pressing keys
2. **Press boot menu key repeatedly** — don't wait, start early
3. **If no response**, restart and try BIOS entry key instead
4. **Navigate BIOS settings** if you need to modify boot configuration

*Expected result:* Either boot menu appears with `USB` option, or BIOS/`UEFI` interface loads.

---

### Step 3: Select Boot Device

**From boot menu:**
- Use arrow keys to navigate options
- Look for entry containing "USB", your drive brand name, or "UEFI: [Drive Name]"
- Press **Enter** to select

*Expected result:* PikaOS bird logo appears on screen.

> 💡 **Tip:** If you see Windows Boot Manager instead of USB options, Secure Boot may still be enabled or boot order needs adjustment in BIOS settings.

---

### Step 4: PikaOS Boot Menu

**After successful USB boot detection:**

You'll see the PikaOS boot menu with bird logo featuring:
- **Install Distro to System** (default) — Full graphical installer
- **Try PikaOS without installing** — Live session for testing
- **Boot from hard drive** — Return to existing OS
- **Advanced options** — Kernel parameters, recovery modes

**Select "Install Distro to System"** and press Enter.

---

### Step 5: Installer Environment Loads

**After selecting installation option:**

1. Wait for loading animation (bird logo with progress indicator)
2. System loads into live desktop environment
3. Welcome screen appears with installation options
4. Click **"Install Distro to System"** button

*Expected result:* Graphical installer window opens, ready for partitioning choices.

> 💡 **Tip:** Loading time varies by hardware (5-15 minutes typical). Be patient — don't interrupt the process.

---

## Troubleshooting Boot Issues

### Issue: No bootable device found or black screen on `USB` boot

**Possible causes and solutions:**

| Cause | Solution |
| :--- | :--- |
| **Secure Boot enabled** | Disable in BIOS/`UEFI` settings |
| **CSM/Legacy mode active** | Switch to `UEFI`-only mode |
| **Wrong boot method** | Try different `USB` writing tool |
| **Corrupted `ISO`** | Re-download and verify checksum |

> 💡 **Tip:** For `MSI` systems specifically, ensure `BOOTX64` Mode is enabled in BIOS Advanced options.

---


### Issue: System boots to existing OS instead of USB

**Causes and solutions:**

| Cause | Solution |
| :--- | :--- |
| **Boot order incorrect** | Change BIOS boot priority, put USB first |
| **Fast Startup enabled (Windows)** | Disable in Windows power settings |
| **Secure Boot interfering** | Disable Secure Boot in BIOS |
| **USB not detected as bootable** | Re-write using different tool |

**How to disable Windows Fast Startup:**
1. Open Control Panel → Power Options
2. Click "Choose what power buttons do"
3. Click "Change settings that are currently unavailable"
4. Uncheck "Turn on fast startup"
5. Save changes and perform complete shutdown

---


## Advanced Boot Parameters

**For experienced users who need custom boot configurations:**

### Available Kernel Parameters

| Parameter | Effect | When to Use |
| :--- | :---: | :--- |
| **`nomodeset`** | Disable GPU driver initialization | Black screen on boot |
| **`nouveau.modeset=0`** | Disable Nouveau driver specifically | `NVIDIA` GPU issues |
| **`acpi=enforce`** | Strict ACPI compliance | Power management issues |
| **`intel_idle.max_cstate=1`** | Limit CPU C-states | Intel system instability |
| **`amd_iommu_map=on`** | Enable AMD `IOMMU` | Virtualization conflicts |

### How to Use Custom Parameters

1. At PikaOS boot menu, press `Tab` or `e` to edit boot options
2. Locate line starting with `linux` or `kernel`
3. Add your parameter(s) at end of line (space-separated)
4. Press F10 or Ctrl+X to boot with modified parameters

> 💡 **Tip:** Boot parameters are temporary and only affect the current boot session. They don't modify installed system configuration.

---

## Related Guides

* [**BIOS Checklist**](../01-getting-started/03-bios-checklist.md) — Configure BIOS settings before installation
* [**Creating Install Media**](02-creating-install-media.md) — Write `ISO` to `USB` drive, verify integrity
* [**Guided Installation**](04-guided-install.md) — Automated partitioning with advanced filesystem options
* [**Dual Boot Windows**](06-dual-boot-windows.md) — Safe Windows coexistence setup
* [**Post-Install Setup**](05-post-install-setup.md) — Initial configuration after installation
* [**Common Troubleshooting Steps**](../08-common-faults/01-common-troubleshooting-steps.md) — Comprehensive troubleshooting guide

---

## Quick Reference: Successful Boot Checklist

Before installation, ensure these conditions are met:

- [ ] `USB` drive properly written with verified `ISO`
- [ ] BIOS Secure Boot disabled
- [ ] CSM/Legacy mode disabled (`UEFI` only)
- [ ] SATA operation set to AHCI
- [ ] Boot menu accessible from system
- [ ] `MSI` `BOOTX64` Mode enabled (if applicable)
- [ ] Windows Fast Startup disabled (if dual-booting)

> 💡 **Tip:** If you've verified all settings above and still can't boot, try a different `USB` port or write tool. Hardware compatibility varies across systems.

---

## Special Cases: Manufacturer-Specific Notes

### ASUS Systems
- May require disabling "Fast Boot" in BIOS
- Some models need "Secure Boot Control" explicitly set to "Other OS"
- Use F8 or F11 for boot menu access

### Dell Systems
- Press F12 multiple times immediately after power-on
- Some business models have additional security settings that may block USB boot
- Check "Boot Sequence" in BIOS for UEFI/Legacy options

### HP Systems
- May require Esc key first, then F10 for BIOS
- Some models have "Secure Boot" under Security tab
- Try both F9 and F12 for boot menu access

### Lenovo Systems
- Novo button (physical button on side) provides direct boot menu
- F2 or Enter to enter BIOS settings
- May need to enable "Boot from USB" in Startup tab