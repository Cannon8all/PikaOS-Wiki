# PikaOS Documentation

**PikaOS is a gaming-focused Linux distribution built on Debian Sid.** It ships with the latest drivers, kernel, and gaming tools out of the box — so you can play Windows games immediately without spending hours configuring your system.

This wiki covers installation, setup, drivers, gaming, and troubleshooting. Choose a path below based on what you need, or browse the full documentation at the bottom.

---

## Choose Your Path

### 🐧 New to Linux?

Follow these steps in order. Each one builds on the previous — don't skip ahead.

0. **[Installation Overview](02-installation/01-overview.md)** — What you need before installing
1. **[Introduction](01-getting-started/01-intro.md)** — What PikaOS is and isn't
2. **[Editions Guide](01-getting-started/02-editions.md)** — Choose GNOME, KDE, Hyprland, Niri, or COSMIC
3. **[BIOS Checklist](01-getting-started/03-bios-checklist.md)** — Prepare your hardware before install (Secure Boot, CSM, SATA mode)
4. **[Preparing USB and Booting](02-installation/02-prepare-usb-and-boot.md)** — Write the ISO to USB and boot it
5. **[Guided Installation](02-installation/03-guided-install.md)** — Partition and install
6. **[Post-Install Setup](02-installation/04-post-install.md)** — First steps after your first boot
7. **[PikaOS Welcome App](03-system-basics/04-pika-welcome.md)** — Configure your system through the built-in setup wizard

**Already have Windows?** → [**Dual Boot Guide**](02-installation/06-dual-boot-windows.md) — Install PikaOS alongside Windows

**Older NVIDIA GPU (GTX 10 / 900 / 750 Ti)?** → [**NVIDIA 580 Legacy Driver Setup**](04-hardware-and-drivers/03-nvidia-580-legacy-setup.md) — Special driver package for legacy cards

---

### 🔧 Common Troubleshooting

Having a problem? Most common issues are covered here first.

- **[Common Troubleshooting Steps](08-common-faults/01-common-troubleshooting-steps.md)** — Quick-reference table for boot failures, greeter issues, keyboard problems, NVIDIA legacy cards, AMD KWin crashes, and more.
- **[How to Chroot from a Live ISO](07-guides/06-chrooting-from-a-live-iso.md)** — When nothing else works: mount your installed system from a live USB and repair it manually (fix broken updates, restore GRUB, reset passwords, and more).

---

### 🎮 Gaming Focused

