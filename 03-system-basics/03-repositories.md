# Repositories — PikaOS Package Sources

---

## Table of Contents

- [Base Repository (Nest)](#base-repository-nest)
  - [Included Repositories](#included-repositories)
- [GFX/Compute Repository (Raven/Pigeon)](#gfxcompute-repository-ravenpigeon)
  - [AMD GPU Stack](#amd-gpu-stack)
  - [Intel GPU Stack](#intel-gpu-stack)
  - [Compute Frameworks](#compute-frameworks)
- [3rd-Party Sync Repository (Parrot)](#3rd-party-sync-repository-parrot)
  - [Gaming & Communication](#gaming-communication)
  - [Productivity & Privacy](#productivity-privacy)
  - [Window Managers & Tools](#window-managers-tools)
- [Custom Repository (Cockatiel)](#custom-repository-cockatiel)
  - [Included Applications](#included-applications)
- [Related Guides](#related-guides)

---

> ℹ️ **Overview:** PikaOS uses a multi-layered repository system optimized for performance and compatibility. Each repository serves a specific purpose, from base packages to specialized graphics/compute stacks and third-party integrations.

---

## Base Repository (Nest)

The **Base Repository** is a custom compilation of Debian Sid packages with the following optimizations:

| Feature | Description |
| :--- | :--- |
| `x86_64-v3` | Optimized for modern 64-bit `AMD`/`Intel` CPUs |
| `LTO` (Link-Time Optimization) | Improved performance through compiler optimization |
| `O3` (Optimization Level 3) | Maximum compilation optimization |
| **ABI Compatibility** | Packages compiled against each other to prevent conflicts |

### Included Repositories

| Repository | Contents | Purpose |
| :--- | :---: | :--- |
| **Debian Sid (main)** | Core Debian packages | Stable base system packages |
| **Debian Sid (contrib)** | Community-maintained free software | Additional community packages |
| **Debian Sid (non-free)** | Proprietary firmware/drivers | Hardware support |
| **Debian Sid (non-free-firmware)** | Standalone firmware | Firmware for devices |
| **Debian Experimental** | Selected desktop environments | Cutting-edge DE packages |
| **DEB Multimedia** | Multimedia frameworks | Updated audio/video codecs |

> 💡 **Tip:** The DEB Multimedia repository provides up-to-date multimedia packages with full feature support, including `FFmpeg` with `AMF` and `NVENC` encoding, plus the latest `GStreamer` plugins.

---

## GFX/Compute Repository (Raven/Pigeon)

The **GFX/Compute Repository** contains specialized stacks for graphics and compute workloads:

### AMD GPU Stack
| Component | Description |
| :--- | :--- |
| **Modified AMDGPU Stack** | Enables packages depending on `amdgpu` to install on modern Debian bases like PikaOS |
| `AMF` (1.5 branch) | `AMF` encoding for `RDNA3` and newer GPUs |
| `AMF Legacy` (1.4 branch) | `AMF` encoding for `RDNA2` and older GPUs |

### Intel GPU Stack
| Component | Description |
| :--- | :--- |
| **Modified Intel Level Zero** | Enables `OneAPI` and other `Intel` compute frameworks on modern Debian bases |

### Compute Frameworks
| Framework | Purpose | Includes |
| :--- | :---: | :--- |
| `ROCm` | AMD GPU compute platform | Full stack with versioning, dev packages, `HIPRT` for GPU compute |
| `OneAPI` | Intel GPU compute framework | Full stack with versioning, dev packages |
| `CUDA` | NVIDIA GPU compute platform | Full stack with versioning, dev packages |

---

## 3rd-Party Sync Repository (Parrot)

The **3rd-Party Sync Repository** integrates popular applications from their official sources:

### Gaming & Communication
| Application | Source | Notes |
| :--- | :---: | :--- |
| **Steam** | Official Valve/Steampowered repository | Latest Steam client |
| **Discord** | [palfrey/discord-apt](https://github.com/palfrey/discord-apt) | Stable and Canary builds |
| **xivlauncher** | [Maia Everett PPA](https://launchpad.net/~linneris/+archive/ubuntu/xivlauncher-core-stable) | Final Fantasy XIV launcher |

### Productivity & Privacy
| Application | Source | Notes |
| :--- | :---: | :--- |
| **VS Code** | Official Microsoft repository | Visual Studio Code |
| **Brave** | Official Brave repository | Privacy-focused browser |
| **Floorp** | Official Floorp repository | Privacy-focused Firefox derivative |
| **Mullvad** | Official Mullvad repository | VPN client |
| **ProtonVPN** | Official Proton repository | VPN client |

### Window Managers & Tools
| Application | Source | Notes |
| :--- | :---: | :--- |
| **WM Packages (OBS)** | [AvengeMedia OBS](https://download.opensuse.org/repositories/home:/AvengeMedia/Debian_13/) | Various window manager tools and utilities |

---

## Custom Repository (Cockatiel)

The **Custom Repository** contains:

- **PikaOS-maintained packages** from <https://git.pika-os.com/>
- **Latest versions** of critical applications not yet in upstream Debian

### Included Applications
| Category | Packages |
| :--- | :--- |
| **Creation & Media** | OBS Studio, Blender, Lutris |
| **Graphics** | Mesa drivers, firmware, SOF firmware |
| **Overlay & Monitoring** | GOverlay, MangoHud |
| **Compatibility Layers** | Wine Staging |
| **Gaming Tools** | Gamescope |
| **Kernel** | Custom PikaOS kernels |

> 💡 **Tip:** This repository ensures you always have access to the latest versions of essential tools and cutting-edge features.

---

## Related Guides

* [**Pikman CLI Guide**](01-pikman-cli.md) — Command-line package management
* [**Pikman GUI**](02-pikman-gui.md) — Graphical software manager for package management
* [**Kernel Manager**](05-kernel-manager.md) — Switch between kernel versions safely
* [**PikaOS Device Manager**](07-pikaos-device-manager.md) — GPU driver installation and updates
* [**Post-Install Setup**](../02-installation/05-post-install-setup.md) — First steps after installation