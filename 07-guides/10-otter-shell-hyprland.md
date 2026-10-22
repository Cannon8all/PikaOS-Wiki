# Otter-Shell installation guide for Hyprland (deprecated)

## Install Otter-Shell

Install the core shell.

```bash
pikman i otter-shell
```

## Backup Configuration

> Before making changes, back up your existing configuration directory located at: ~/.config/hypr/

## Deactivate Default Modules

In `~/.config/hypr/exec.conf` remove or comment out the following lines to disable the default Pikabar/Noctalia shell components:

| Remove or //                                       |
| -------------------------------------------------- |
| `exec-once=systemctl --user enable --now hypridle` |
| `exec-once=/usr/bin/mate-polkit`                   |
| `exec-once=swww-daemon`                            |
| `exec-once=pikabar`                                |

## Add the Otter-Shell Autostart Modules

Add these lines to your `exec.conf` to ensure the Otter-Shell modules start at boot:

| Daemon                                              | Required    | Purpose                                                     |
| --------------------------------------------------- | ----------- | ----------------------------------------------------------- |
| `exec-once=otter-bar`                               | Recommended | Status bar, system tray, workspace indicator                |
| `exec-once=otter-wallpaper`                         | Recommended | Desktop background                                          |
| `exec-once=otter-notifications`                     | Recommended | `notify-send` and app notifications                         |
| `exec-once=otter-osd`                               | Recommended | Volume/brightness/lock-key overlays                         |
| `exec-once=otter-idle`                              | Recommended | Screen lock and DPMS on idle                                |
| `exec-once=otter-polkit`                            | Recommended | Authentication for privileged actions                       |
| `exec-once=otter-clip daemon`                       | Recommended | Clipboard history                                           |
| `exec-once=otter-theme-gen`                         | Optional    | Wallpaper-reactive color layer (use with `otter-wallpaper`) |
| `exec-once=otter-search`                            | Optional    | File and content search (launcher file / grep modes)        |
| `exec-once=otter-weather --watch 900 --write-cache` | Optional    | Bar weather widget data                                     |
| `exec-once=otter-jade`                              | Optional    | Desktop pet                                                 |
| `exec-once=otter-transcribe`                        | Optional    | Speech transcription (needs `otter-shell-extras`)           |
| `exec-once=otter-assist`                            | Optional    | Local AI backend for Otter Assistant (`otter-shell-extras`) |

## Configure keybinds

Configure your primary navigation and session shortcuts. You can adjust these keys to suit your preference.

The following keybinds can be used as an example.

**Edit** `~/.config/hypr/keybinds.conf`

### Launcher

**Change**

```ini
bind=$mainMod,d,exec,pikabar-launcher
```

**Into**

```ini
bind=$mainMod, d, exec, pkill otter-launcher || otter-launcher
```

### Logout

**Add**

```ini
bind=CTRL ALT, Delete, exec, pkill otter-logout || otter-logout
```

### Screenshot

**Delete** all 5 lines at the bottom of the config from:

bind=CTRL,Print,exec,grim...

This Keybind will use **PrtScn** and save screenshots to the clipboard

**Add**

```ini
bind = , Print, exec, otter-screenshot
```

This keybind will use **Shift+PrtScn** and save screenshots to the Pictures folder

**Add**

```ini
bind = SHIFT, Print, exec, otter-screenshot --freeze --output ~/Pictures/screenshot.png
```

## Notifications and OSD

### Capslock and Numlock

**Add**

```ini
bindl = , Caps_Lock, exec, otter-osd caps-lock
bindl = , Num_Lock, exec, otter-osd num-lock
```

### Audio

**Replace the current 3 XF86Audio... keybinds**

```ini
bindle = , XF86AudioRaiseVolume, exec, otter-osd volume-up 5
bindle = , XF86AudioLowerVolume, exec, otter-osd volume-down 5
bindl = , XF86AudioMute, exec, otter-osd volume-mute-toggle
```

### Brightness

**Replace the current XF86MonBrightness... keybinds**

```ini
bindle = , XF86MonBrightnessUp, exec, brightnessctl set +5% && otter-osd brightness-up 5
bindle = , XF86MonBrightnessDown, exec, brightnessctl set 5%- && otter-osd brightness-down 5
```

> For laptops this could need additional parameters to make sure the correct backlight is controlled.
