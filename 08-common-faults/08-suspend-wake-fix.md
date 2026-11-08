# Suspend/Wake Up Fix Guide

---

## Table of Contents

- [Problem](#problem)
- [Root Cause](#root-cause)
- [Solutions](#solutions)
  - [Solution 1: Check Arch Linux Community Thread](#solution-1-check-arch-linux-community-thread)
  - [Solution 2: Prevent Immediate Wake from PCI Devices](#solution-2-prevent-immediate-wake-from-pci-devices)
  - [Solution 3: Common Fixes to Try](#solution-3-common-fixes-to-try)
- [Related Guides](#related-guides)

---

## Problem

Your system may experience issues when suspending or waking up, including:

- **Immediate wake-up** after attempting to suspend
- **Failed resume** from suspend mode
- **Hardware not responding** after waking (USB devices, network, etc.)

---

## Root Cause

This is typically caused by **PCI device power management conflicts**. Certain hardware components may prevent proper suspension or cause issues during wake-up due to:

- Aggressive PCI Power Management settings
- Device driver incompatibilities with suspend/resume cycles
- BIOS/UEFI firmware limitations

---

## Solutions

### Solution 1: Check Arch Linux Community Thread

Follow the detailed instructions in this **Arch Linux Forums** thread, particularly the solutions near the end:

[Arch Linux Suspend Issue - Forum Discussion](https://bbs.archlinux.org/viewtopic.php?id=271357)

This thread contains multiple community-suggested fixes for suspend/resume issues on various hardware configurations.

---

### Solution 2: Prevent Immediate Wake from PCI Devices

If the first solution doesn't resolve your issue, try disabling wake triggers from specific PCI devices:

[AskUbuntu: Prevent Wake from PCI Devices](https://askubuntu.com/questions/148481/how-do-i-prevent-immediate-wake-up-from-suspend-and-or-hibernation-from-pci-devi)

This guide provides commands to identify and disable devices that may be preventing proper suspend behavior.

---

### Solution 3: Common Fixes to Try

Here are some general troubleshooting steps you can attempt:

**1. Check Current Wake Sources**

```
cat /proc/acpi/wakeup
```

This shows which devices are enabled to wake your system. Look for entries marked with `*enabled`.

**2. Disable Problematic Devices (Temporary)**

To disable a device that's causing wake issues:

```
sudo echo DEVICENAME | sudo tee /proc/acpi/wakeup
```

Replace DEVICENAME with the actual device identifier from the list above.

**3. Update BIOS/UEFI Firmware**

Check your motherboard or laptop manufacturer's website for firmware updates that may improve suspend/resume compatibility.

---

## Related Guides

* [**Troubleshooting Hub**](../README.md#troubleshooting) — All common troubleshooting guides