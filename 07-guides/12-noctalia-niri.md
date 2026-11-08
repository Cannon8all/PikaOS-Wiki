# Noctalia Shell for Niri - Complete Guide

---

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Deactivate Otter-Shell and Add Noctalia](#deactivate-otter-shell-and-add-noctalia)
  - [Step 1: Remove Otter-Shell Components](#step-1-remove-otter-shell-components)
  - [Step 2: Add Noctalia to Startup](#step-2-add-noctalia-to-startup)
- [Configure Keybinds](#configure-keybinds)
  - [Remove Otter-Shell Keybinds](#remove-otter-shell-keybinds)
- [Core Noctalia Keybinds](#core-noctalia-keybinds)
  - [Launcher](#launcher)
  - [Control Center](#control-center)
  - [Settings](#settings)
  - [Window Switcher](#window-switcher)
- [Audio Keybinds](#audio-keybinds)
  - [Replace Otter-Shell Audio Bindings](#replace-otter-shell-audio-bindings)
- [Brightness Keybinds](#brightness-keybinds)
  - [Replace Otter-Shell Brightness Bindings](#replace-otter-shell-brightness-bindings)
- [Wallpaper and Overview Configuration](#wallpaper-and-overview-configuration)
- [Compositor Settings](#compositor-settings)
- [Apply Changes](#apply-changes)
- [Related Guides](#related-guides)

---

Complete installation and configuration guide for `Noctalia-Shell` on `Niri` desktop.

---

## Prerequisites

Before editing configuration files, backup your previous configuration:

```kdl
# Backup location: ~/.config/niri/config.kdl
cp ~/.config/niri/config.kdl ~/.config/niri/config.kdl.backup
```

> 💡 **Tip:** Always create a backup before modifying desktop environment configurations.

---

## Installation

Install the `noctalia-shell` package in the terminal:

```bash
pikman install noctalia
```

---

## Deactivate Otter-Shell and Add Noctalia

**Open your `~/.config/niri/config.kdl`:**

### Step 1: Remove Otter-Shell Components

Remove or comment out (`//`) the following lines:

```kdl
spawn-at-startup "otter-wallpaper"
spawn-at-startup "otter-osd"
spawn-at-startup "otter-notifications"
spawn-at-startup "otter-polkit"
spawn-at-startup "otter-idle"
spawn-at-startup "otter-theme-gen"
spawn-at-startup "otter-weather" "--watch" "900" "--write-cache"
spawn-at-startup "otter-search"
spawn-at-startup "otter-clip" "daemon"
spawn-at-startup "otter-bar"
```

> 💡 **Important Notes:**
> 
> - If you disable `otter-polkit`, enable `Polkit-Agent` in `Noctalia-Shell` settings (**Settings → Security / Authentication / Polkit Agent**)
> - If you disable `otter-idle`, enable idle in `Noctalia-Shell` settings (**Settings → Screenoff / Idle / Lock and Suspend**)

### Step 2: Add Noctalia to Startup

Add the following line to your config:

```kdl
spawn-at-startup "noctalia"
```

---

## Configure Keybinds

### Remove Otter-Shell Keybinds

Delete or comment out (`//`) these keybinds from your `config.kdl`:

```kdl
Super+Alt+L { spawn "otter-lock"; }
Mod+O { toggle-overview; }
```

---

## Core Noctalia Keybinds

### Launcher

**Replace the old keybind:**

Old:
```kdl
Mod+D { spawn "otter-launcher"; }
```

New:
```kdl
Mod+D { spawn-sh "noctalia msg panel-toggle launcher"; }
```

### Control Center

Add this keybind to access the control center:

```kdl
Mod+S { spawn-sh "noctalia msg panel-toggle control-center"; }
```

### Settings

Add this keybind to open Noctalia settings:

```kdl
Mod+Comma { spawn-sh "noctalia msg settings-toggle"; }
```

### Window Switcher

`Niri` has a built-in window switcher. Choose which one you prefer:

**Option 1 - Use `Niri`'s native:**
```kdl
# Keep your existing Niri window switcher
```

**Option 2 - Use `Noctalia-Shell`'s:**
```kdl
Alt+Tab { spawn-sh "noctalia msg window-switcher"; }
```

---

## Audio Keybinds

### Replace Otter-Shell Audio Bindings

Old:
```kdl
XF86AudioRaiseVolume allow-when-locked=true repeat=true { spawn "otter-osd" "volume-up" "5"; }
XF86AudioLowerVolume allow-when-locked=true repeat=true { spawn "otter-osd" "volume-down" "5"; }
XF86AudioMute        allow-when-locked=true { spawn "otter-osd" "volume-mute-toggle"; }
```

New:
```kdl
XF86AudioRaiseVolume { spawn-sh "noctalia msg volume-up"; }
XF86AudioLowerVolume { spawn-sh "noctalia msg volume-down"; }
XF86AudioMute        { spawn-sh "noctalia msg volume-mute"; }
```

---

## Brightness Keybinds

### Replace Otter-Shell Brightness Bindings

Old:
```kdl
XF86MonBrightnessUp   allow-when-locked=true repeat=true { spawn "otter-osd" "brightness-up" "5"; }
XF86MonBrightnessDown allow-when-locked=true repeat=true { spawn "otter-osd" "brightness-down" "5"; }
```

New:
```kdl
XF86MonBrightnessUp   { spawn-sh "noctalia msg brightness-up"; }
XF86MonBrightnessDown { spawn-sh "noctalia msg brightness-down"; }
```

---

## Wallpaper and Overview Configuration

To ensure the wallpaper layer renders correctly, update your `layer-rule`:

**Replace:**
```kdl
layer-rule {
    match namespace="^otter-wallpaper$"
    place-within-backdrop true
}
```

**With:**
```kdl
layer-rule {
    match namespace="^noctalia-backdrop"
    place-within-backdrop true
}
```

> 💡 **Additional Configuration:** Check out the official [`Noctalia-Shell` Wiki](https://docs.noctalia.dev/noctalia/compositor-settings/niri/) for additional background and overview configuration options.

---

## Compositor Settings

Add these settings at the bottom of your `config.kdl` file:

```kdl
debug {
    honor-xdg-activation-with-invalid-serial
}
```

This enables notification actions and window activation from Noctalia components.

---

## Apply Changes

**Restart your `Niri` session to see all changes take effect.**

You can restart without logging out by:
1. Press `Mod+Shift+E` to exit `Niri` (saves session)
2. Log back in, or
3. Reboot your system

---

## Related Guides

* [**Wiki Home**](../README.md) — Complete PikaOS documentation hub