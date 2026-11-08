# GTK3 Themes Don't Stick in GNOME

---

## Table of Contents

- [Problem](#problem)
- [Root Cause](#root-cause)
- [Solution](#solution)
  - [Step 1: Open Extension Manager](#step-1-open-extension-manager)
  - [Step 2: Disable Problematic Extension](#step-2-disable-problematic-extension)
- [Related Guides](#related-guides)

---

## Problem

The **GTK3 Theme** you set keeps randomly changing or resetting.

---

## Root Cause

This is caused by the "Legacy (GTK3) Theme Scheme Auto Switcher" extension, which automatically syncs your GTK3 theme with Libadwaita's Dark/Light mode.

> ⚠️ **Warning:** This automatic switching isn't compatible with out-of-spec themes like **Whitesur** or custom GTK3 themes that don't follow the standard naming conventions.

---

## Solution

### Step 1: Open Extension Manager

Install and open the **Extension Manager** application from your app launcher (if not already installed).

### Step 2: Disable Problematic Extension

Find and disable the following extension:

- **"Legacy (GTK3) Theme Scheme Auto Switcher"**

Once disabled, your GTK3 theme will remain consistent and won't reset automatically.

> 💡 **Tip:** You can re-enable this extension later if you need automatic dark/light mode switching for compatible themes.

---

## Related Guides

* [**Troubleshooting Hub**](../README.md#troubleshooting) — All common troubleshooting guides