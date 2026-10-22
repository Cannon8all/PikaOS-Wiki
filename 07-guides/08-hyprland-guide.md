# PikaOS Hyprland Guide

## Keybinds

```text
SUPER+Enter = Terminal
SUPER+D = Application Launcher
SUPER+Q = Close active program
SUPER+SHIFT+Q = logout/reboot/shutdown menu
SUPER+N = show notifications
SUPER+SHIFT+B = open browser
SUPER+SHIFT+F = open file manager
```

There are many more so please check `~/.config/hypr/keybinds.conf` for them all.

## Configuration

To stop the welcome app starting on boot remove its line in `~/.config/hypr/exec.conf`

Non-Nvidia users using the nvidia iso may need to remove the bottom section labelled nvidia in `~/.config/hypr/env.conf` once they are booted into their install.

Please set your monitor resolutions etc and scaling in `~/.config/hypr/monitors.conf`

To change the location for weather or set it to ~~heathen~~ american mode edit `~/.config/pikabar/config.json`

There is a bunch of other config in that hypr folder you can edit, including wallpaper etc.

## How do I modify pikabar without it getting overwritten on updates?

The way it is setup is it is meant to get updates without requiring users to manually apply them.

If however you want to heavily customize then you are best doing the following:

> Copy the contents of /usr/share/pikabar into ~/.config/quickshell
> Then update ~/.config/hypr/exec.conf and replace pikabar with quickshell
