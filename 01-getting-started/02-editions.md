# PikaOS Desktop Editions Guide

---

## Table of Contents

- [Available Desktop Environments](#available-desktop-environments)
- [GNOME - Focused & Calm](#gnome-focused-calm)
- [KDE Plasma - Familiar & Flexible](#kde-plasma-familiar-flexible)
- [Hyprland - Polished Tiling](#hyprland-polished-tiling)
- [Niri - Scrollable Tiling](#niri-scrollable-tiling)
- [COSMIC - Modern Rust Desktop](#cosmic-modern-rust-desktop)
- [Which Edition Should You Choose?](#which-edition-should-you-choose)
- [Installation Notes](#installation-notes)
- [Converting Between Editions](#converting-between-editions)
- [Related Guides](#related-guides)

---

**PikaOS offers multiple editions to suit different preferences and hardware configurations.** Every edition gets the same PikaOS base; you choose your desktop environment based on workflow preferences and GPU requirements.

---

## Available Desktop Environments

The desktop environment determines your graphical interface and workflow style. Choose a familiar traditional desktop or jump straight into a modern tiling window manager.

---

## GNOME - Focused & Calm

**Best for:** Users who prefer simplicity and minimal configuration. Ideal for first-time Linux users.

- **Philosophy:** Stays out of your way, focused on content
- **Workflow:** Mouse-first, intuitive gestures
- **Customization:** Minimal by default, extensible via extensions
- **Experience:** Calm, distraction-free interface

**Downloads:**
| Version | Description | Link |
| :--- | :--- | :--- |
| **Standard Edition** | Open-source drivers for AMD/Intel | [Download GNOME ISO](https://pika-os.com/download/gnome) |
| **NVIDIA Edition** | Pre-configured proprietary NVIDIA drivers | [Download GNOME NVIDIA ISO](https://pika-os.com/download/gnome-nvidia) |

> 💡 **Tip:** GNOME is perfect if you want the computer to stay out of your way and focus on your work.

---

## KDE Plasma - Familiar & Flexible

**Best for:** Windows users transitioning to Linux who want customization without complexity.

- **Philosophy:** Deeply adjustable, becomes exactly your desktop
- **Workflow:** Traditional desktop metaphor with modern features
- **Customization:** Extensive configuration options out of the box
- **Experience:** Familiar interface with powerful capabilities

**Downloads:**
| Version | Description | Link |
| :--- | :--- | :--- |
| **Standard Edition** | Open-source drivers for AMD/Intel | [Download KDE ISO](https://pika-os.com/download/kde) |
| **NVIDIA Edition** | Pre-configured proprietary NVIDIA drivers | [Download KDE NVIDIA ISO](https://pika-os.com/download/kde-nvidia) |

> 💡 **Tip:** KDE Plasma is ideal if you want a familiar Windows-like experience with endless customization options.

---

## Hyprland - Polished Tiling

**Best for:** Keyboard-first users who want modern aesthetics without manual configuration.

- **Philosophy:** Dynamic tiling with motion and flexibility
- **Workflow:** Keyboard-driven, window auto-arrangement
- **Customization:** Pre-configured but fully customizable via Lua scripts
- **Experience:** Modern, animated tiling window manager

**Downloads:**
| Version | Description | Link |
| :--- | :--- | :--- |
| **Standard Edition** | Open-source drivers for AMD/Intel | [Download Hyprland ISO](https://pika-os.com/download/hyprland) |
| **NVIDIA Edition** | Pre-configured proprietary NVIDIA drivers | [Download Hyprland NVIDIA ISO](https://pika-os.com/download/hyprland-nvidia) |

> 💡 **Tip:** Hyprland is perfect if you want a modern tiling workflow with beautiful animations already dialed in.

---

## Niri - Scrollable Tiling

**Best for:** Users who prefer unconventional workflows and smooth animations.

- **Philosophy:** Vertical scrollable tiling with unique interaction model
- **Workflow:** Keyboard-driven, vertical workspace organization
- **Customization:** Configurable via `KDL` (`Kdl DSL`) configuration language
- **Experience:** Learn by using it, unconventional but powerful

**Downloads:**
| Version | Description | Link |
| :--- | :--- | :--- |
| **Standard Edition** | Open-source drivers for AMD/Intel | [Download Niri ISO](https://pika-os.com/download/niri) |
| **NVIDIA Edition** | Pre-configured proprietary NVIDIA drivers | [Download Niri NVIDIA ISO](https://pika-os.com/download/niri-nvidia) |

> 💡 **Tip:** Niri is ideal if you want to experiment with a unique tiling approach and learn by using it.

---

## COSMIC - Modern Rust Desktop

**Best for:** Users who want innovation and a unique desktop experience built from the ground up.

- **Philosophy:** Built in Rust, designed for productivity and modern workflows
- **Workflow:** Tiling support, intelligent workspaces, workspace overview
- **Customization:** Growing ecosystem with focus on usability
- **Experience:** Innovative desktop environment with forward-thinking design

**Downloads:**
| Version | Description | Link |
| :--- | :--- | :--- |
| **Standard Edition** | Open-source drivers for AMD/Intel | [Download COSMIC ISO](https://pika-os.com/download/cosmic) |
| **NVIDIA Edition** | Pre-configured proprietary NVIDIA drivers | [Download COSMIC NVIDIA ISO](https://pika-os.com/download/cosmic-nvidia) |

> ⚠️ **Note:** COSMIC is in early development by System76. The PikaOS COSMIC edition may be experimental and subject to change.

---

## Which Edition Should You Choose?

### Quick Selection Guide

| If You... | Choose | Reason |
| :--- | :---: | :--- |
| Are new to Linux | **GNOME** | Familiar, calm, stays out of your way |
| Are a Windows user | **KDE Plasma** | Most familiar interface and workflow |
| Prefer keyboard-first workflows | **Hyprland or Niri** | Modern tiling workspaces |
| Have an AMD-only system | **Any edition** | Standard ISO works perfectly for all GPUs |
| Want to experiment | **COSMIC** | Innovative, Rust-based desktop |

### GPU Requirements

> 💡 **Use the NVIDIA ISO** for `RTX` cards and `GTX` 1650 or newer GPUs. The pre-installed proprietary drivers ensure optimal performance out of the box.

For older NVIDIA GPUs or AMD/Intel systems, the Standard ISO includes open-source drivers that work perfectly well.

---

## Installation Notes

The editions page shows available downloads for each desktop environment. Choose based on:

1. **Your workflow preference** — How do you like to interact with your computer?
2. **Your GPU model** — NVIDIA cards benefit from pre-installed proprietary drivers
3. **Your Linux experience** — Traditional DEs vs tiling window managers

Each edition provides the same core PikaOS experience; only the desktop interface differs.

---

## Converting Between Editions

**Note:** Side-by-side installs are not officially supported by the PikaOS team. For the best experience, use the ISO that matches your preferred desktop environment from the start.

### Conversion Options

| From | To | Recommendation |
| :--- | :--- | :--- |
| GNOME/KDE | Tiling (Hyprland/Niri) | Clean install with tiling ISO recommended |
| Any Edition | COSMIC | Clean install with COSMIC ISO recommended |
| Tiling | Traditional DE | Reinstall using traditional desktop ISO |

> ⚠️ **Warning:** While manual conversion is technically possible, a clean installation ensures the best experience and avoids configuration conflicts.

---

## Related Guides

* [**BIOS Checklist**](./03-bios-checklist.md) — Prepare your system before installation
* [**Installation Overview**](../02-installation/01-overview.md) — Complete installation methods and options
* [**NVIDIA Drivers Guide**](../04-hardware-and-drivers/01-nvidia-drivers.md) — GPU driver troubleshooting steps
