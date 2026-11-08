# Blender Missing Title Bars - GNOME

---

## Table of Contents

- [Problem](#problem)
- [Root Cause](#root-cause)
- [Solutions](#solutions)
  - [Option A: Wait for Official Fix](#option-a-wait-for-official-fix)
  - [Option B: Launch in X11 Mode (Terminal)](#option-b-launch-in-x11-mode-terminal)
  - [Option C: Use Menu Editor (Recommended)](#option-c-use-menu-editor-recommended)
  - [Option D: Manual Desktop File Edit](#option-d-manual-desktop-file-edit)
- [Related Guides](#related-guides)

---

## Problem

`Blender` has an issue on `GNOME` that won't display the title bar on the main window or popup windows.

---

## Root Cause

- **`Blender`** dropped `libdecor` support
- **`GNOME`** doesn't support `XDG` Server Side Decorations

> ⚠️ **Note:** This is a known upstream issue being tracked by `Blender` developers: [Issue #148350](https://projects.blender.org/blender/blender/pulls/148350)

---

## Solutions

### Option A: Wait for Official Fix

The Blender team is working on resolving this issue. You can track progress at the official project page.

---

### Option B: Launch in `X11` Mode (Terminal)

Launch `Blender` from a terminal using environment variables to force `X11` mode:

```
WAYLAND_DISPLAY="" blender & disown
```

**What this does:**
- `WAYLAND_DISPLAY=""` - Forces `X11` compatibility mode
- `& disown` - Detaches the process so closing the terminal doesn't close Blender

---

### Option C: Use Menu Editor (Recommended)

Install **Menu Libre** to edit the application launcher:

#### Step 1: Install Menu Libre

```
pikman install menulibre
```

#### Step 2: Edit `Blender` Entry

1. Open **Menu Editor** from your app launcher
2. Find and select **`Blender`** in the list
3. Add this to the command line field:

```
Exec=env WAYLAND_DISPLAY= blender %f
```

4. Save changes

---

### Option D: Manual Desktop File Edit

Edit the Blender desktop file directly:

**Location:** `~/.local/share/applications/blender.desktop`

**Add or modify this line:**

```
Exec=env WAYLAND_DISPLAY= blender %f
```

> 💡 **Tip:** After making changes to desktop files, log out and back in for the changes to take effect.

---

## Related Guides

* [**Troubleshooting Hub**](../README.md#troubleshooting) — All common troubleshooting guides