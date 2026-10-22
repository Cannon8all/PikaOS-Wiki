# GTK3 Themes don't stick in GNOME

## Problem

The GTK3 Theme I set keeps randomly changing/resetting.

## Cause

This is due to the `Legacy (GTK3) Theme Scheme Auto Switcher` extension, it allows the GTK3 theme to sync with the Libadwaita Dark/Light mode, this however isn't compatible with out-of-spec themes such as Whitesur.

## Solution

Simply disable `Legacy (GTK3) Theme Scheme Auto Switcher` from the extension manager

![extension-manager-disable-gtk3-switcher.png](/extension-manager-disable-gtk3-switcher.png)
