# Kernel manager

## Main Page

![kernel-manager-main-page.png](/kernel-manager-main-page.png)

## PikaOS Kernel Manager Documentation

### Overview

The PikaOS Kernel Manager is a system utility that provides information about your current kernel version and scheduling system, while also showing the latest available stable kernel version.

### Interface Elements

#### Version Information

- **Latest Stable Version**: Displays the most recent stable kernel version available (shown as 6.15.3 in the screenshot)

  - Displayed in green when matching the running version
  - Displayed in red when the running version is older

- **Running Version**: Shows the currently installed kernel version (6.15 in the screenshot)

  - Displayed in green when matching the latest stable version
  - Displayed in red when older than the latest stable version

- **Running Kernel**: Displays the full kernel identifier including the OS-specific build (6.15.0-pikaos in the screenshot)

- **Running Sched**: Shows the active scheduler (sched_ext: lawd in the screenshot), indicating the system is using the extensible scheduler framework with the "lawd" scheduler

#### Navigation Buttons

- **Left Button**: Takes you to the SCX (Scheduler eXtended) configuration page where you can modify scheduler settings
- **Right Button**: Navigates to the kernel version management page where you can view available kernels and perform updates

### Status Indicators

The middle two badges (Latest Stable Version and Running Version) will appear:

- **Accent Color** when the running version matches the latest stable version
- **Red** when the running version is older than the latest stable version

This visual cue helps users quickly identify if their system needs a kernel update.

### Usage Recommendations

- Check this page periodically to ensure your kernel is up-to-date
- Visit the kernel version page (right button) to update when the running version is outdated
- Use the SCX config page (left button) to optimize scheduler settings for your workload

## Kernel Version Page

![kernel-manager-kernel-version-page.png](/kernel-manager-kernel-version-page.png)

## PikaOS Kernel Manager - Available Kernel Packages Documentation

### Overview

This screen displays a list of available kernel packages that can be installed on PikaOS. Each entry includes version details, package names, and installation status.

### Interface Elements

#### Kernel Package Entries

Each kernel version is displayed in the following format:

- **Version Label** (e.g., _PikaOS Linux Kernel 6.15.0_)
- **Version & Build Identifier** (e.g., _6.15.0-10|pika8_)
- **Package Name** (e.g., _linux-image-6.15.0-pikaos_)
- **Status Indicator** (✔)
  - ✔ **installed** → Currently running kernel (e.g., _6.15.0-rc5_)
  - ✔ (without label) → Available for installation

#### Example Breakdown:

```text
PikaOS Linux Kernel 6.15.0
6.15.0-10|pika8    ✔ linux-image-6.15.0-pikaos ✔
```

- **Version**: 6.15.0 (stable)
- **Build**: `10|pika8` (OS-specific compilation)
- **Package**: `linux-image-6.15.0-pikaos` (installable via package manager)
- **Status**: Available (✔) but not installed (no "installed" label).

### Key Observations

1. **Installed Kernel**

- _6.15.0-rc5_ is marked as **✔ installed**, indicating it is the currently running kernel (matches the previous screenshot).
- This is a **release candidate (rc5)**, suggesting the system is testing an upcoming stable version.

2. **Stable vs. Development Kernels**

- **Stable**: 6.14.5–6.15.0 (non-"rc" versions).
- **Testing/RC**: 6.15.0-rc5, 6.15.0-rc6 (pre-release).

3. **Actionable Items**

- Users can select any non-installed kernel for updates/downgrades.
- The **Back** button returns to the previous screen (Kernel Manager overview).

### Usage Recommendations

- **Stability vs. Features**:
  - Choose stable kernels (e.g., _6.15.0_) for production systems.
  - Testing/RC kernels (e.g., _6.15.0-rc6_) may offer newer features but could be less stable.
- **Downgrades**: Older kernels (e.g., _6.14.7_) are listed for compatibility troubleshooting.
- **Installation**: Clicking an entry (where ✔ is present) initiates installation.

### Visual Cues

- **✔ installed** → Bold/highlighted to distinguish the active kernel.
- **✔ (standalone)** → Available for selection.
- No indicator → Kernel not available in repositories (none shown here).

This screen ensures users have full control over kernel management while maintaining clarity about the current system state.

## SCX Scheduler Page

![kernel-manager-scx-page.png](/kernel-manager-scx-page.png)

## PikaOS Kernel Manager - Scheduler Configuration Documentation

### Overview

This screen allows users to configure the Sched-Ext (SCX) scheduler, which replaces the default Linux kernel scheduler. The interface provides options to select different scheduler implementations and modes optimized for specific workloads.

### Interface Elements

#### Current Scheduler Status

- **Running Sched**: Displays the active scheduler (e.g., "sched_ext: lavd")

#### Scheduler Selection Section

- **Default Kernel Scheduler Option**
  - "Disable SCX and use default kernel scheduler" - Reverts to the standard Linux BORE scheduler

#### Scheduler Mode Selection Section

When a scheduler is selected, this section displays:

- Default modes that automatically populate and overwrite the Scheduler Flags row
- Example profiles for BPF-LAND:
  - **Multimedia Mode**: Optimized for audio processing and multimedia applications
  - **Gaming Mode**:
    - Prioritizes performance cores (P-cores) on Intel CPUs
    - Optimizes for Ryzen X3D's cache-dense CCDs
    - General high-performance tuning for games

#### Scheduler Flags

- Displays active tuning flags (e.g., "m performance")

#### Navigation and Actions

- **Back**: Returns to previous screen
- **Apply**: Saves scheduler configuration changes
