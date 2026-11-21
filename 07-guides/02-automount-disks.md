# Auto-Mount Disks with GNOME Disk Utility

---

## Table of Contents

- [Problem](#problem)
  - [Root Cause](#root-cause)
- [Solution: Configure Persistent Mounts](#solution-configure-persistent-mounts)
  - [Step 1: Install GNOME Disk Utility](#step-1-install-gnome-disk-utility)
  - [Step 2: Launch Disk Utility](#step-2-launch-disk-utility)
- [Configure Mount Options](#configure-mount-options)
  - [1. Select Target Drive](#1-select-target-drive)
  - [2. Access Mount Options](#2-access-mount-options)
  - [3. Configure Persistent Mounting](#3-configure-persistent-mounting)
  - [4. Set Display Name](#4-set-display-name)
- [Complete Configuration](#complete-configuration)
  - [Verification Steps](#verification-steps)
- [Important Notes](#important-notes)
  - [Steam Integration](#steam-integration)
  - [File System Compatibility](#file-system-compatibility)
- [Troubleshooting](#troubleshooting)
  - [Disk Still Not Mounting After Reboot?](#disk-still-not-mounting-after-reboot)
  - [GUI Options Grayed Out?](#gui-options-grayed-out)
- [Related Guides](#related-guides)

---

**Additional disks not staying mounted after clicking them in a file manager is a common issue.** This guide shows how to configure persistent disk mounting using the GUI-based `GNOME Disk Utility`.

---

## Problem

When you click on additional drives or partitions in your graphical file manager, they mount temporarily but **don't stay mounted after reboot**. You need to manually remount them each time.

### Root Cause

This occurs because disks are not properly configured in `/etc/fstab` (the system file that defines persistent mounts). While you could edit this file manually via command line, the `GNOME Disk Utility` provides a user-friendly graphical interface for this task.

---

## Solution: Configure Persistent Mounts

### Step 1: Install GNOME Disk Utility

Install the disk management tool from `PikaOS` repositories:

```bash
pikman install gnome-disk-utility
```

**Alternative installation methods:**
- **Software Center:** Search for "Disks" in Cosmic Store/Discover
- **Application Menu:** Type `disks` to launch the GUI utility

### Step 2: Launch Disk Utility

Open the application from your menu or by running:

```bash
disks
```

The application will display as **"Disks - Disk Image Writer"** or simply **"Disks"**.

---

## Configure Mount Options

> 💡 **Note:** Your actual device names, serial numbers, and UUIDs will differ from the examples below. Always verify you're configuring the correct drive.

### 1. Select Target Drive

1. In the left sidebar, **click on your target disk/partition**
2. The main panel shows information about the selected volume
3. Verify it's the correct drive by checking size and mount point

### 2. Access Mount Options

1. Look for the **second box from the left** under the partition diagram
2. This section is labeled **"Additional Partition Options"** or similar
3. Click to expand the options panel

### 3. Configure Persistent Mounting

#### Deselect User Session Defaults

- **Uncheck** the option labeled `User Session Defaults`
- This allows you to customize mount behavior beyond user session settings

#### Enable System Startup Mount

- **Check** the box for `Mount at system startup`
- This ensures the disk mounts automatically when your system boots

### 4. Set Display Name

Enter a **user-friendly display name** for the drive:
- This name appears in your file manager sidebar
- Also visible in Steam's external storage list (if using Steam)
- Choose something descriptive and easy to identify

> 💡 **Tip:** Use consistent naming conventions like "Games Drive", "Media Storage", or "Backup Volume" for clarity.

---

## Complete Configuration

After making all changes:

1. Click **OK** to save your mount configuration
2. The drive should now be mounted immediately
3. Verify it remains accessible after rebooting

### Verification Steps

To confirm your configuration is correct:

```bash
# Check if disk is in fstab
`cat` `/etc/fstab` | `grep` -i your-drive-label

# List currently mounted filesystems
`mount` | `grep` your-drive-label

# View mount options
`findmnt` your-drive-label-or-mount-point
```

---

## Important Notes

### Steam Integration

**If `Steam` was open during configuration changes:**
1. **Close `Steam` completely** (ensure it's not running in system tray)
2. **Reopen `Steam`** to refresh the drive list
3. Your newly mounted drive should now appear in `Steam`'s external storage options

> 💡 **Tip:** Always close `Steam` before modifying disk configurations to avoid stale device lists.

### File System Compatibility

- Ensure your partition uses a **Linux-compatible filesystem** (`EXT4`, `XFS`, `Btrfs`) for best compatibility
- `NTFS`/`FAT32` partitions may have different mount requirements
- Encrypted drives require additional configuration steps

---

## Troubleshooting

### Disk Still Not Mounting After Reboot?

1. **Verify fstab entry exists:**
   ```bash
   `cat` `/etc/fstab`
   ```

2. **Check mount point permissions:**
   ```bash
   ls -la /mnt/your-mount-point
   sudo chown $USER:$USER /mnt/your-mount-point
   ```

3. **Review system logs for errors:**
   ```bash
   `journalctl` -xe | `grep` -i mount
   ```

### GUI Options Grayed Out?

- Ensure you're running Disk Utility with appropriate permissions
- Some drives may require unmounting before configuration changes
- Check if the drive is in use by another process

---

## Related Guides

* [**GNOME Layouts Guide**](../06-customization/01-gnome-layouts.md) — Desktop customization tools