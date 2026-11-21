# Intel & AMD Drivers — Open-Source Graphics Stack

---

## Table of Contents

- [Usage of Basic Profiles](#usage-of-basic-profiles)
  - [For AMD/Intel GPUs](#for-amdintel-gpus)
  - [AMD-Specific Options](#amd-specific-options)
- [Related Guides](#related-guides)

---

> ℹ️ **Overview:** PikaOS uses open-source Mesa drivers as the default for Intel and AMD GPUs, providing excellent performance and compatibility out of the box. The Driver Manager provides easy access to different driver profiles including stable releases and development versions.

---

## Usage of Basic Profiles

### For AMD/Intel GPUs

| Profile | Description | Use Case |
| :--- | :---: | :--- |
| **Mesa Stable** | Official `Mesa` release from Debian repositories | Production systems, maximum stability |
| **Mesa Git** | Development version from upstream `Mesa` | Testing cutting-edge features |

> 💡 **Tip:** All profiles default to the latest non-experimental drivers for optimal performance and compatibility.

### AMD-Specific Options

AMD GPU users have an additional option:

- Install **AMD's proprietary driver stack** directly through the Driver Manager
  - Provides access to AMD's latest encoding technologies (`AMF`)
  - Recommended for advanced users who need specific features

---

## Related Guides

* [**Gaming on PikaOS**](../05-gaming/01-gaming-on-pikaos.md) — Gaming performance optimization