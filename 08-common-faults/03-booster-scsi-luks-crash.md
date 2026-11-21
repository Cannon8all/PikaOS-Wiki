# Booster and SCSI LUKS Crash

---

## Table of Contents

- [Problem](#problem)
- [Root Cause](#root-cause)
- [Solution](#solution)
  - [Step 1: Remove Problematic USB Drive](#step-1-remove-problematic-usb-drive)
  - [Step 2: Boot Normally](#step-2-boot-normally)
  - [Step 3: Identify Problematic Drive (Optional)](#step-3-identify-problematic-drive-optional)
- [Related Guides](#related-guides)

---

## Problem

**`Booster` `initramfs` crashes** when attempting to unlock a `LUKS` encrypted drive during boot.

---

## Root Cause

Some **Sketchy `USB` drives** report themselves as `SCSI` drives instead of `USB` flash drives in their firmware. This causes `Booster` to crash during the encryption unlocking process.

> ⚠️ **Warning:** This is typically caused by low-quality or counterfeit `USB` drives that misreport their hardware type.

---

## Solution

### Step 1: Remove Problematic USB Drive

Before booting, ensure you do **NOT** have any USB drives plugged in that may be incorrectly reporting as SCSI drives.

### Step 2: Boot Normally

With the problematic drive removed, your system should boot normally and unlock the LUKS partition without issues.

### Step 3: Identify Problematic Drive (Optional)

If you need to identify which USB drive is causing the issue:

1. Boot with each USB drive individually
2. Check dmesg output for SCSI device detection:

```bash
dmesg | grep -i scsi
```

---

## Related Guides

* [**Troubleshooting Hub**](../README.md#troubleshooting) — All common troubleshooting guides