# Noctalia-Shell V5 for Hyprland

---

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Deactivate Otter-Shell](#deactivate-otter-shell)
- [Add Noctalia-Shell](#add-noctalia-shell)
- [Configure Keybinds](#configure-keybinds)
  - [Core Noctalia Keybinds](#core-noctalia-keybinds)
    - [Step 1: Remove Otter-Shell Keybinds](#step-1-remove-otter-shell-keybinds)
    - [Step 2: Add Noctalia Variables](#step-2-add-noctalia-variables)
    - [Step 3: Add Noctalia Keybinds](#step-3-add-noctalia-keybinds)
  - [Audio Keybinds](#audio-keybinds)
  - [Brightness Keybinds](#brightness-keybinds)
- [Window Rules](#window-rules)
  - [Enable Blur for Noctalia Components](#enable-blur-for-noctalia-components)
  - [Noctalia Settings Window Rule](#noctalia-settings-window-rule)
- [Apply Changes](#apply-changes)
- [Related Guides](#related-guides)

---

Complete installation and configuration guide for `Noctalia-Shell` on `Hyprland` desktop.

---

## Prerequisites

Before editing configuration files, backup your previous configuration:

```bash
cp -r ~/.config/hypr ~/.config/hypr.backup
```

Backup location: `~/.config/hypr`

---

## Installation

Install the `noctalia-shell` package in the terminal:

```bash
pikman install noctalia
```

---

## Deactivate `Otter-Shell`

**Open your `~/.config/hypr/exec.lua`:**

Remove or comment out (`--`) the following lines:

```lua
hl.exec_cmd("otter-wallpaper")
hl.exec_cmd("otter-osd")
hl.exec_cmd("otter-notifications")
hl.exec_cmd("otter-polkit")
hl.exec_cmd("otter-idle")
hl.exec_cmd("otter-theme-gen")
hl.exec_cmd("otter-weather --watch 900 --write-cache")
hl.exec_cmd("otter-search")
hl.exec_cmd("otter-clip daemon")
hl.exec_cmd("otter-bar")
```

> 💡 **Important Notes:**
> 
> - If you disable `otter-polkit`, enable `Polkit-Agent` in `Noctalia-Shell` settings (**Settings → Security / Authentication / Polkit Agent**)
> - If you disable `otter-idle`, enable idle in `Noctalia-Shell` settings (**Settings → Screenoff / Idle / Lock and Suspend**)

---

## Add Noctalia-Shell

Add the following to your `~/.config/hypr/exec.lua`:

```lua
hl.exec_cmd("noctalia")
```

---

## Configure Keybinds

### Core `Noctalia-Shell` Keybinds

**Open your `~/.config/hypr/keybinds.lua`:**

#### Step 1: Remove `Otter-Shell` Keybinds

Remove or comment (`--`) the following keybinds:

```lua
hl.bind(mainMod .. " + " .. "D", hl.dsp.exec_cmd("otter-launcher"), { description = "Application Launcher" })
hl.bind(mainMod .. " + " .. "P", hl.dsp.exec_cmd("otter-screenshot"), { description = "Screenshot" })
hl.bind(mainMod .. " + " .. "SHIFT + P", hl.dsp.exec_cmd("otter-rec"), { description = "Screen Recorder" })
hl.bind(mainMod .. " + " .. "T", hl.dsp.exec_cmd("otter-transcribectl toggle"), { description = "Toggle Transcription" })
hl.bind(mainMod .. " + " .. "tab", hl.dsp.exec_cmd("otter-overview"), { description = "Show Overview" })
```

#### Step 2: Add `Noctalia-Shell` Variables

At the top of the config file, add:

```lua
local mainMod = `SUPER`
local ipc = `noctalia msg `
```

#### Step 3: Add `Noctalia-Shell` Keybinds

Add the following keybinds:

```lua
hl.bind(mainMod .. "+Space", hl.dsp.exec_cmd(ipc .. "panel-toggle launcher"))
hl.bind(mainMod .. "+S", hl.dsp.exec_cmd(ipc .. "panel-toggle control-center"))
hl.bind(mainMod .. "+comma", hl.dsp.exec_cmd(ipc .. "settings-toggle"))
hl.bind("ALT + Tab", hl.dsp.exec_cmd(ipc .. "window-switcher"))
hl.bind("PRINT", hl.dsp.exec_cmd("noctalia msg screenshot-region"))
```

### Audio Keybinds

**Replace `Otter-Shell` audio bindings:**

Old:
```lua
hl.bind("XF86AudioRaiseVolume", hl.dsp.exec_cmd("otter-osd volume-up 5"), { locked = true, repeating = true, description = "Raise Volume" })
hl.bind("XF86AudioLowerVolume", hl.dsp.exec_cmd("otter-osd volume-down 5"), { locked = true, repeating = true, description = "Lower Volume" })
hl.bind("XF86AudioMute", hl.dsp.exec_cmd("otter-osd volume-mute-toggle"), { locked = true, description = "Toggle Mute" })
```

New:
```lua
hl.bind("XF86AudioRaiseVolume", hl.dsp.exec_cmd(ipc .. "volume-up"))
hl.bind("XF86AudioLowerVolume", hl.dsp.exec_cmd(ipc .. "volume-down"))
hl.bind("XF86AudioMute", hl.dsp.exec_cmd(ipc .. "volume-mute"))
```

### Brightness Keybinds

**Replace `Otter-Shell` brightness bindings:**

Old:
```lua
hl.bind("XF86MonBrightnessUp", hl.dsp.exec_cmd("otter-osd brightness-up 5"), { locked = true, repeating = true, description = "Brightness Up" })
hl.bind("XF86MonBrightnessDown", hl.dsp.exec_cmd("otter-osd brightness-down 5"), { locked = true, repeating = true, description = "Brightness Down" })
hl.bind("Caps_Lock", hl.dsp.exec_cmd("otter-osd caps-lock"), { locked = true, description = "Caps Lock OSD" })
```

New:
```lua
hl.bind("XF86MonBrightnessUp", hl.dsp.exec_cmd(ipc .. "brightness-up"))
hl.bind("XF86MonBrightnessDown", hl.dsp.exec_cmd(ipc .. "brightness-down"))
```

---

## Window Rules

**Open your `~/.config/hypr/windows.lua`:**

### Enable Blur for Noctalia Components

Add blur to `Noctalia-Shell`'s bar, panels, dock, and notifications:

```lua
-- Noctalia blur
hl.layer_rule({
  name = "noctalia",
  match = {
    namespace = "^noctalia-(bar-.+|notification|dock|panel|attached-panel|osd|window-switcher)$",
  },
  no_anim = true,
  ignore_alpha = 0.5,
  blur = true,
  blur_popups = true,
})
```

### `Noctalia-Shell` Settings Window Rule

Configure the settings window appearance:

```lua
-- Noctalia Settings
hl.window_rule({
  match = { class = "dev.noctalia.Noctalia" },
  float = true,
  size = { 1080, 920 },
})
```

> 💡 **Additional Configuration:** Check out the official [`Noctalia-Shell` Wiki](https://docs.noctalia.dev/noctalia/compositor-settings/hyprland/) for additional window appearance and blur configuration options.

---

## Apply Changes

**Restart your `Hyprland` session to see all changes take effect.**

For a quick restart without logging out:
```bash
hyprctl reload
```

---

## Related Guides

* [**Wiki Home**](../README.md) — Complete PikaOS documentation hub