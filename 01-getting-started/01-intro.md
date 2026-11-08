# Welcome to PikaOS - Introduction Guide

---

## Table of Contents

- [Fast, Up-to-Date, and Rolling Release](#fast-up-to-date-and-rolling-release)
- [One Versatile System](#one-versatile-system)
- [Play Without the Setup Weekend](#play-without-the-setup-weekend)
- [Your GPU Has a Day Job Too](#your-gpu-has-a-day-job-too)
- [Control When You Want It GUIs When You Don't](#control-when-you-want-it-guis-when-you-dont)
- [System Specifications Overview](#system-specifications-overview)
- [Related Guides](#related-guides)
- [Quick Start Checklist](#quick-start-checklist)
- [Troubleshooting & Support](#troubleshooting-support)

---

**PikaOS is a modern Linux distribution built on Debian Sid, optimized for gaming, content creation, and daily use.** Get the latest drivers, kernel updates, and tools right out of the box.

---

## Fast, Up-to-Date, and Rolling Release

With the latest drivers, kernel, gaming stack, development tools, and content creation apps, PikaOS gets you to the good part faster.

**Core Foundation:**
- **Base:** Debian Sid + Deb Multimedia (Curated, patched, compiled together)
- **Packages:** `O3` · `LTO` · `x86-64-v3` optimized across repositories
- **Kernel:** Custom performance build with CachyOS patches and switchable `SCX` schedulers
- **Graphics:** Latest Mesa, NVIDIA, and full compute stacks (`ROCm`, `CUDA`, `OneAPI`)
- **Installation:** XFS · Btrfs · EXT4 — your choice
- **Source:** Open source — every package and tool on our Gitea

> 💡 **Tip:** Need the details? Our wiki covers installs, drivers, tools, and troubleshooting comprehensively.

---

## One Versatile System

**PikaOS isn't a gaming skin over a stock distro.** We maintain the kernel, graphics stack, repositories, and tools that make the whole machine easier to use.

---

## Play Without the Setup Weekend

`Steam`, `Wine`, `Gamescope`, `MangoHud`, and support for controllers you forgot you owned. Latest Mesa (AMD®/INTEL®) and NVIDIA® graphics drivers arrive through a stack we maintain ourselves.

**Key Gaming Features:**
- **Out-of-box gaming:** Everything needed to play Windows games immediately
- **Controller support:** Automatic detection and configuration for popular controllers
- **Latest drivers:** Up-to-date Mesa and NVIDIA drivers via our maintained stack

---

## Your GPU Has a Day Job Too

Our Blender package ships with `CUDA`, `OptiX`, `HIP`, `HIPRT`, and `OneAPI` support. We package full ROCm, CUDA, and OneAPI stacks for compute work, while our OBS package includes game capture and stream-key support.

**Content Creation Capabilities:**
- **Blender optimized:** Full acceleration support via `CUDA`, `OptiX`, and `HIP`
- **Compute stacks:** Complete `ROCm`, `CUDA`, and `OneAPI` implementations
- **Streaming ready:** OBS with game capture and stream-key integration

---

## Control When You Want It GUIs When You Don't

Update `APT` and `Flatpak` with Pikman, switch kernels and schedulers, manage GPU drivers, or do it all from the CLI. The useful choices are exposed; the chores are not.

**Flexible Management:**
- **Package management:** `APT` and `Flatpak` via intuitive Pikman tool
- **Kernel switching:** Choose your kernel version easily
- **Scheduler selection:** Switch between `SCX` schedulers for optimal performance
- **GPU driver management:** Full control over graphics drivers
- **CLI access:** All power available through command line when desired

---

## System Specifications Overview

| Component | Specification | Details |
| :--- | :---: | :--- |
| **Base** | Debian Sid + Deb Multimedia | Curated, patched, compiled together |
| **Packages** | `O3` · `LTO` · `x86-64-v3` | Optimized across base repositories |
| **Kernel** | Custom performance build | CachyOS patches and `SCX` schedulers |
| **Graphics** | Mesa · NVIDIA · Compute | Latest drivers with full compute stacks |
| **Installation Options** | XFS · Btrfs · EXT4 | Flexible filesystem choices |
| **Source Code** | Open source | Every package on Gitea repository |

---

## Related Guides

* [**Desktop Editions**](./02-editions.md) — Choose the right desktop environment for your workflow
* [**BIOS Checklist**](./03-bios-checklist.md) — Prepare your system before installation
* [**Installation Overview**](../02-installation/01-overview.md) — Complete installation methods and options
* [**Post-Install Setup**](../02-installation/05-post-install-setup.md) — Essential first steps after installation
* [**Pikman CLI & GUI**](../03-system-basics/01-pikman-cli.md) — Package management made simple
* [**PikaOS Device Manager**](../03-system-basics/07-pikaos-device-manager.md) — Hardware and desktop detection
* [**Gaming on PikaOS**](../05-gaming/01-gaming-on-pikaos.md) — Gaming setup and Proton configuration
* [**NVIDIA Drivers**](../04-hardware-and-drivers/01-nvidia-drivers.md) — GPU driver installation and management
* [**What PikaOS Changes from Debian**](../09-advanced-and-internals/01-what-pikaos-changes-from-debian.md) — Technical overview of modifications
* [**Default Configuration**](../09-advanced-and-internals/02-default-configuration.md) — Default system settings reference

---

## Quick Start Checklist

Before you begin, ensure you have:

1. ✅ **Downloaded the ISO:** Get the latest PikaOS image from our website
2. ✅ **Created installation media:** USB drive (8GB minimum recommended)
3. ✅ **Backed up important data:** Always backup before major system changes
4. ✅ **Checked hardware compatibility:** Verify your components are supported

> 💡 **Tip:** Review the [BIOS Checklist](./03-bios-checklist.md) to ensure your firmware is properly configured for Linux installation.