1. **[Gaming on PikaOS](05-gaming/01-gaming-on-pikaos.md)** — Complete gaming overview, Proton versions, and launch commands
2. **[Install Gaming Tools](05-gaming/01-gaming-on-pikaos.md#quick-start)** — One-command setup: `pikman i pika-gameutils-meta`
3. **[Gamescope Guide](05-gaming/01-gaming-on-pikaos.md#gamescope)** — Resolution scaling and VRR control
4. **[Proton Version Guide](05-gaming/01-gaming-on-pikaos.md#which-proton-version-should-i-use)** — Choose the right compatibility layer
5. **[Driver Setup](04-hardware-and-drivers/01-nvidia-drivers.md)** — GPU-specific driver guides

**Then explore:**
- [falcond](05-gaming/02-falcond.md) — Automatic game optimization daemon
- [Falcon Gamemode](05-gaming/03-falcon-gamemode.md) — Manual performance control
- [NVIDIA DLSS Switcher](05-gaming/04-nvidia-dlss-switcher.md) — Update DLSS versions automatically
- [AMD FSR4 Switcher](05-gaming/05-amd-fsr4-switcher.md) — Enable FSR4 upscaling

---

### ⚙️ Power User / Advanced

1. **[What PikaOS Changes from Debian](09-advanced-and-internals/01-what-pikaos-changes-from-debian.md)** — Understand the differences
2. **[Kernel Manager](03-system-basics/05-kernel-manager.md)** — Switch kernel versions safely
3. **[Btrfs with Snapper](07-guides/05-snapper-btrfs.md)** — Snapshot-based system protection and rollback
4. **[Secure Boot Setup](07-guides/04-secure-boot.md)** — Enable secure boot on your machine

**Then explore:**
- [Chroot from Live ISO](07-guides/06-chrooting-from-a-live-iso.md) — Repair system from live environment
- [Default Configuration](09-advanced-and-internals/02-default-configuration.md) — Default system settings reference
- [Customizing Post-Install](02-installation/04-post-install.md) — Post-install configuration

---

## Browse All Documentation

### Installation & Setup
| Document | Description |
|----------|-------------|
| [Preparing USB and Booting](02-installation/02-prepare-usb-and-boot.md) | Write ISO to USB, verify checksum, boot the installer |
| [Guided Installation](02-installation/03-guided-install.md) | Step-by-step automated partitioning |
| [Post-Install Setup](02-installation/04-post-install.md) | First steps after installation |
| [Dual Boot Windows](02-installation/06-dual-boot-windows.md) | Install alongside Windows |

### Package Management
| Document | Description |
|----------|-------------|
| [Pikman CLI](03-system-basics/01-pikman-cli.md) | Command-line package management |
| [Pikman GUI](03-system-basics/02-pikman-gui.md) | Graphical software manager |
| [Repositories](03-system-basics/03-repositories.md) | Configure software sources |

### System Tools
| Document | Description |
|----------|-------------|
| [PikaOS Welcome App](03-system-basics/04-pika-welcome.md) | First-run configuration assistant |
| [Kernel Manager](03-system-basics/05-kernel-manager.md) | Switch between kernel versions |
| [Device Manager](03-system-basics/07-pikaos-device-manager.md) | Hardware detection and driver management |
| [PikaPaste](03-system-basics/06-pika-paste.md) | Securely share logs and command output |

### Hardware & Drivers
| Document | Description |
|----------|-------------|
| [NVIDIA Drivers](04-hardware-and-drivers/01-nvidia-drivers.md) | Install and configure NVIDIA graphics |
| [Intel/AMD Drivers](04-hardware-and-drivers/02-intel-amd-drivers.md) | Open-source driver setup |
| [Legacy 580 Setup](04-hardware-and-drivers/03-nvidia-580-legacy-setup.md) | GTX 580 legacy GPU configuration |

### Gaming
| Document | Description |
|----------|-------------|
| [Gaming Overview](05-gaming/01-gaming-on-pikaos.md) | Complete gaming documentation |
| [DLSS Switcher](05-gaming/04-nvidia-dlss-switcher.md) | Toggle NVIDIA DLSS per-game |
| [FSR4 Switcher](05-gaming/05-amd-fsr4-switcher.md) | Enable AMD FSR4 upscaling |

### Customization
| Document | Description |
|----------|-------------|
| [GNOME Layouts](06-customization/01-gnome-layouts.md) | Switch between Windows, macOS, Unity, and GNOME desktop layouts |

### Technical Guides
| Document | Description |
|----------|-------------|
| [Secure Boot](07-guides/04-secure-boot.md) | Enable secure boot |
| [3rd Party Repositories](07-guides/01-3rd-party-debian-repos.md) | Safely add external repositories |
| [Automount Disks](07-guides/02-automount-disks.md) | Configure automatic disk mounting |
| [Snapper Btrfs Snapshots](07-guides/05-snapper-btrfs.md) | Automatic system snapshots |
| [CUPS Printers](07-guides/03-cups-printers.md) | Printer and scanner support |
| [Chroot from Live ISO](07-guides/06-chrooting-from-a-live-iso.md) | System repair from live environment |
| [Winboat](07-guides/07-winboat.md) | Run Windows apps in containers |

### Desktop Environments
| Document | Description |
|----------|-------------|
| [Hyprland Guide](07-guides/08-hyprland-guide.md) | Configure Hyprland compositor |
| [Noctalia Shell (Hyprland)](07-guides/09-noctalia-hyprland.md) | Noctalia shell for Hyprland |
| [Otter-Shell (Hyprland)](07-guides/10-otter-shell-hyprland.md) | Otter-Shell for Hyprland |
| [Niri Guide](07-guides/11-niri-guide.md) | Configure Niri desktop |
| [Noctalia Shell (Niri)](07-guides/12-noctalia-niri.md) | Noctalia shell for Niri |
| [Otter-Shell (Niri)](07-guides/13-otter-shell-niri.md) | Otter-Shell for Niri |

### Troubleshooting
| Document | Description |
|----------|-------------|
| [Common Steps](08-common-faults/01-common-troubleshooting-steps.md) | First steps for diagnosing any issue |
| [Blender Title Bars](08-common-faults/02-blender-title-bars.md) | Wayland title bar fix |
| [Booster SCSI LUKS Crash](08-common-faults/03-booster-scsi-luks-crash.md) | Boot failure workaround |
| [GTK3 Themes Don't Stick](08-common-faults/04-gtk3-themes-dont-stick.md) | Theme persistence fix |
| [KWin Freezing (AMD RA24)](08-common-faults/05-kwin-ra24-freezing.md) | Wayland compositor freeze fix |
| [LACT Stuttering](08-common-faults/06-lact-stuttering.md) | Fan control stutter fix |
| [NVIDIA GTK/GSK Crash](08-common-faults/07-nvidia-gtk-gsk-crash.md) | Application crash fix |
| [Suspend/Wake Fix](08-common-faults/08-suspend-wake-fix.md) | Resume from sleep issues |

### Advanced & Internals
| Document | Description |
|----------|-------------|
| [What PikaOS Changes from Debian](09-advanced-and-internals/01-what-pikaos-changes-from-debian.md) | System modifications overview |
| [Default Configuration](09-advanced-and-internals/02-default-configuration.md) | Default system settings |
| [Bootloader & Initramfs](09-advanced-and-internals/03-bootloader-and-initramfs.md) | Technical bootloader details |
| [Additions to Debian](09-advanced-and-internals/04-additions.md) | Additional packages and tools |

### Getting Involved
| Document | Description |
|----------|-------------|
| [Overview](10-getting-involved/01-overview.md) | All ways to participate |
| [Documentation Guidelines](10-getting-involved/02-documentation-guidelines.md) | Write documentation for PikaOS |
| [Translation with Weblate](11-contributing/01-translate-weblate.md) | Localize PikaOS |
| [Feedback & Support](11-contributing/02-feedback.md) | Report issues and suggest improvements |