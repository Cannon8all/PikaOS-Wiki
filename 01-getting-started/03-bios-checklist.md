# PikaOS BIOS/UEFI Checklist Guide

---

## Table of Contents

- [Why Check BIOS Settings?](#why-check-bios-settings)
- [Pre-Installation Checklist](#pre-installation-checklist)
- [Step-by-Step Verification Guide](#step-by-step-verification-guide)
- [Advanced Settings (Optional)](#advanced-settings-optional)
- [Common Issues & Solutions](#common-issues-solutions)
- [Manufacturer-Specific Quick Reference](#manufacturer-specific-quick-reference)
- [After Installation: Re-enabling Secure Boot](#after-installation-re-enabling-secure-boot)
- [Related Guides](#related-guides)

---

**Before installing PikaOS, verify your UEFI/BIOS settings to ensure a smooth installation experience.** This comprehensive checklist covers the essential firmware configurations required for proper booting and hardware compatibility.

---

## Why Check BIOS Settings?

Proper BIOS configuration is critical for successful Linux installation:

- **Secure Boot:** Must be disabled for initial installation (can be enabled later with PikaOS Secure Boot setup)
- **CSM/Legacy Mode:** Should be disabled to use pure `UEFI` boot
- **Boot Order:** `USB` drive must be prioritized or boot menu accessed manually
- **Hardware Features:** Disable conflicting features that may interfere with Linux

> 💡 **Tip:** Take notes of your current BIOS settings before making changes. This allows you to revert if needed.

---

## Pre-Installation Checklist

### Required Settings Overview

| Setting | Recommended Value | Why This Matters |
| :--- | :---: | :--- |
| **Secure Boot** | Disabled | Required for initial install; can enable later with PikaOS Secure Boot setup |
| **CSM (Compatibility Support Module)** | Disabled | Pure `UEFI` boot is required for modern Linux systems |
| **Boot Mode** | `UEFI` Only | Legacy/BIOS mode not supported by default |
| **SATA Operation** | `AHCI` | Required for proper `NVMe`/`SATA` drive detection |

> ⚠️ **Warning:** Changing these settings may affect your existing operating system. Back up important data before proceeding.

---

## Step-by-Step Verification Guide

### Step 1: Enter BIOS/UEFI Settings

**Access Methods:**
- **Reboot your computer** and press the setup key repeatedly
- Common keys: `F2`, `Del`, `F10`, `Esc`, or `F12` (varies by manufacturer)

*Expected result:* You'll see the BIOS/UEFI interface with various tabs.

---

### Step 2: Disable Secure Boot

**Location varies by manufacturer:**

| Manufacturer | Menu Path |
| :--- | :--- |
| **ASUS** | Security → Secure Boot Control → Disabled |
| **MSI** | Settings → Advanced → Windows OS Configuration → Disable UEFI Secure Boot |
| **Gigabyte** | BIOS → Secure Boot → Enabled → Set as "Other OS" or Disabled |
| **Dell** | System Configuration → BIOS Settings → Secure Boot → Disabled |
| **HP** | Security → Secure Boot Configuration → Disabled |

*Expected result:* Secure Boot status shows "**Disabled**" after changes.

> 💡 **Tip:** If you can't find Secure Boot settings, check under "Security," "Boot," or "Authentication" tabs.

---

### Step 3: Disable CSM/Legacy Support

**Location varies by manufacturer:**

| Manufacturer | Menu Path |
| :--- | :--- |
| **ASUS** | Boot → CSM (Compatibility Support Module) → Disabled |
| **MSI** | Settings → Advanced → Boot → CSM Support → Disabled |
| **Gigabyte** | BIOS → Boot → CSM Support → Disabled |
| **Dell** | System Configuration → Boot Sequence → UEFI Only |
| **Lenovo** | Startup → UEFI/Legacy Boot → UEFI Only |

*Expected result:* Boot mode shows "**UEFI**" not "Legacy" or "CSM".

> 💡 **Tip:** CSM may be labeled as "Legacy Support," "Boot Mode Compatibility," or similar.

---

### Step 4: Verify SATA Operation Mode

**Location varies by manufacturer:**

| Manufacturer | Menu Path |
| :--- | :--- |
| **ASUS** | Advanced → SATA Configuration → AHCI Mode |
| **MSI** | Settings → Advanced → Storage Configuration → AHCI |
| **Gigabyte** | Chipset → SATA Configuration → AHCI |
| **Dell** | System Configuration → Drive Configuration → AHCI |

*Expected result:* SATA mode shows "**`AHCI`**" not "`RAID`" or "`IDE`".

> ⚠️ **Warning:** Changing from `RAID` to `AHCI` may prevent Windows from booting on dual-boot systems. Ensure you have recovery media ready.

---

### Step 5: Set Boot Priority

**Access Boot Menu:**
- Press `F12`, `Esc`, or dedicated boot menu key during startup
- Select your USB drive from the list

*Expected result:* System boots to PikaOS installer instead of existing OS.

> 💡 **Tip:** If you're unsure which key to press, watch for on-screen prompts during boot (e.g., "Press F12 for Boot Menu").

---

## Advanced Settings (Optional)

### For Gaming Laptops with Hybrid Graphics

| Setting | Recommended Value | Notes |
| :--- | :---: | :--- |
| **Hybrid Mode** | Disabled | Use dedicated GPU only during install |
| **Discrete Graphics** | Enabled | Ensures NVIDIA/AMD card is primary |

### For AMD Ryzen Systems

| Setting | Recommended Value | Notes |
| :--- | :---: | :--- |
| **SVM Mode** | Enabled | Required for virtualization features |
| **Secure Boot Keys** | Clear All (if needed) | Only if you encounter key issues later |

### For Intel Systems (11th Gen+)

| Setting | Recommended Value | Notes |
| :--- | :---: | :--- |
| **VT-d** | Enabled | Required for virtualization and some hardware features |
| **CFG Lock** | Disabled | May be required by some Linux kernels |

> 💡 **Tip:** These advanced settings are optional but recommended for optimal performance on specific hardware configurations.

---

## Common Issues & Solutions

### Issue: Can't Access BIOS/UEFI?

**Solution:** Shut down completely (not restart), then power on while tapping setup key repeatedly. For Windows Fast Startup, hold `Shift` while clicking "Shut down" in Windows.

### Issue: Secure Boot Won't Disable?

**Solution:** Some systems require a password first or have locked settings. Check manufacturer documentation for unlocking procedures. Try clearing CMOS jumper if available.

### Issue: `USB` Drive Not Detected?

**Solution:** Ensure ISO was written correctly using `Rufus`, `BalenaEtcher`, or similar tool. Try different `USB` port (preferably `USB` 2.0). Some systems require `UEFI`-mode written media only.

### Issue: Installation Hangs After Boot Menu Selection?

**Solution:** Re-check SATA mode (must be `AHCI`). Some systems need `nomodeset` kernel parameter added to boot options. See [Installation Troubleshooting](../02-installation/03-booting-the-installer.md) for more details.

### Issue: Black Screen After Boot?

**Solution:** Try adding `nomodeset` to kernel parameters during boot. This disables GPU driver initialization until after installation completes.

---

## Manufacturer-Specific Quick Reference

| Brand | Boot Menu Key | BIOS Entry Key | Notes |
| :--- | :---: | :---: | :--- |
| **ASUS** | F8/F11 | Del or F2 | May require holding Shift during boot |
| **MSI** | F11 | Del | Advanced mode may need enabling first |
| **Gigabyte** | F12 | Del | Easy BIOS option available on newer models |
| **Dell** | F12 | F2 or F12 | Press F12 multiple times during startup |
| **HP** | F9 | Esc, then F10 | May require Fn key combination |
| **Lenovo** | F12 | F2 or Enter | Novo button available on some models |

---

## After Installation: Re-enabling Secure Boot

Once PikaOS is installed and configured with Secure Boot support:

1. Return to BIOS/UEFI settings
2. Enable Secure Boot
3. Leave keys at default (Microsoft + PikaOS)
4. Save and reboot

See [Secure Boot Setup Guide](../07-guides/04-secure-boot.md) for detailed post-installation configuration.

> 💡 **Tip:** You don't need to disable Secure Boot again after initial setup. PikaOS handles updates automatically once configured.

---

## Related Guides

* [**Installation Overview**](../02-installation/01-overview.md) — Complete installation methods and options
* [**Guided Installation**](../02-installation/04-guided-install.md) — Step-by-step automated partitioning guide
* [**Secure Boot Setup Guide**](../07-guides/04-secure-boot.md) — Post-installation secure boot configuration
