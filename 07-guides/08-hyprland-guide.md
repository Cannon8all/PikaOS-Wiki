# PikaOS Hyprland Guide

---

## Table of Contents

- [Default Keybindings](#default-keybindings)
  - [Configuration Tips](#configuration-tips)
- [Modifying Pikabar Safely](#modifying-pikabar-safely)
  - [Safe Customization Method](#safe-customization-method)
- [Troubleshooting](#troubleshooting)
  - [Hyprland Won't Start?](#hyprland-wont-start)
  - [Pikabar Not Showing?](#pikabar-not-showing)
- [Related Guides](#related-guides)

---

`Hyprland` is a dynamic tiling `Wayland` compositor included in `PikaOS`. This guide covers essential keybindings, configuration tips, and customization options.

---

## Default Keybindings

| Key Combination | Action |
| :--- | :--- |
| `SUPER + Enter` | Open terminal emulator |
| `SUPER + D` | Launch application launcher |
| `SUPER + Q` | Close active window/program |
| `SUPER + SHIFT + Q` | Logout/reboot/shutdown menu |
| `SUPER + N` | Show notifications panel |
| `SUPER + SHIFT + B` | Open web browser |
| `SUPER + SHIFT + F` | Open file manager |

> 💡 **Tip:** View all available keybindings in `~/.config/hypr/keybinds.conf`. Many more are configured beyond the essential ones listed above.

---

## Configuration Tips

### Disable Welcome App on Boot

To prevent the `PikaOS` Welcome app from launching automatically:

1. Open `~/.config/hypr/exec.conf`
2. Remove or comment out the line referencing the welcome application

> 💡 **Tip:** Use a text editor like `nano` or `vim` to edit configuration files in the terminal.

### `NVIDIA` Users (Non-`NVIDIA` `ISO`)

If you're using an `NVIDIA` `GPU` with the standard `ISO`, you may need to adjust environment variables:

1. Open `~/.config/hypr/env.conf`
2. Remove or comment out the **`NVIDIA`-specific section** at the bottom once booted into your installed system

### Display Configuration

Set your monitor resolutions and scaling factors in:

`~/.config/hypr/monitors.conf`

> 💡 **Tip:** Common settings include resolution, refresh rate, and scale factor for high-`DPI` displays.

### Customize Pikabar Settings

Modify weather location or temperature units (`imperial`/`Metric`):

1. Edit `~/.config/pikabar/config.json`
2. Adjust the appropriate fields for your region preferences

---

## Modifying Pikabar Safely

**Pikabar is designed to receive updates without requiring manual intervention.** However, if you need deep customization, follow this approach:

### Safe Customization Method

1. **Copy base configuration:**
   ```bash
   cp -r /usr/share/pikabar ~/.config/quickshell
   ```

2. **Update exec.conf** to use quickshell instead of pikabar:
   Edit `~/.config/hypr/exec.conf` and replace the pikabar startup command with quickshell.

3. **Customize your copy:**
   All modifications are now in `~/.config/quickshell` and won't be overwritten by updates.

> ⚠️ **Warning:** Directly modifying files in `/usr/share/pikabar` will cause issues during system updates. Always use the user configuration directory instead.

---

## Troubleshooting

### Hyprland Won't Start?

Check for configuration errors:

```bash
# Test configuration syntax
hyprctl --batch "-e reload"

# Check logs
journalctl -xe | grep hyprland
```

### Pikabar Not Showing?

Verify the process is running:

```bash
ps aux | grep pikabar
```

If not running, check `exec.conf` for startup errors.

---

## Related Guides

* [**Wiki Home**](../README.md) — Complete PikaOS documentation hub