# What PikaOS changes from Debian

## Modifications

- Debian console-data Replaced with KBD (Allows systemd-locale1 to enabled)
- systemd configured with KBD support, libxkbcommon, and locale1 fixed.
- mkinitramfs replaced with booster.
- Blender built with CUDA,OPTIX,HIP,HIPRT,ONEAPI, and many more.
- PPD replaced with tuned.
- OBS Studio built with Stream API Keys, and [a few patches](https://git.pika-os.com/multimedia-packages/obs-studio/src/branch/main/patches/series).
- GNOME: Replaced gnome-console with ptyxis.
- KDE: Replaced kdepartitionmanager with Gnome Disks.
- Replaced Debian's Kernel patches with CachyOS Kernel Patches.
- switcheroo patched with Jan's Patches and Nvidia vaapi driver patch.
- Debian's minimal hwdata replaced with full hwdata with -dev headers.
- grub replaced with refind.
- software-properties-gtk3 replaced with the APT Settings Page in Pikman Update Manager.
- and many many more...
