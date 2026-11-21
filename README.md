# PikaOS Documentation

---

## Table of Contents

- [Quick Start Pathways](#quick-start-pathways)
  - [New to Linux?](#new-to-linux)
  - [Gaming Focused](#gaming-focused)
  - [Power User / Advanced](#power-user--advanced)
- [Search & Navigation](#search--navigation)
  - [Quick Links by Topic](#quick-links-by-topic)
- [Getting Started](#getting-started)
- [Installation & Setup](#installation)
- [System Basics](#system-basics)
- [Hardware & Drivers](#hardware)
- [Gaming on PikaOS](#gaming)
- [Customization](#customization)
- [Technical Guides](#guides)
- [Troubleshooting](#troubleshooting)
- [Advanced & Internals](#advanced)
- [Getting Involved](#contributing)

---

## Quick Start Pathways

Choose your path based on your experience level and goals. Follow the recommended sequence for best results.

### New to Linux?

**Recommended reading order:**

1. **[Introduction](01-getting-started/01-intro.md)** — What PikaOS is and isn't
2. **[Editions Guide](01-getting-started/02-editions.md)** — Choose GNOME, Hyprland, or Niri
3. **[BIOS Checklist](01-getting-started/03-bios-checklist.md)** — Prepare your hardware before install
4. **[Guided Installation](02-installation/04-guided-install.md)** — Safe, step-by-step setup
5. **[Post-Install Setup](02-installation/05-post-install-setup.md)** — Essential first steps
6. **[PikaOS Welcome App](03-system-basics/04-pika-welcome.md)** — Configure your system

**Then explore:**
- [Package Management with Pikman](03-system-basics/01-pikman-cli.md)
- [System Basics Overview](#system-basics)

---

### Gaming Focused

**Recommended reading order:**

1. **[Gaming on PikaOS](05-gaming/01-gaming-on-pikaos.md)** — Complete gaming overview
2. **[Proton Version Guide](05-gaming/01-gaming-on-pikaos.md#which-proton-version-should-i-use)** — Choose your compatibility layer
3. **[Install Gaming Tools](05-gaming/01-gaming-on-pikaos.md#quick-start)** — One-command setup
4. **[Gamescope Guide](05-gaming/01-gaming-on-pikaos.md#gamescope)** — Resolution and scaling control
5. **[Driver Setup](04-hardware-and-drivers/01-nvidia-drivers.md)** — See [Hardware & Drivers](#hardware) for GPU-specific guides

**Then explore:**
- [NVIDIA DLSS Switcher](05-gaming/04-nvidia-dlss-switcher.md)
- [AMD FSR4 Switcher](05-gaming/05-amd-fsr4-switcher.md)
- [Falcon GameMode](05-gaming/03-falcon-gamemode.md)

---

### Power User / Advanced

**Recommended reading order:**

1. **[What PikaOS Changes from Debian](09-advanced-and-internals/01-what-pikaos-changes-from-debian.md)** — Understand the differences
2. **[Kernel Manager](03-system-basics/05-kernel-manager.md)** — Switch kernel versions safely
3. **["Btrfs with Snapper](07-guides/05-snapper-btrfs.md)** — Snapshot-based system protection
4. **[Secure Boot Setup](07-guides/04-secure-boot.md)** — Enable secure boot on your machine

**Then explore:**
- [Chroot from Live ISO](07-guides/06-chrooting-from-a-live-iso.md)
- [Customizing Post-Install](02-installation/05-post-install-setup.md#advanced-customization)
- [Default Configuration](09-advanced-and-internals/02-default-configuration.md)

---

## Search & Navigation

### Quick Links by Topic

#### Installation & Setup
| Document | Description |
|----------|-------------|
| [Creating Install Media](02-installation/02-creating-install-media.md) | Make bootable USB on Windows, macOS, or Linux |
| [Booting the Installer](02-installation/03-booting-the-installer.md) | Troubleshoot boot issues and secure boot |
| [Guided Installation](02-installation/04-guided-install.md) | Step-by-step automated partitioning guide |
| [Post-Install Setup](02-installation/05-post-install-setup.md) | Essential first steps after installation |
| [Dual Boot Windows](02-installation/06-dual-boot-windows.md) | Install alongside existing Windows system |

#### Package Management
| Document | Description |
|----------|-------------|
| [Pikman CLI](03-system-basics/01-pikman-cli.md) | Command-line package management tool |
| [Pikman GUI](03-system-basics/02-pikman-gui.md) | Graphical interface for software management |
| [Repositories](03-system-basics/03-repositories.md) | Configure and manage software sources |

#### Hardware & Drivers
| Document | Description |
|----------|-------------|
| [NVIDIA Drivers](04-hardware-and-drivers/01-nvidia-drivers.md) | Install and configure NVIDIA graphics |
| [Intel/AMD Drivers](04-hardware-and-drivers/02-intel-amd-drivers.md) | Open-source driver setup for integrated graphics |
| [Legacy 580 Setup](04-hardware-and-drivers/03-nvidia-580-legacy-setup.md) | GTX 580 legacy GPU configuration |

#### Gaming
| Document | Description |
|----------|-------------|
| [Gaming Overview](05-gaming/01-gaming-on-pikaos.md) | Complete gaming documentation and setup |
| [Proton Guide](05-gaming/01-gaming-on-pikaos.md#which-proton-version-should-i-use) | Choose the right compatibility layer for your games |
| [Gamescope](05-gaming/01-gaming-on-pikaos.md#gamescope) | Resolution scaling and VRR control |
| [DLSS Switcher](05-gaming/04-nvidia-dlss-switcher.md) | Toggle NVIDIA DLSS per-game automatically |
| [FSR4 Switcher](05-gaming/05-amd-fsr4-switcher.md) | Enable AMD FSR4 upscaling per-game |

#### System Configuration
| Document | Description |
|----------|-------------|
| [PikaOS Welcome](03-system-basics/04-pika-welcome.md) | First-run configuration assistant |
| [Kernel Manager](03-system-basics/05-kernel-manager.md) | Switch between kernel versions safely |
| [Device Manager](03-system-basics/07-pikaos-device-manager.md) | Hardware detection and management |
| [PikaPaste](03-system-basics/06-pika-paste.md) | Securely share logs and command output |

#### Technical Guides
| Document | Description |
|----------|-------------|
| [BTRFS with Snapper](07-guides/05-snapper-btrfs.md) | Snapshot-based system protection and rollback |
| [Secure Boot](07-guides/04-secure-boot.md) | Enable secure boot on your machine |
| [3rd Party Repositories](07-guides/01-3rd-party-debian-repos.md) | Safely add external repositories to your system |
| [Automount Disks](07-guides/02-automount-disks.md) | Configure automatic disk mounting at boot |
| [CUPS Printers](07-guides/03-cups-printers.md) | Set up printing and scanner support |

#### Troubleshooting
| Document | Description |
|----------|-------------|
| [Common Steps](08-common-faults/01-common-troubleshooting-steps.md) | First steps for diagnosing any issue |
| [Booster SCSI LUKS Crash](08-common-faults/03-booster-scsi-luks-crash.md) | Boot failure workaround and fix |
| [GTK3 Themes Don't Stick](08-common-faults/04-gtk3-themes-dont-stick.md) | Theme persistence fix for GTK apps |
| [KWin RA24 Freezing](08-common-faults/05-kwin-ra24-freezing.md) | Wayland compositor freeze resolution |
| [LACT Stuttering](08-common-faults/06-lact-stuttering.md) | Fan control stutter fix and workaround |
| [NVIDIA GTK GSK Crash](08-common-faults/07-nvidia-gtk-gsk-crash.md) | Application crash resolution for NVIDIA users |
| [Suspend Wake Fix](08-common-faults/08-suspend-wake-fix.md) | Resume from sleep issues and fixes |

---

## Getting Started

> **Introduction to PikaOS** — Learn about PikaOS features, editions, and prepare your system with our [BIOS Checklist](01-getting-started/03-bios-checklist.md).
>
> **Desktop Editions** — Choose the right desktop environment for your needs.

---

## Installation & Setup

> **Installation Overview** — Different installation methods and approaches available for PikaOS.
>
> **Quick Links:**
> - [Creating Install Media](02-installation/02-creating-install-media.md) — USB drives on any OS
> - [Booting the Installer](02-installation/03-booting-the-installer.md) — Boot successfully from media
> - [Guided Installation](02-installation/04-guided-install.md) — Step-by-step process
> - [Post-Install Setup](02-installation/05-post-install-setup.md) — Configure your new system
> - [Dual Boot with Windows](02-installation/06-dual-boot-windows.md) — Install alongside Windows

> **[Update & Maintain](03-system-basics/01-pikman-cli.md)** — Maintaining your PikaOS system with regular updates.

---

## System Basics

> **Package Management** — Manage software with [Pikman CLI](03-system-basics/01-pikman-cli.md) or the graphical interface.
>
> **Key Tools:**
> - [Pikman GUI](03-system-basics/02-pikman-gui.md) — Graphical package management
> - [Repositories](03-system-basics/03-repositories.md) — Configure software sources
> - [PikaOS Welcome App](03-system-basics/04-pika-welcome.md) — First-run configuration
> - [Kernel Manager](03-system-basics/05-kernel-manager.md) — Manage kernel versions
> - [PikaPaste](03-system-basics/06-pika-paste.md) — Share logs securely
> - [Device Manager](03-system-basics/07-pikaos-device-manager.md) — Hardware detection
>
> **Additional Resources:** See [System Basics](../03-system-basics/) for complete tool documentation

> **[System Configuration](09-advanced-and-internals/02-default-configuration.md)** — Advanced system configuration and customization options.

---

## Hardware & Drivers

> **NVIDIA Graphics** — Complete guide for NVIDIA GPU setup and optimization.
>
> **Modern GPUs (580+):** [Setup Guide](04-hardware-and-drivers/01-nvidia-drivers.md)
> **Legacy GPUs (570-):** [Legacy Setup](04-hardware-and-drivers/03-nvidia-580-legacy-setup.md)

> **Intel & AMD Graphics** — Open-source driver information and setup for integrated graphics.

> **[Storage & Peripherals](07-guides/02-automount-disks.md)** — Storage configuration and peripheral device support.

---

## Gaming on PikaOS

> **Quick Start** — Get gaming with [complete gaming setup guide](05-gaming/01-gaming-on-pikaos.md).
>
> **Essential Tools:**
> - **Launchers:** Steam, Heroic, Lutris, Faugus Launcher
> - **Optimization:** ProtonPlus, GOverlay, MangoHud, Gamescope
> - **Installation:** `pikman i pika-gameutils-meta`
>
> **Performance Optimization:**
> - [falcond](05-gaming/02-falcond.md) — Automatic game optimization daemon
> - [Falcon Gamemode](05-gaming/03-falcon-gamemode.md) — Manual performance control
>
> **Graphics Enhancements:**
> - [NVIDIA DLSS Switcher](05-gaming/04-nvidia-dlss-switcher.md) — Update DLSS versions automatically
> - [AMD FSR4 Switcher](05-gaming/05-amd-fsr4-switcher.md) — Enable FSR4 upscaling
>
> **Configuration Guides:**
> - [Proton Versions Guide](05-gaming/01-gaming-on-pikaos.md#proton-guide) — Choose the right Proton build
> - [Launch Commands Reference](05-gaming/01-gaming-on-pikaos.md#launch-commands) — Customize game startup
> - [Gamescope Guide](05-gaming/01-gaming-on-pikaos.md#gamescope) — Resolution and scaling control
>
> **Optimization:**
> - [Shader Pre-caching](05-gaming/01-gaming-on-pikaos.md#shader-pre-caching) — Reduce stutter and loading times
> - [Shader Cache Size](05-gaming/01-gaming-on-pikaos.md#shader-cache-size) — Optimize for large games
>
> **Troubleshooting:** See the [Proton Logging section](05-gaming/01-gaming-on-pikaos.md#troubleshooting-proton).

---

## Customization

> **GNOME Layouts** — Customize the GNOME desktop environment with various layout options.

> **System Settings** — Advanced system settings and preferences configuration.

---

## Technical Guides

> **Security & Boot**
> - [Secure Boot Setup Guide](07-guides/04-secure-boot.md) — Complete step-by-step setup
> - [Third-Party Debian Repositories](07-guides/01-3rd-party-debian-repos.md) — Add external repositories safely

> **Storage & Filesystems**
> - [Automount Disks](07-guides/02-automount-disks.md) — Manage disk mounts and partitions
> - [Snapper Btrfs Snapshots](07-guides/05-snapper-btrfs.md) — Automatic system snapshots

> **Printers & Scanners**
> - [CUPS Printer Stack](07-guides/03-cups-printers.md) — Install and configure printer support

> **System Repair**
> - [Chroot from Live ISO](07-guides/06-chrooting-from-a-live-iso.md) — Repair system from live environment

> **Desktop Environments**
> **Hyprland:**
> - [Hyprland Setup Guide](07-guides/08-hyprland-guide.md) — Configure Hyprland compositor
> - [Noctalia Shell for Hyprland](07-guides/09-noctalia-hyprland.md)
> - [Otter-Shell for Hyprland](07-guides/10-otter-shell-hyprland.md)
>
> **Niri:**
> - [Niri Setup Guide](07-guides/11-niri-guide.md) — Configure Niri desktop environment
> - [Noctalia Shell for Niri](07-guides/12-noctalia-niri.md)
> - [Otter-Shell for Niri](07-guides/13-otter-shell-niri.md)

> **Containers & Virtualization**
> - [Winboat (Windows Containers)](07-guides/07-winboat.md) — Run Windows apps in containers

---

## Troubleshooting

> **Common Faults**
> - [General Diagnostic Procedures](08-common-faults/01-common-troubleshooting-steps.md)
> - [Blender Title Bars (Wayland)](08-common-faults/02-blender-title-bars.md)
> - [Booster SCSI/LUKS Crash](08-common-faults/03-booster-scsi-luks-crash.md)
> - [GTK3 Themes Not Visible](08-common-faults/04-gtk3-themes-dont-stick.md)
> - [KWin Freezing (AMD RA24)](08-common-faults/05-kwin-ra24-freezing.md)
> - [LACT Fan Control Stuttering](08-common-faults/06-lact-stuttering.md)
> - [NVIDIA GTK/GSK Crash](08-common-faults/07-nvidia-gtk-gsk-crash.md)
> - [Suspend/Wake Issues](08-common-faults/08-suspend-wake-fix.md)
>
> **Gaming Troubleshooting:** See the [Proton Logging section](05-gaming/01-gaming-on-pikaos.md#troubleshooting-proton).

---

## Advanced & Internals

> **System Deep Dive**
> - [What PikaOS Changes from Debian](09-advanced-and-internals/01-what-pikaos-changes-from-debian.md) — System modifications overview
> - [Default Configuration](09-advanced-and-internals/02-default-configuration.md) — Default system settings
> - [Bootloader & Initramfs](09-advanced-and-internals/03-bootloader-and-initramfs.md) — Technical bootloader details
> - [Additions to Debian](09-advanced-and-internals/04-additions.md) — Additional packages and tools

---

## Getting Involved

> **Contribute to PikaOS** — Help make PikaOS better by contributing to the project.
>
> **Ways to contribute:**
> - [Getting Involved Overview](10-getting-involved/01-overview.md) — All ways to participate
> - [Documentation Guidelines](10-getting-involved/02-documentation-guidelines.md) — Write documentation for PikaOS
> - [Translation with Weblate](11-contributing/01-translate-weblate.md) — Localize PikaOS
> - [Feedback & Support](11-contributing/02-feedback.md) — Report issues and suggest improvements
>
> **Community:** Join our community channels to connect with other users and developers. See the [Getting Involved Overview](10-getting-involved/01-overview.md) for links.
