# Noctalia-Shell V5 guide for Niri

## Niri configuration guide

### Backup

> Optionally before editing configuration files backup your previous configuration located in:

- **~/.config/niri/config.kdl**

## Install the noctalia package

```bash
pikman install noctalia
```

## Deactivate Otter-shell and add Noctalia

Open `~/.config/niri/config.kdl`.

**Remove or comment out (`//`) the Otter-shell items**

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

> **Note:**
>
> **-If you disable `otter-polkit` you will have to enable Polkit-Agent in the Noctalia settings**
>
> (Settings: Security / Authentication / Polkit Agent)
>
> **-If you disable `otter-idle` you will have to enable idle in the Noctalia settings:**
>
> (screenoff / idle / lock and suspend)

**Add the following line**

```kdl
spawn-at-startup "noctalia"
```

## Configure the Keybinds

### Delete or comment `//` the following otter-shell keybinds

```kdl
Super+Alt+L { spawn "otter-lock"; }
Mod+O { toggle-overview; }
```

### Launcher

**Remove or comment out the old keybind**

```kdl
Mod+D { spawn "otter-launcher"; }
```

**Add and adjust the new keybind:**

```kdl
Mod+D { spawn-sh "noctalia msg panel-toggle launcher"; }
```

## Optional core Noctalia keybinds

**You can add and adjust these to your liking**

### Control center

```kdl
Mod+S { spawn-sh "noctalia msg panel-toggle control-center"; }
```

### Settings

```kdl
Mod+Comma { spawn-sh "noctalia msg settings-toggle"; }
```

### Window switcher

Niri also has a built-in window switcher, you can choose which one you prefer.

```kdl
Alt+Tab { spawn-sh "noctalia msg window-switcher"; }
```

### Audio

**Replace**

```kdl
XF86AudioRaiseVolume allow-when-locked=true repeat=true { spawn "otter-osd" "volume-up" "5"; }
XF86AudioLowerVolume allow-when-locked=true repeat=true { spawn "otter-osd" "volume-down" "5"; }
XF86AudioMute        allow-when-locked=true { spawn "otter-osd" "volume-mute-toggle"; }
```

With

```kdl
XF86AudioRaiseVolume { spawn-sh "noctalia msg volume-up"; }
XF86AudioLowerVolume { spawn-sh "noctalia msg volume-down"; }
XF86AudioMute { spawn-sh "noctalia msg volume-mute"; }
```

### Brightness

**Replace**

```kdl
XF86MonBrightnessUp   allow-when-locked=true repeat=true { spawn "otter-osd" "brightness-up" "5"; }
XF86MonBrightnessDown allow-when-locked=true repeat=true { spawn "otter-osd" "brightness-down" "5"; }
```

With

```kdl
XF86MonBrightnessUp { spawn-sh "noctalia msg brightness-up"; }
XF86MonBrightnessDown { spawn-sh "noctalia msg brightness-down"; }
```

## Set Up Noctalia wallpaper and overview

To ensure the wallpaper layer renders correctly, adjust the layer-rule from `match namespace="^otter-wallpaper$"` to:

```kdl
layer-rule {
    match namespace="^noctalia-backdrop"
    place-within-backdrop true
}
```

> Check out the official Noctalia V5 Wiki for additional background and overview configuration options.
>
> <https://docs.noctalia.dev/noctalia/compositor-settings/niri/>

## Extra compositor settings

Put this all the way at the bottom of your config.kdl, it allows notification actions and window activation from Noctalia.

```kdl
debug {
    honor-xdg-activation-with-invalid-serial
}
```

**Restart your session to see the changes.**
