# NVIDIA Drivers in PikaOS

---

## Table of Contents

- [Basic Profiles Overview](#basic-profiles-overview)
  - [For NVIDIA GPUs](#for-nvidia-gpus)
- [Advanced Profiles](#advanced-profiles)
  - [Select Different NVIDIA Driver Versions](#select-different-nvidia-driver-versions)
- [Important Warnings](#important-warnings)
  - [Driver Version Compatibility](#driver-version-compatibility)
- [Related Guides](#related-guides)

---

PikaOS provides comprehensive support for NVIDIA GPUs through multiple driver profiles, making it easy to choose the right configuration for your needs.

---

## Basic Profiles Overview

### For NVIDIA GPUs

Choose between two primary driver profiles:

- **NVIDIA Open** - Open-source kernel modules; recommended for `GTX` 16-series and newer GPUs
- **NVIDIA Closed** - Proprietary drivers with better performance and feature support

> 💡 **Note:** Users who prefer the fully open-source `Nouveau` driver can uninstall NVIDIA profiles and use `Mesa` profiles instead. This provides maximum openness at the cost of reduced performance and missing features like hardware acceleration for newer games.

All profiles default to the latest non-experimental drivers, ensuring good compatibility out of the box.

---

## Advanced Profiles

### Select Different NVIDIA Driver Versions

PikaOS provides a wide selection of NVIDIA drivers from version 550 onward, including:

- **Beta releases** - Latest features and improvements
- **New Branch releases** - Cutting-edge driver versions for testing

This is ideal for users who need older versions for compatibility with specific applications or want to test the newest builds before they become stable.

---

## Important Warnings

### Driver Version Compatibility

When selecting different NVIDIA driver versions, be aware of these considerations:

- **Kernel requirements** - Older drivers may require rolling back to a compatible kernel version
- **Version mismatches** - Using mismatched driver and kernel versions can cause kernel panics and prevent the system from booting
- **Experimental builds** - Experimental drivers are clearly labeled in the Device Manager and never set as defaults

> 💡 **Recommendation:** Always check the [PikaOS Forum](https://forum.pikaos.dev) before downgrading to an older driver version. Other users may have encountered similar compatibility issues with documented solutions.

---

## Related Guides

* [**NVIDIA 580 Legacy Setup**](03-nvidia-580-legacy-setup.md) — Legacy configuration for NVIDIA GPU systems