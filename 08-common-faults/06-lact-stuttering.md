# LACT - Fix Performance and Stuttering Issues

---

## Table of Contents

- [Problem](#problem)
- [Root Cause](#root-cause)
- [Solution: Configure GPU Performance Profile](#solution-configure-gpu-performance-profile)
  - [Step 1: Install LACT](#step-1-install-lact)
  - [Step 2: Launch LACT](#step-2-launch-lact)
  - [Step 3: Configure Performance Settings](#step-3-configure-performance-settings)
  - [Step 4: Reboot (Recommended)](#step-4-reboot-recommended)
- [Related Guides](#related-guides)

---

## Problem

Experiencing **stuttering** or **performance drops** in games on hybrid laptops with dedicated GPUs.

---

## Root Cause

Your GPU may not be using the correct power profiles, causing it to remain in a low-power state even during demanding tasks like gaming.

> 💡 **What is LACT?**  
> Linux Advanced Control Tool (LACT) provides a GUI for controlling AMD and NVIDIA GPUs on Linux. It allows you to adjust power profiles, fan curves, and performance settings.

---

## Solution: Configure GPU Performance Profile

### Step 1: Install LACT

Open a terminal and run:

```bash
pikman update && pikman install lact
```

### Step 2: Launch LACT

You can start LACT from your app launcher, or run it via terminal:

```bash
lact
```

**Official Package Info:** [LACT on GitHub](https://github.com/ilyazoliatov/lact)

---

### Step 3: Configure Performance Settings

1. **Select Your Dedicated GPU**  
   In the main window, select your dedicated GPU from the device list.

2. **Navigate to OC Tab**  
   Click on the **OC** (Overclocking) tab in the sidebar.

3. **Adjust Performance Level**  
   Under the **Performance** section:
   - Find **Performance Level** dropdown
   - Change from Automatic to Manual

4. **Set Power Profile Mode**  
   In the same section:
   - Find **Power Profile Mode** dropdown
   - Change from BOOTUP_DEFAULT to 3D_FULL_SCREEN

5. **Apply and Save**  
   Click the **Apply** or **Save** button to commit changes.

### Step 4: Reboot (Recommended)

As a precaution, reboot your system after making these changes:

```bash
sudo reboot
```

> 💡 **Tip:** After rebooting, verify that the settings persist by checking them again in LACT before launching games.

---

## Related Guides

* [**Troubleshooting Hub**](../README.md#troubleshooting) — All common troubleshooting guides