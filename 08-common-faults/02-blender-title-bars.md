# Blender missing title bars - GNOME

## Problem

Blender has an issue on GNOME that won't display the title bar on the main window and any popup window.

## Cause

Blender dropped libdecor support and GNOME doesn't support XDG Server Side Decorations.

## Solutions

#A - Wait till Blender finishes this fix: <https://projects.blender.org/blender/blender/pulls/148350>

#B - Use Terminal and launch blender in x11 mode with this cmd :

```bash
WAYLAND_DISPLAY="" blender & disown
```

The `disown` cmd is used to separate the application from the Terminal. That way you can close the terminal without closing the application in question.

#C - Install `menulibre` (shows as Menu Editor on the app launcher). Edit the Blender entry and add on the command line to force X11 mode:

```bash
env WAYLAND_DISPLAY= blender %f
```

![gnome_fix_blender_tittlebar_menu_editor.png](/screenshots/gnome_fix_blender_tittlebar_menu_editor.png)

#D - Edit directly the file on : `~/.local/share/applications/blender.desktop` with the following:

```ini
Exec=env WAYLAND_DISPLAY= blender %f
```
