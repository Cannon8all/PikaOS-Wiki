# PikaOS Welcome — First-Boot Setup Assistant

---

## Table of Contents

- [Key Features](#key-features)
  - [Setup Steps](#setup-steps)
- [Recommended Additions](#recommended-additions)
  - [Gaming Essentials](#gaming-essentials)
  - [Hardware Support](#hardware-support)
- [Other Stuff](#other-stuff)
- [Related Guides](#related-guides)

---

> 💡 **Overview:** The PikaOS Welcome App is a `Rust`-based `GTK4` + `Libadwaita` application that streamlines the setup process for new users. It provides a curated, centralized experience to configure your desktop environment quickly—no terminal required (unless you prefer it).

**Key Benefits:**
- Never miss critical drivers or codecs
- Install gaming tools and configure peripherals easily
- No need to dig through documentation or wonder what you forgot

> ⚙️ **Default Behavior:** The Welcome App opens automatically at each startup for new users. Disable this by unchecking the `Show on startup` box in the top-left corner of the window.

---

## Key Features

### Setup Steps

Quickly install, configure, and maintain essential components:

| Task | Description |
| :--- | :--- |
| **Update My System** | Launches the `pikman` Update Manager to update all installed packages |
| **Install Patented Media Codecs and Libraries** | Adds `FFMPEG`, `VA-API`, and more for out-of-box video/audio playback |
| **Setup Printer Support** | Installs `CUPS` and printer drivers (excluded by default for security) |
| **Open Driver Manager** | Install proprietary `NVIDIA` drivers, CPU microcode, and more with one click |
| **Open Kernel Manager** | Switch between kernel versions and schedulers for performance tuning |
| **Software Manager Access** | Launch the PikaOS Software Manager to explore and install packages |
| **Install WebApps** | Run web apps (`Spotify`, Discord, etc.) as native windows using your browser |

> 💡 **Tip:** Each task is designed to be completed in any order based on your needs. You can return to complete remaining steps later.

---

## Recommended Additions

Hand-picked tools and packages for gamers and creative professionals:

### Gaming Essentials
| Package | Purpose |
| :--- | :--- |
| **PikaOS Game Utilities** | One-click install for `Steam`, `Lutris`, `MangoHud`, `VKBasalt`, `Wine`, `Winetricks`, and more |
| **Game Utilities Extras** | Additional launchers: `Heroic Games Launcher` and `Bottles` |

### Hardware Support
| Package | Purpose |
| :--- | :--- |
| **Device Configs for Controllers & VR Gear** | Udev rules for HID gamepads, VR devices, and specialty controllers |

> 💡 **Tip:** These additions are optional but highly recommended for an optimal gaming experience.

---

## Other Stuff

The Welcome App includes additional features to explore:

- Custom configuration options
- Advanced setup tools
- Quick access to system utilities

> ℹ️ **Info:** The Welcome App is designed to be intuitive and user-friendly. All major setup tasks are accessible through the graphical interface.

---

## Related Guides

* [**Pikman CLI Guide**](01-pikman-cli.md) — Command-line package management
* [**Pikman GUI**](02-pikman-gui.md) — Graphical software manager for package management
* [**Kernel Manager**](05-kernel-manager.md) — Switch between kernel versions safely
* [**Gaming on PikaOS**](../05-gaming/01-gaming-on-pikaos.md) — Gaming setup and Proton guides
* [**NVIDIA Drivers**](../04-hardware-and-drivers/01-nvidia-drivers.md) — GPU driver installation guide
* [**PikaOS Device Manager**](07-pikaos-device-manager.md) — Driver management interface