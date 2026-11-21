# Secure Boot Setup Guide

---

## Table of Contents

- [How It Works](#how-it-works)
- [Prerequisites](#prerequisites)
  - [Step 1: Update Your System](#step-1-update-your-system)
  - [Step 2: Install and Enable](#step-2-install-and-enable)
  - [Step 3: Enroll the MOK](#step-3-enroll-the-mok)
    - [Enroll MOK (Machine Owner Key)](#enroll-mok-machine-owner-key)
  - [Step 4: Enable Secure Boot in Firmware](#step-4-enable-secure-boot-in-firmware)
  - [Step 5: Verify Configuration](#step-5-verify-configuration)
- [Additional Information](#additional-information)
  - [Updates](#updates)
  - [NVIDIA DKMS Modules](#nvidia-dkms-modules)
  - [Dual-Boot with Windows](#dual-boot-with-windows)
  - [Custom Kernels and Modules](#custom-kernels-and-modules)
  - [Disable Secure Boot Again](#disable-secure-boot-again)
- [Troubleshooting](#troubleshooting)
  - [Missed the MOK Enrollment Screen](#missed-the-mok-enrollment-screen)
  - [Security Violations](#security-violations)
  - [rEFInd Not Found](#refind-not-found)
  - [Still Booting Legacy rEFInd](#still-booting-legacy-refind)
- [Related Guides](#related-guides)

---

`PikaOS` now supports `Secure Boot`! No more manual signing with `sbctl`.

---

## How It Works

Your `PC` trusts `Microsoft`'s keys by default, so we use **`shim`** (a tiny bootloader `Microsoft` has signed) to start `rEFInd`. `rEFInd` and the kernel are signed with the `PikaOS` key. You tell your `PC` to trust that key once via the `MOK` enrollment screen, and after that, updates take care of themselves.

---

> 💡 **Important:** The live `ISO` won't boot with `Secure Boot` enabled.  
> **Install `PikaOS` first with `Secure Boot` disabled**, then return to this guide.

---

## Prerequisites

* A working `PikaOS` install that boots with **`rEFInd`** (default bootloader)
* Firmware `Secure Boot` keys include **`Microsoft`'s keys** (standard on all `PCs`)
* No custom keys or certificates needed—shim handles authentication

---

## Step 1: Update Your System

Signed kernels, `NVIDIA` modules, and `Secure Boot` `rEFInd` come from the repository. **Update your system first:**

```bash
pikman upgrade
```

> 💡 **Tip:** If you updated to a new kernel, reboot before continuing.

---

## Step 2: Install and Enable

```bash
pikman install pika-secureboot
sudo pika-secureboot enable
```

This sets up **`shim`** and signed `rEFInd` alongside your current setup. Your config and theme remain unchanged.

A "`PikaOS` `Secure Boot`" entry appears in your boot menu (set as default). If `rEFInd` uses the fallback `EFI/BOOT` folder, `shim` moves there instead.

> 💡 **Note:** You'll set a one-time password used only for `MOK` enrollment.

---

## Step 3: Enroll the MOK

**Reboot immediately.** A blue "Perform `MOK` Management" screen appears for ~10 seconds.

### Enroll `MOK` (`Machine Owner Key`)

1. Select **Enroll MOK**
2. Click **Continue**
3. Confirm with **Yes**
4. Enter your one-time password
5. Choose **Reboot**

---

## Step 4: Enable Secure Boot in Firmware

Enter your firmware (`UEFI`/`BIOS`) settings:

* Switch **`Secure Boot`** to **Enabled**
* Leave key settings at their default values
* Save changes and reboot

---

## Step 5: Verify Configuration

Check your `Secure Boot` status:

```bash
`mokutil` --sb-state
```

**Expected output:**
```
`SecureBoot`: enabled

or

`Secure Boot` is enabled on this machine.
```

If you see `SecureBoot`: disabled, return to Step 4.

---

## Additional Information

### Updates

You don't have to do anything when updates come in. New kernels, `rEFInd` and `shim` get copied to your `EFI` partition automatically.

### NVIDIA DKMS Modules

`NVIDIA` modules that come with the `PikaOS` kernel are already signed. If you use `DKMS` modules instead, enroll your `DKMS` key as well:

```bash
sudo `pika-secureboot` enable --dkms
```

Then reboot and do step 3 again.

> 💡 **Gamers:** `Linux` anti-cheat (`EAC`) only allows well-known keys as `MOKs`. A custom `DKMS` key blocks protected games—**use prebuilt modules for gaming.**

### Dual-Boot with Windows

No changes needed. `Windows` games/anti-cheat requiring `Secure Boot` work perfectly.

### Custom Kernels and Modules

Unsigned custom kernels or third-party modules **won't load** with `Secure Boot` enabled.

### Disable Secure Boot Again

Just switch `Secure Boot` off in your firmware. `PikaOS` keeps booting exactly the same way.

---

## Troubleshooting

### Missed the MOK Enrollment Screen

**Reboot again**—the enrollment request persists until completed.

If the screen doesn't appear:

```bash
sudo mokutil --revoke-import
sudo pika-secureboot enable
```

### Security Violations

The key isn't enrolled yet:

1. Disable `Secure Boot` in firmware
2. Boot to `PikaOS`
3. Run: `sudo `pika-secureboot` enable`
4. Complete Steps 3–4 again

### rEFInd Not Found

Search paths: `/boot/efi/EFI/refind` or `/boot/efi/EFI/BOOT`

For custom ESP mount points:

```bash
sudo `PIKA_ESP`=/path/to/esp `pika-secureboot` enable
```

### Still Booting Legacy rEFInd

MOK enrollment may have failed:

1. Complete Step 3 (enroll key)
2. Enable Secure Boot in firmware (Step 4)
3. Reboot and verify

---

## Related Guides

* [**Post-Install Setup**](../02-installation/05-post-install-setup.md) — Initial system configuration guide