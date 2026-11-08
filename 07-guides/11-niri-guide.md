# Using Niri on PikaOS - Complete Guide

---

## Table of Contents

- [Default Keybindings](#default-keybindings)
- [Configuration Guide](#configuration-guide)
  - [Input Keymap Settings](#input-keymap-settings)
  - [Monitor Configuration](#monitor-configuration)
  - [Pikabar Settings](#pikabar-settings)
- [Modifying Pikabar Safely](#modifying-pikabar-safely)
  - [Safe Customization Method](#safe-customization-method)
- [Converting Existing Installation to Niri](#converting-existing-installation-to-niri)
  - [Conversion Steps](#conversion-steps)
    - [Step 1: Create Niri Configuration Directory](#step-1-create-niri-configuration-directory)
    - [Step 2: Remove Conflicting Settings (If Using Hyprland)](#step-2-remove-conflicting-settings-if-using-hyprland)
    - [Step 3: Install Niri Desktop Environment](#step-3-install-niri-desktop-environment)
      - [Non-NVIDIA Users](#non-nvidia-users)
      - [NVIDIA Users](#nvidia-users)
    - [Step 4: Select Niri at Login](#step-4-select-niri-at-login)
- [Troubleshooting](#troubleshooting)
  - [Niri Doesn't Start After Installation?](#niri-doesnt-start-after-installation)
  - [Display Issues on NVIDIA GPU?](#display-issues-on-nvidia-gpu)
- [Related Guides](#related-guides)

---

`Niri` is a dynamic tiling `Wayland` compositor designed for simplicity and elegance. This comprehensive guide covers keybindings, configuration, installation, and customization options.

---

## Default Keybindings

| Key Combination | Action |
| :--- | :--- |
| `SUPER + Enter` | Open terminal emulator |
| `SUPER + D` | Launch application launcher |
| `SUPER + Q` | Close active program/window |
| `SUPER + SHIFT + Q` | Logout/reboot/shutdown menu |
| `SUPER + SHIFT + B` | Open web browser |
| `SUPER + SHIFT + F` | Open file manager |

> 💡 **Tip:** The full list of keybindings can be found near the bottom of `~/.config/niri/config.kdl`. Some helpful ones will also display on login.

---

## Configuration Guide

### Input Keymap Settings

**To configure your keyboard layout, edit the following file:**

`~/.config/niri/config.kdl`

Change the `layout` setting from `us` to your preferred locale (e.g., `de`, `fr`, `es`).

### Monitor Configuration

**Set your monitor resolutions, refresh rates, and scaling factors in:**

`~/.config/niri/config.kdl`

Common settings include:
- Resolution (e.g., `1920x1080`)
- Refresh rate (e.g., `60Hz`, `144Hz`)
- Scale factor for high-`DPI` displays (`scale 1.5` or `scale 2`)

### Pikabar Settings

**To change weather location or temperature units (`imperial`/`Metric`):**

Edit the configuration file:
`~/.config/pikabar/config.json`

> 💡 **Tip:** `Niri` includes extensive customization options in its config file. Explore settings for wallpaper, animations, and behavior tweaks.

---

## Modifying Pikabar Safely

`Pikabar` is designed to receive updates without requiring manual intervention. However, if you need deep customization, follow this safe approach:

### Safe Customization Method

1. **Copy base configuration:**
   ```
cp -r /usr/share/pikabar ~/.config/quickshell
```

2. **Update `Niri` config** to use quickshell instead of `pikabar`:
   Edit `~/.config/niri/config.kdl` and replace the `pikabar` startup command with quickshell.

3. **Customize your copy:**
   All modifications are now in `~/.config/quickshell` and won't be overwritten by updates.

> ⚠️ **Warning:** Directly modifying files in `/usr/share/pikabar` will cause issues during system updates. Always use the user configuration directory instead.

---

## Converting Existing Installation to Niri

**Note:** Side-by-side installs are not officially supported by the `PikaOS` team. For the best experience, please use the dedicated **`Niri ISO`**.

### Conversion Steps

#### Step 1: Create Niri Configuration Directory

If you don't already have a `~/.config/niri` folder, create one:

```
mkdir ~/.config/niri
```

> 💡 **Tip:** You'll find `Niri`'s `config.kdl` here after installation. This is where all your customizations will be stored.

#### Step 2: Remove Conflicting Settings (If Using Hyprland)

**If you currently use `Hyprland`, uninstall its settings package to prevent conflicts:**

```
# Remove `Hyprland` configuration that may overwrite `Niri` settings
pikman remove pika-hyprland-settings
```

#### Step 3: Install Niri Desktop Environment

**Execute the following command from the terminal, depending on your `GPU` type:**

##### Non-NVIDIA Users

```
pikman update && pikman install pika-niri-desktop-minimal pika-niri-settings
```

##### NVIDIA Users

```
pikman update && pikman install pika-niri-desktop-minimal pika-niri-settings-nvidia
```

> ⚠️ **Warning:** Ensure you select the correct package variant for your `GPU` to avoid display issues.

#### Step 4: Select `Niri` at Login

**On reboot, select `Niri` from the login screen:**

- Look for a small **cog icon** at the bottom right (if prior install was `GNOME`)
- Click it and choose **`Niri`** from the session list

---

## Troubleshooting

### `Niri` Doesn't Start After Installation?

Check for configuration errors:

```
# Test configuration syntax
niri --check-config ~/.config/niri/config.kdl

# Check logs
journalctl -xe | grep niri
```

### Display Issues on `NVIDIA` `GPU`?

Ensure you installed the correct `NVIDIA` variant:
```
pikman install pika-niri-desktop-minimal pika-niri-settings-nvidia
```

Then reboot and select `Niri` at login.

---

## Related Guides

* [**Wiki Home**](../README.md) — Complete PikaOS documentation hub