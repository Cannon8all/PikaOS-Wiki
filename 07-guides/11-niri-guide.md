# How to use Niri on PikaOS

## Keybinds

```text
SUPER+Enter = Terminal
SUPER+D = Application Launcher
SUPER+Q = Close active program
SUPER+SHIFT+Q = logout/reboot/shutdown menu
SUPER+SHIFT+B = open browser
SUPER+SHIFT+F = open file manager
```

The full list can be found near the bottom of `~/.config/niri/config.kdl` - some helpful ones will also display on login.

## Configuration

To set your input keymap please change the layout from "us" in `~/.config/niri/config.kdl`

Please set your monitor resolutions etc and scaling in `~/.config/niri/config.kdl`

To change the location for weather or set it to ~~heathen~~ american mode edit `~/.config/pikabar/config.json`

There is a bunch of other config in that niri config you can edit, including wallpaper etc.

## How do I modify pikabar without it getting overwritten on updates?

The way it is setup is it is meant to get updates without requiring users to manually apply them.

If however you want to heavily customize then you are best doing the following:

> Copy the contents of /usr/share/pikabar into ~/.config/quickshell
> Then update ~/.config/niri/config.kdl and replace pikabar with quickshell

## How do I convert my existing install to Niri?

Do note side by side installs are not officially supported by the PikaOS team, for the best experience please use the Niri ISO.

1. If you don't already have a ~/.config/niri folder, make one: `mkdir ~/.config/niri`.

   - You'll find Niri's `config.kdl` here after install.

2. If you currently use Hyprland you will need to uninstall its settings package or you will overwrite your settings with the defaults.

3. Execute the following from the terminal depending on GPU:

   - _**Non-Nvidia users:**_

   ```bash
   pikman update && pikman install pika-niri-desktop-minimal pika-niri-settings
   ```

   - _**Nvidia users:**_

   ```bash
   pikman update && pikman install pika-niri-desktop-minimal pika-niri-settings-nvidia
   ```

4. On reboot, select _Niri_ from the login screen (small cog at bottom right if prior install was GNOME)
