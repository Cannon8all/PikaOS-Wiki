# PikaOS Additions — System Enhancements & Packages

---

## Table of Contents

- [System Tools & Utilities](#system-tools--utilities)
  - [NVIDIA Optimus Support](#nvidia-optimus-support)
  - [CPU Scheduler & Performance](#cpu-scheduler-performance)
- [Gaming & Multimedia Packages](#gaming--multimedia-packages)
  - [Meta-Packages Available](#meta-packages-available)
- [Developer Tools & Repositories](#developer-tools--repositories)
- [Laptop Hardware Management](#laptop-hardware-management)
- [Legacy Compatibility Package](#legacy-compatibility-package)
  - [AMDGPU Backlight Blacklist (Optional)](#amdgpu-backlight-blacklist-optional)
- [Related Guides](#related-guides)

---

> ℹ️ **Overview:** This guide documents additional tools, meta-packages, and system enhancements included in PikaOS beyond the core installation. These additions provide specialized functionality for gaming, content creation, laptop hardware management, and advanced GPU configurations.

---

## System Tools & Utilities

### NVIDIA Optimus Support

| Tool | Purpose | Usage Context |
| :--- | :--- | :---: |
| **`prime-run`** | CLI wrapper to enable Optimus for command-line applications | Run specific apps on dedicated GPU without full session switch |
| **GPU Selector (KDE Plasma)** | GUI tool for selecting active GPU in multi-GPU systems | KDE Plasma desktop environments with hybrid graphics |

### CPU Scheduler & Performance

- **`scx`** — Scalable Linux CPU scheduler included by default
- **`ananicy-cpp`** — Automatic process priority tuning for better responsiveness
- **PikaOS Kernel Manager** — GUI interface to change SCX schedulers and kernel parameters

---

## Gaming & Multimedia Packages

### Meta-Packages Available

| Package | Contents | Use Case |
| :--- | :--- | :---: |
| **`pika-hhd-meta`** | Gamescope-session, inputplumber | Handheld gaming optimization (Steam Deck-style experience) |
| **`pika-gaming-meta`** | pika-multimedia-meta, Wine Staging, Steam, Lutris, and more | Complete gaming suite installation |
| **`pika-multimedia-meta`** | All codecs, GStreamer, VAAPI, VDPAU (64-bit & 32-bit) | Hardware-accelerated media playback across architectures |

---

## Developer Tools & Repositories

- **OBS GameCapture** — Enhanced screen recording for gaming content
- **multiatium** — Multi-monitor AMD display management tools
- **Vulkan Switcher Wrappers (AMD GPUs)** — Simplify Vulkan API selection for different games

---

## Laptop Hardware Management

Device-specific packages for enhanced laptop functionality:

| Tool | Vendor/Function | Description |
| :--- | :--- | :---: |
| **`lact`** | General | AMD GPU temperature and fan control daemon |
| **`asusctl`** | ASUS | ASUS laptop hardware management (RGB, fans, power modes) |
| **`supergfxctl`** | Intel/AMD | Switchable graphics management for hybrid laptops |
| **`corectrl`** | General | Hardware sensor monitoring and fan curve control |
| **`nvidia-dlss-switcher`** | NVIDIA | Quick DLSS feature toggling without game restart |
| **`xone` / `xpadneo`** | Xbox Controllers | Enhanced Xbox controller support with custom mappings |

> 💡 **Tip:** Most device-specific tools are auto-detected and installed via the PikaOS Device Manager during initial setup.

---

## Legacy Compatibility Package

### AMDGPU Backlight Blacklist (Optional)

| Feature | Details |
| :--- | :---: |
| **Package Name** | `amdgpu-backlight-blacklist` |
| **Purpose** | Fixes brightness controls on specific Lenovo AMD laptops |
| **Side Effect** | Breaks brightness controls on 99% of AMD laptops |
| **Recommendation** | Install only if experiencing backlight issues on supported Lenovo models |

> ⚠️ **Warning:** This package is not recommended for general use. Only install if you have confirmed compatibility issues with your specific Lenovo AMD laptop model.

---

## Related Guides

* [**Device Manager**](../03-system-basics/07-pikaos-device-manager.md) — Complete hardware management interface