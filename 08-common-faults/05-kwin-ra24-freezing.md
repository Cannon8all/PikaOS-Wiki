# KWin Bug: Unsupported Screen Format RA24 (AMD GPUs)

---

## Table of Contents

- [Problem](#problem)
  - [Error Messages](#error-messages)
- [Root Cause](#root-cause)
- [Temporary Workaround: Enable Software Cursor](#temporary-workaround-enable-software-cursor)
  - [Step-by-Step Fix](#step-by-step-fix)
- [Related Guides](#related-guides)

---

## Problem

A critical regression in **KWin (Wayland)** can cause Plasma to repeatedly crash or fail to initialize on systems using newer AMD graphics cards, such as the **Radeon RX 9070**.

### Error Messages

You may see these errors in system logs:

- amdgpu: [drm] *ERROR* Unsupported screen format RA24 little-endian
- kwin_wayland: Atomic modeset commit failed! Invalid argument
- kwin_wayland: Applying output configuration failed!

---

## Root Cause

This is a **kernel/DRM rendering issue** where the hardware cursor initialization fails with certain AMD GPU firmware configurations. The problem affects atomic modeset commits when using hardware-accelerated cursors.

> ⚠️ **Note:** This is an upstream regression affecting newer AMD GPUs. A permanent fix requires kernel and Mesa updates.

---

## Temporary Workaround: Enable Software Cursor

Until a permanent upstream patch is applied, you can force KWin to use a software-based mouse cursor instead of hardware-driven DRM rendering. This bypasses the faulty screen format initialization.

### Step-by-Step Fix

**1. Open Environment Configuration File**

```bash
sudo nano /etc/environment
```

**2. Add Cursor Override Setting**

Add this line to the bottom of the file:

```ini
KWIN_FORCE_SW_CURSOR=1
```

**3. Save and Exit**

- Press `Ctrl+O`, then `Enter` to save
- Press `Ctrl+X` to exit nano

**4. Reboot Your System**

```bash
sudo reboot
```

---

## Related Guides

* [**Troubleshooting Hub**](../README.md#troubleshooting) — All common troubleshooting guides