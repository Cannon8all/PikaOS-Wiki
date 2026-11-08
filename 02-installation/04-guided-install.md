# PikaOS Guided Installation Guide

---

## Table of Contents

- [Critical Warning Before You Begin](#critical-warning-before-you-begin)
- [Installation Overview](#installation-overview)
  - [Installation Flow Chart](#installation-flow-chart)
- [Selecting Automatic Partitioning](#selecting-automatic-partitioning)
  - [Initial Installation Screen](#initial-installation-screen)
- [Selecting the Installation Disk](#selecting-the-installation-disk)
  - [Step-by-Step Disk Selection](#step-by-step-disk-selection)
  - [Understanding Disk Options](#understanding-disk-options)
- [Advanced Configuration Options](#advanced-configuration-options)
  - [Filesystem Selection](#filesystem-selection)
  - [Directory Separation Options](#directory-separation-options)
  - [Swap Configuration Options](#swap-configuration-options)
  - [Bootloader (rEFInd) Configuration](#bootloader-refind-configuration)
- [Special Notes for MSI Motherboard Users](#special-notes-for-msi-motherboard-users)
  - [MSI-Specific Boot Setting](#msi-specific-boot-setting)
- [Confirming Changes Before Installation](#confirming-changes-before-installation)
  - [Review Summary Screen](#review-summary-screen)
  - [Starting Installation](#starting-installation)
- [Installation Progress Tracking](#installation-progress-tracking)
  - [What Happens During Installation](#what-happens-during-installation)
- [Related Guides](#related-guides)
- [Troubleshooting Installation Issues](#troubleshooting-installation-issues)
  - [Common Problems & Solutions](#common-problems-solutions)
- [Quick Reference: Recommended Settings](#quick-reference-recommended-settings)
  - [For Most Users (Default Configuration)](#for-most-users-default-configuration)
  - [For Minimal Systems (<128GB Drive)](#for-minimal-systems-128gb-drive)
  - [For Power Users & Workstations](#for-power-users-workstations)
- [Advanced: Customizing Post-Installation](#advanced-customizing-post-installation)
  - [After Installation: BTRFS Optimization](#after-installation-btrfs-optimization)
  - [After Installation: Zram Configuration](#after-installation-zram-configuration)

---

**Complete walkthrough of automatic partitioning with advanced configuration options.** This guide covers filesystem selection, home directory separation, swap configuration, and bootloader settings for your PikaOS installation.

---

## Critical Warning Before You Begin

> ⚠️ **BACKUP WARNING:** Before installing, it is your responsibility to back up all data. This will erase all the data on the disk and cannot be undone.
>
> **Ensure you have backed up any important files before proceeding with installation.** Data loss during installation is permanent and irreversible.

---

## Installation Overview

The guided installer provides an intuitive interface for automatic partitioning, suitable for most users while offering advanced options for customization.

### Installation Flow Chart

```
Start → Select Disk → Advanced Options → Review Changes → Install → Reboot
  ↓              ↓             ↓               ↓            ↓         ↓
`USB` Boot   Choose Target    Configure       Confirm All  Begin      First Boot
                      Partitioning     Settings        Setup
```

---

## Selecting Automatic Partitioning

### Initial Installation Screen

During installation, you'll see two primary options:

| Option | Description | Best For |
| :--- | :---: | :--- |
| **Automatically Partition The Drive** (Top option) | Full automatic setup with optional advanced settings | Most users, single-boot systems |
| **Manual Partitioning** (Advanced) | Manual control over every partition and mount point | Advanced users, custom configurations |

> 💡 **Tip:** For this guide, select **"Automatically Partition The Drive"** — the top option. This provides the best balance of automation and customization for typical installations.

---

## Selecting the Installation Disk

### Step-by-Step Disk Selection

1. **Locate yellow box** labeled **(No Disk Selected for Installation)**
2. Click to open disk selection window
3. View available storage devices with capacity information
4. **Select your target drive** (typically shows brand, model, and size)
5. Confirm selection by clicking the yellow arrow button

*Expected result:* Yellow box updates to show selected disk name and capacity.

> ⚠️ **Warning:** Double-check you've selected the correct drive! Installing to the wrong disk will erase all data on that device permanently.

### Understanding Disk Options

| Column | Information Provided | What to Look For |
| :--- | :---: | :--- |
| **Device** | Device identifier (e.g., `/dev/nvme0n1`) | Technical reference if needed |
| **Type** | Storage type (`NVMe`, `SATA` SSD, `HDD`) | Helps identify physical location |
| **Capacity** | Total drive size in GB/TB | Match expected drive capacity |
| **Used Space** | Current data on drive | Verify it's the correct target |

> 💡 **Tip:** If you see multiple drives and aren't sure which is which, check capacities against your system specifications. The largest drive is typically the main system disk in dual-boot setups.

---

## Advanced Configuration Options

Click **"Advanced Options"** button to access detailed configuration settings before installation begins.

### Filesystem Selection

PikaOS offers three filesystem options for your root partition:

| Filesystem | Default | Features | Best For |
| :--- | :---: | :--- | :--- |
| **`BTRFS`** | ✅ Selected | Copy-on-write, built-in snapshots, compression | Most users, system protection |
| **`EXT4`** | ❌ | Traditional, stable, widely supported | Maximum compatibility, simplicity |
| **`XFS`** | ❌ | High-performance for large files, servers | Enterprise use, media workloads |

### `BTRFS` (Recommended Default)

**Advantages:**
- Built-in snapshot capability for system recovery
- Automatic compression saves disk space
- Copy-on-write prevents data corruption
- Seamless updates with rollback capability

**Best for:** Most users who want automatic backup and recovery features.

> 💡 **Tip:** `BTRFS` is the default because it provides the best balance of modern features and ease of use for typical desktop installations.

### `EXT4` (Traditional Choice)

**Advantages:**
- Extremely stable and well-tested
- Maximum compatibility with all Linux tools
- Lower CPU overhead than `BTRFS`
- Simpler troubleshooting if issues arise

**Best for:** Users who prioritize stability over features or have specific compatibility requirements.

### `XFS` (Performance Option)

**Advantages:**
- Excellent performance for large files (>1GB)
- Ideal for media servers and content creation
- Scalable to very large file systems
- Good enterprise support

**Best for:** Power users, servers, or workstations handling large media files.

---

### Directory Separation Options

Choose how your home directory is structured relative to the system:

| Option | Description | Best For |
| :--- | :---: | :--- |
| **No** (All on root) | Single partition, no `/home` separation | Simple setups, small drives (<128GB) |
| **Yes, via Subvolume** *(Default)* | `BTRFS` subvolume for `/home`, system shares disk | Most users with `BTRFS` |
| **Yes, via Partition** | Separate physical partition for `/home` | Users wanting complete separation |

### No Separation (Single Partition)

**Configuration:**
- Root (`/`) contains all data including user files
- Simple structure, no complexity
- Reinstalling requires manual backup of home directory

**Best for:** Small drives where every GB counts, or users who prefer simplicity.

> 💡 **Tip:** If you choose this option and need to reinstall later, remember to back up `/home` manually before formatting the root partition.

### Yes, via Subvolume (Recommended for `BTRFS`)

**Configuration:**
- System creates dedicated subvolume for home directory
- Both system and user data on same physical disk
- Easy backup with `BTRFS` snapshot tools
- Clean separation without partition overhead

**Best for:** Most users who want the benefits of separation while maintaining simplicity.

> 💡 **Recommendation:** Select **"Yes, via a Subvolume"** if using `BTRFS` — it provides easy backup and snapshot capabilities while maintaining separation between system and user data.

### Yes, via Partition (Complete Separation)

**Configuration:**
- System creates distinct physical partition for `/home`
- Independent sizing options available
- Reinstalling root doesn't affect home directory
- More complex setup process

**Best for:** Users who frequently reinstall systems or want maximum data isolation.

> ⚠️ **Note:** Partition-based separation is not available with `EXT4` filesystem — only works with `BTRFS` or during manual partitioning.

---

### Swap Configuration Options

Choose how virtual memory (swap) is configured:

| Option | Default | Description | Best For |
| :--- | :---: | :--- | :--- |
| **None/Zram** | ✅ Selected | Compressed RAM-based swap, no disk file | Most users, SSD longevity |
| **½ System RAM** | ❌ | Swap file = 50% of installed RAM | Systems with <8GB RAM |
| **Equal to RAM** | ❌ | Swap file = 100% of installed RAM | Low-RAM systems (<4GB) |
| **Custom Size** | ❌ | Manual swap size in GB increments | Advanced users, specific needs |

### None/Zram (Recommended Default)

**How it works:**
- No traditional swap file on disk
- Uses compressed memory pages in RAM instead
- Faster than disk-based swap
- Reduces SSD wear by eliminating write cycles

**Benefits:**
- Better performance for modern systems with ≥8GB RAM
- Extends SSD lifespan (no additional writes)
- Automatically adjusts to memory pressure

> 💡 **Recommendation:** For most users, `Zram` is sufficient and reduces wear on SSDs while providing fast virtual memory when needed.

### Equal System RAM

**When to use traditional swap:**
- Systems with <8GB total RAM
- Need hibernation support (requires swap ≥ RAM size)
- Running memory-intensive applications (video editing, VMs)
- Specific software requirements

> 💡 **Tip:** If you have 4GB or less of physical RAM, select "Equal to System Ram" to ensure adequate virtual memory.

### Custom Swap Size

**Manual configuration for advanced users:**

| Scenario | Recommended Size | Notes |
| :--- | :---: | :--- |
| **Hibernation required** | ≥ Total RAM size | Must equal or exceed physical memory |
| **Light usage** | 2-4 GB | Minimal virtual memory needs |
| **Heavy workloads** | 8-16 GB | Video editing, VMs, development |

> ⚠️ **Warning:** Setting swap too large wastes disk space. For most desktop users, `Zram` provides better performance and flexibility.

---

### Bootloader (`rEFInd`) Configuration

PikaOS uses `rEFInd` as the default bootloader, providing a modern boot menu interface. Configure your preferred behavior:

### `rEFInd` Display Options

| Option | Description | Behavior |
| :--- | :---: | :--- |
| **Skip Selection and Boot Automatically** | No boot menu shown | Boots last-selected OS immediately |
| **Show Selection** (Default) | Full `rEFInd` interface at every boot | Manual selection required each time |
| **Show with Timeout** | Menu appears with countdown timer | Auto-boots after timeout expires |

### Choosing Your Boot Strategy

**Skip Selection and Boot Automatically:**
- Best for single-boot systems where you never change OS
- Fastest boot experience (no menu delay)
- Still accessible via Shift/Arrow keys during boot

**Show Selection (Default):**
- Ideal for dual-boot setups with Windows or other Linux distros
- Allows easy OS switching at startup
- No timeout needed — choose when ready

**Show Selection with Timeout:**
- Perfect compromise: see options but auto-boots eventually
- Recommended timeout: 5-10 seconds
- Best for occasional multi-OS users

> 💡 **Tip:** If you're dual-booting, select **"Show Selection"** to always have the option to choose your OS at startup. For single-boot PikaOS systems, automatic boot is faster and simpler.

---

## Special Notes for `MSI` Motherboard Users

**`MSI` systems require additional configuration** for proper `UEFI` compatibility:

### `MSI`-Specific Boot Setting

1. During installation, click **"Advanced Options"**
2. Navigate to **Boot** tab within advanced settings
3. Select **"`BOOTX64` Mode (`MSI` Compatibility Mode)"**
4. Continue with installation as normal

> 💡 **Why this matters:** This setting ensures compatibility with `MSI`'s `UEFI` implementation and prevents boot issues after installation. Without it, you may encounter "No bootable device" errors despite correct `BIOS` configuration.

---

## Confirming Changes Before Installation

### Review Summary Screen

After configuring all options, the installer presents a summary of planned changes:

**What to verify:**
- [ ] Correct disk selected (double-check capacity and name)
- [ ] Filesystem matches your preference (`BTRFS`/`EXT4`/`XFS`)
- [ ] Home directory separation configured as desired
- [ ] Swap size appropriate for your needs
- [ ] Bootloader settings match your workflow

### Starting Installation

Once you've confirmed all details:

1. Click red **(Confirm & Install PikaOS)** button
2. System begins partitioning and copying files
3. Progress indicator shows installation status
4. Estimated time remaining displayed (typically 15-30 minutes)

*Expected result:* Installation completes successfully with confirmation message.

> ⚠️ **Warning:** Once you click "Confirm & Install," the process cannot be interrupted without risking system damage. Ensure all settings are correct before proceeding.

---


## Related Guides

* [**`BIOS` Checklist**](../01-getting-started/03-bios-checklist.md) — Configure `BIOS` settings before installation
* [**Creating Install Media**](02-creating-install-media.md) — Write `ISO` to `USB` drive, verify integrity
* [**Booting the Installer**](03-booting-the-installer.md) — Boot modes, `BIOS` settings, troubleshooting boot issues
* [**Post-Install Setup**](05-post-install-setup.md) — Essential initial configuration steps after installation completes
* [**Dual Boot Windows**](06-dual-boot-windows.md) — Safe Windows coexistence configuration and setup
* [**Secure Boot Setup**](../07-guides/04-secure-boot.md) — Enable Secure Boot for enhanced security (optional)

---

## Troubleshooting Installation Issues

### Common Problems & Solutions

| Issue | Likely Cause | Solution |
| :--- | :---: | :--- |
| **Installation hangs at partitioning** | Disk incompatible with filesystem | Try `EXT4` instead of `BTRFS` |
| **No disk appears in selection** | SATA mode incorrect in `BIOS` | Change to AHCI, restart installer |
| **Insufficient space error** | Drive too small or already partitioned | Use different drive or wipe existing partitions first |
| **Bootloader installation fails** | `MSI` motherboard compatibility issue | Enable `BOOTX64` Mode before proceeding |

> 💡 **Tip:** If you encounter persistent issues, try the manual partitioning option for more control over the process.

---

## Quick Reference: Recommended Settings

### For Most Users (Default Configuration)
- **Filesystem:** `BTRFS` (default)
- **Home Separation:** Yes, via Subvolume
- **Swap:** None/`Zram` (default)
- **Bootloader:** Show Selection

**Why these defaults work well:**
- Automatic snapshots for system recovery
- Clean separation of user and user data
- No SSD wear from traditional swap
- Easy OS switching at startup (dual-boot friendly)

### For Minimal Systems (<128GB Drive)
- **Filesystem:** `EXT4` or `BTRFS` with compression
- **Home Separation:** No (single partition)
- **Swap:** None/`Zram`
- **Bootloader:** Skip Selection and Boot Automatically

**Rationale:** Maximizes available space for applications and user data.

### For Power Users & Workstations
- **Filesystem:** `BTRFS` with compression enabled
- **Home Separation:** Yes, via Partition (for easy backup)
- **Swap:** Custom size based on workload (4-16GB)
- **Bootloader:** Show Selection with 10-second timeout

**Rationale:** Maximum flexibility and control for advanced workflows.

---

## Advanced: Customizing Post-Installation

### After Installation: `BTRFS` Optimization

If you chose `BTRFS`, consider these post-install optimizations:

```bash
# Enable compression for all files (saves space)
sudo btrfs property set / compress=zstd

# Check current filesystem usage
btrfs filesystem df /

# View available snapshots
snapper --list
```

### After Installation: `Zram` Configuration

`Zram` is enabled by default. To customize settings:

```bash
# Edit `Zram` configuration
sudo nano /etc/default/zram-config

# Adjust compression algorithm and size as needed
```

> 💡 **Tip:** These advanced configurations are optional. The defaults work well for most use cases without additional tuning.
