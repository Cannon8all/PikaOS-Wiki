# NVIDIA GTK GSK Renderer Crash Fix

---

## Table of Contents

- [Problem](#problem)
- [Root Cause](#root-cause)
- [Solution](#solution)
  - [Option A: Upgrade Your NVIDIA Driver (Recommended)](#option-a-upgrade-your-nvidia-driver-recommended)
  - [Option B: Switch Back to OpenGL GSK Renderer](#option-b-switch-back-to-opengl-gsk-renderer)
    - [Step 1: Create Configuration Directory](#step-1-create-configuration-directory)
    - [Step 2: Create Environment Config File](#step-2-create-environment-config-file)
    - [Step 3: Add OpenGL Renderer Setting](#step-3-add-opengl-renderer-setting)
    - [Step 4: Log Out and Back In](#step-4-log-out-and-back-in)
- [Related Guides](#related-guides)

---

## Problem

**GTK applications fail to open** or crash immediately when using the proprietary NVIDIA driver.

---

## Root Cause

Some versions of the **proprietary NVIDIA driver** are incompatible with the **GSK Vulkan Renderer** that GTK 4.16+ uses by default. This causes any GTK-based application (like GNOME Software, Settings, etc.) to crash on startup.

> ⚠️ **Warning:** This issue specifically affects systems running both NVIDIA proprietary drivers and newer GTK applications using the Vulkan renderer.

---

## Solution

You have two options:

### Option A: Upgrade Your NVIDIA Driver (Recommended)

Update your system to get the latest NVIDIA driver version, which may include fixes for this compatibility issue:

```bash
pikman upgrade
```

After upgrading, reboot and test if GTK applications work properly.

---

### Option B: Switch Back to OpenGL GSK Renderer

If upgrading doesn't resolve the issue, you can force GTK to use the OpenGL renderer instead of Vulkan:

#### Step 1: Create Configuration Directory

```bash
mkdir -p ~/.config/environment.d/
```

#### Step 2: Create Environment Config File

```bash
touch ~/.config/environment.d/gsk.conf
```

#### Step 3: Add OpenGL Renderer Setting

Add this line to the configuration file:

```bash
echo "GSK_RENDERER=opengl" | tee -a ~/.config/environment.d/gsk.conf
```

#### Step 4: Log Out and Back In

For the environment variable to take effect, log out of your session and back in (or reboot):

```bash
sudo reboot
```

> 💡 **Tip:** This setting applies system-wide to all GTK applications. You can verify it's active by checking if GTK apps launch without crashing.

---

## Related Guides

* [**Troubleshooting Hub**](../README.md#troubleshooting) — All common troubleshooting guides