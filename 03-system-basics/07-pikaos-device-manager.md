# PikaOS Device Manager — Hardware & Driver Management Tool

---

## Table of Contents

- [One-Click Installs](#one-click-installs)
- [Control Device Drivers Easily](#control-device-drivers-easily)
  - [Driver Management Features](#driver-management-features)
- [Other Devices](#other-devices)
  - [Supported Device Categories](#supported-device-categories)
- [Related Guides](#related-guides)

---

> ℹ️ **Overview:** The PikaOS Device Manager is a modern, feature-rich upgrade to the original Driver Manager. It retains all familiar functionality while adding powerful new tools for comprehensive system hardware management and driver configuration.

---

## One-Click Installs

The Device Manager simplifies installing and switching between major graphics driver families:

| Driver Family | Description | Use Case |
| :--- | :---: | :--- |
| **Mesa** | Open-source graphics drivers | AMD/Intel GPUs, default choice |
| **NVIDIA** | Proprietary NVIDIA drivers | RTX/GTX series, gaming, compute |

> 💡 **Tip:** Switching between driver families is effortless through the graphical interface—no manual configuration required.

---

## Control Device Drivers Easily

Manage drivers for nearly any device on your system:

### Driver Management Features

| Action | Description | Use Case |
| :--- | :---: | :--- |
| **Enable/Disable at Boot** | Toggle driver activation during system startup | Troubleshoot unstable hardware (e.g., problematic Wi-Fi cards) |
| **Pause Drivers** | Temporarily disable specific device drivers | Isolate hardware conflicts |
| **Activate Drivers** | Re-enable previously disabled drivers | Restore functionality after troubleshooting |
| **Inspect Drivers** | View detailed driver information | Diagnose compatibility issues |

> 💡 **Tip:** Use the enable/disable feature when troubleshooting unstable hardware. This is especially useful for problematic Wi-Fi cards or other peripheral devices that may cause boot issues.

---

## Other Devices

The left-hand menu lists all detected hardware with associated drivers, providing a comprehensive view of your system's components:

### Supported Device Categories
- Graphics Cards (GPU)
- Network Adapters (Wi-Fi/Ethernet)
- Audio Devices
- Storage Controllers
- Input Devices (Keyboards, Mouse, Gamepads)
- USB Controllers
- And more...

**Management Actions Available:**
1. **Pause** — Temporarily disable a device driver
2. **Activate** — Re-enable a disabled device
3. **Inspect** — View detailed hardware and driver information

> ℹ️ **Info:** System-wide driver management has never been easier—all controls are accessible through an intuitive graphical interface.

---

## Related Guides

* [**Secure Boot Setup**](../07-guides/04-secure-boot.md) — Driver signing requirements for Secure Boot systems