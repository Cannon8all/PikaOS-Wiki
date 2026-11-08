# Kernel Manager — PikaOS System Utility

---

## Table of Contents

- [Main Page](#main-page)
  - [Version Information](#version-information)
  - [Navigation Buttons](#navigation-buttons)
- [Kernel Version Page](#kernel-version-page)
  - [Interface Elements](#interface-elements)
  - [Kernel Package Entry Format](#kernel-package-entry-format)
  - [Status Indicators](#status-indicators)
  - [Kernel Types](#kernel-types)
  - [Usage Recommendations](#usage-recommendations)
- [SCX Scheduler Page](#scx-scheduler-page)
  - [Current Scheduler Status](#current-scheduler-status)
  - [Scheduler Selection Options](#scheduler-selection-options)
  - [Scheduler Mode Selection](#scheduler-mode-selection)
  - [Scheduler Flags](#scheduler-flags)
  - [Navigation & Actions](#navigation-actions)
- [Related Guides](#related-guides)

---

> ℹ️ **Overview:** The PikaOS Kernel Manager is a system utility that provides comprehensive information about your current kernel version, scheduling system, and available updates. It also displays the latest stable kernel version and allows easy switching between kernels and schedulers for performance tuning or hardware compatibility.

---

## Main Page

### Version Information

| Display Element | Description | Status Indicator |
| :--- | :---: | :--- |
| **Latest Stable Version** | Most recent stable kernel available (e.g., 6.15.3) | Green when matching, Red when older |
| **Running Version** | Currently installed kernel version (e.g., 6.15) | Green when current, Red when outdated |
| **Running Kernel** | Full kernel identifier with OS-specific build (e.g., 6.15.0-pikaos) | Always displayed |
| **Running Sched** | Active scheduler framework (e.g., `sched_ext: lawd`) | Always displayed |

### Navigation Buttons

| Button | Function |
| :--- | :--- |
| **Left Button** | Opens `SCX` (Scheduler eXtended) configuration page |
| **Right Button** | Opens kernel version management page |

> 💡 **Tip:** Check this page periodically to ensure your kernel is up-to-date. The color indicators help you quickly identify if an update is needed.

---

## Kernel Version Page

This screen displays all available kernel packages that can be installed on PikaOS, including version details and installation status.

### Interface Elements

#### Kernel Package Entry Format

Each kernel version shows:

```text
PikaOS Linux Kernel 6.15.0
6.15.0-10|pika8    ✔ linux-image-6.15.0-pikaos ✔
```

**Breakdown:**
- **Version Label:** PikaOS Linux Kernel 6.15.0
- **Version & Build:** `6.15.0-10|pika8` (version-build format)
- **Package Name:** `linux-image-6.15.0-pikaos` (installable via package manager)
- **Status Indicator:** ✔ (available for installation)

### Status Indicators

| Symbol | Meaning | Description |
| :--- | :---: | :--- |
| **✔ installed** | Bold/highlighted | Currently running kernel |
| **✔** (standalone) | Available | Ready to install |
| *No indicator* | — | Not available in repositories |

### Kernel Types

| Type | Examples | Use Case |
| :--- | :---: | :--- |
| **Stable Kernels** | 6.14.5, 6.15.0 (non-"rc" versions) | Production systems, maximum stability |
| **Testing/RC Kernels** | 6.15.0-rc5, 6.15.0-rc6 | Testing new features, development builds |

### Usage Recommendations

| Goal | Recommendation |
| :--- | :--- |
| **Stability** | Choose stable kernels (e.g., `6.15.0`) for production systems |
| **Features** | Test RC kernels (e.g., `6.15.0-rc6`) for cutting-edge features |
| **Compatibility Troubleshooting** | Use older kernels (e.g., `6.14.7`) for legacy support |
| **Installation** | Click any entry with ✔ to initiate installation |

> ⚠️ **Warning:** RC kernels may offer newer features but could be less stable than release versions.

---

## SCX Scheduler Page

This screen allows configuration of the Sched-Ext (`SCX`) scheduler, which replaces the default Linux kernel scheduler for optimized performance.

### Current Scheduler Status

Displays the active scheduler: `sched_ext: lavd`

### Scheduler Selection Options

| Option | Description |
| :--- | :--- |
| **Disable `SCX`** | Revert to default Linux `BORE` scheduler |
| **Enable `SCX` with Custom Scheduler** | Use extended scheduler framework |

### Scheduler Mode Selection

When a scheduler is selected, the interface displays:

- **Default Modes:** Automatically populate and overwrite Scheduler Flags
- **Example Profiles for `BPF-LAND`:**

| Profile | Description | Optimization Target |
| :--- | :---: | :--- |
| **Multimedia Mode** | Optimized for audio processing and multimedia applications | Media workloads |
| **Gaming Mode** | Prioritizes `P-cores` on Intel CPUs<br>Optimizes Ryzen `X3D` cache-dense `CCDs`<br>General high-performance tuning | Gaming performance |

### Scheduler Flags

Displays active tuning flags (e.g., `m performance`) for fine-grained control.

### Navigation & Actions

| Button | Function |
| :--- | :--- |
| **Back** | Return to previous screen |
| **Apply** | Save scheduler configuration changes |

> 💡 **Tip:** Gaming Mode is recommended for gaming workloads on systems with hybrid CPU architectures (Intel P-cores/E-cores or AMD Ryzen X3D).

---

## Related Guides

* [**Pikman CLI Guide**](01-pikman-cli.md) — Command-line package management
* [**Kernel Manager**](05-kernel-manager.md) — Switch between kernel versions safely
* [**Post-Install Setup**](../02-installation/05-post-install-setup.md) — Initial system configuration
* [**PikaOS Device Manager**](07-pikaos-device-manager.md) — GPU driver compatibility checks