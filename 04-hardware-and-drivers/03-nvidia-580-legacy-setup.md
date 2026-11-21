# NVIDIA 580 Legacy Driver Setup — Older GPU Support

---

## Table of Contents

- [Supported Hardware](#supported-hardware)
  - [Pascal Architecture](#pascal-architecture)
  - [Maxwell Architecture](#maxwell-architecture)
  - [Volta Architecture](#volta-architecture)
- [Required Packages](#required-packages)
- [Installation Procedure](#installation-procedure)
  - [First Stage: Install the Distro](#first-stage-install-the-distro)
  - [Second Stage: User Setup and Configuration](#second-stage-user-setup-and-configuration)
- [Verification](#verification)
  - [Check NVIDIA Driver Status](#check-nvidia-driver-status)
- [Related Guides](#related-guides)

---

> ℹ️ **Overview:** To maintain full hardware acceleration and system stability on older graphics cards, PikaOS provides a specialized NVIDIA 580 legacy package. Installing this driver automatically pulls in the legacy kernel to ensure future kernel compatibility.

---

## Supported Hardware

This driver package is officially required for the following legacy NVIDIA GPU series and architectures (including desktop and mobile variants) supported by the **580 driver branch**:

### Pascal Architecture

| Product Line | Models |
| :--- | :--- |
| **GeForce GTX 10 Series** | GTX 1080 Ti, GTX 1080, GTX 1070 Ti, GTX 1070, GTX 1060, GTX 1050 Ti, GTX 1050, GT 1030 |
| **GeForce GTX 10 Series (Mobile/Max-Q)** | GTX 1080 Mobile, GTX 1080 Max-Q, GTX 1070 Mobile, GTX 1070 Max-Q, GTX 1060 Mobile, GTX 1050 Ti Mobile, GTX 1050 Mobile |
| **GeForce MX Series (Pascal)** | MX350, MX330, MX250, MX230, MX150 |
| **TITAN Series (Pascal)** | TITAN X / Xp |
| **NVIDIA RTX/Quadro (Pascal)** | Quadro P6000, P5000, P4000, P3200, P3000, P2200, P2000, P1000, P620, P600, P520, P500 |

### Maxwell Architecture

| Product Line | Models |
| :--- | :--- |
| **GeForce 900 Series** | GTX 980 Ti, GTX 980, GTX 970, GTX 960, GTX 950 |
| **GeForce 900M & Mobile Series** | GTX 980 (Mobile), GTX 980M, GTX 970M, GTX 965M, GTX 960M, GTX 950M, 945M, 940MX, 940M, 930MX, 930M, 920MX, 920M, 910M |
| **GeForce 800M Series** | GTX 860M, GTX 850M, GTX 845M, GTX 840M, GTX 830M |
| **GeForce 700 Series (Maxwell variants only)** | GTX 750 Ti, GTX 750 |
| **GeForce MX Series (Maxwell)** | 940MX, 930MX, MX130, MX110 |
| **TITAN Series (Volta)** | GeForce GTX TITAN X |
| **NVIDIA RTX/Quadro (Maxwell)** | Quadro M6000, M5000, M4000, M2000, M1200, M620, M520, Quadro K620 (Maxwell variant) |

### Volta Architecture

| Product Line | Models |
| :--- | :--- |
| **TITAN Series (Volta)** | TITAN V |

> 💡 **Tip:** If your GPU is not listed above, you may be eligible for the modern NVIDIA driver stack. Check [NVIDIA Drivers (Modern)](01-nvidia-drivers.md) for current-generation support.

---

## Required Packages

The setup is bundled into a single installation step:

| Package | Description |
| :--- | :--- |
| **`pika-nvidia-driver`** | The NVIDIA 580 legacy graphics driver |
| **`kernel-pika-legacy`** | Customized kernel patch (automatically installed as dependency) |

---

## Installation Procedure

> ⚠️ **Important:** Install the NVIDIA legacy drivers during PikaOS installation for best compatibility.

### First Stage: Install the Distro

1. Proceed through the PikaOS installer as normal to install the distribution
2. After a successful install, the system will reboot automatically

### Second Stage: User Setup and Configuration

After booting into your new PikaOS installation:

**Connect to the internet and open a terminal**, then run the following commands:

```bash
pikman upgrade
pikman i pika-nvidia-driver kernel-pika-legacy
```

> 🔑 **Password:** `pikaos` (default for initial setup)

**Proceed with system setup followed by a reboot** to activate the legacy drivers.

---

## Verification

After rebooting, verify that the correct driver is active:

### Check NVIDIA Driver Status

Run the following command in terminal:

```bash
nvidia-smi
```

> ℹ️ **Expected Output:** The output should display driver version `580.xx`. If you see a different version or an error message, the installation may not have completed successfully.

---

## Related Guides

* [**Post-Install Setup**](../02-installation/05-post-install-setup.md) — Initial system configuration guide