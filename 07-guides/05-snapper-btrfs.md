# Snapper Btrfs with Automatic Boot Entries

---

## Table of Contents

- [Important Requirements](#important-requirements)
- [Installation & Setup](#installation-setup)
  - [Step 1: Update System](#step-1-update-system)
  - [Step 2: Install Required Packages](#step-2-install-required-packages)
  - [Step 3: Configure Btrfs Snapshots](#step-3-configure-btrfs-snapshots)
  - [Step 4: Set Up rEFInd Integration](#step-4-set-up-refind-integration)
- [What's Next](#whats-next)
  - [Using Snapshots](#using-snapshots)
- [Troubleshooting](#troubleshooting)
  - [Snapshots Not Appearing?](#snapshots-not-appearing)
  - [Secure Boot Conflicts](#secure-boot-conflicts)
- [Advanced Configuration](#advanced-configuration)
  - [Custom Snapshot Configurations](#custom-snapshot-configurations)
  - [Manual Snapshot Creation](#manual-snapshot-creation)
- [Related Guides](#related-guides)

---

`PikaOS` supports automatic `Btrfs` snapshots on package operations with bootable entries in `rEFInd`. This guide covers the complete setup process.

---

## Important Requirements

Before proceeding, ensure your system meets these requirements:

1. **Boot partition MUST be labelled "`PikaOS`"** - check this in `gparted` or `blivet`
2. **`LUKS` encryption is NOT supported** with this configuration
3. **`UKIs` (`Unified Kernel Images`) are incompatible** with `Secure Boot` when using `Snapper`

> ⚠️ **Warning:** If you're unsure about your setup, verify these requirements before proceeding to avoid boot issues.

---

## Installation & Setup

### Step 1: Update System

```bash
pikman update
```

### Step 2: Install Required Packages

Install `Snapper` and related tools from the `PikaOS` repository:

```bash
pikman install snapper snapper-gui
```

### Step 3: Configure Btrfs Snapshots

Create the default snapshot configuration for your root filesystem:

```bash
sudo snapper create-config /
```

### Step 4: Set Up rEFInd Integration

Enable automatic boot entry creation for snapshots:

```bash
sudo `mkdir` -p /var/lib/refind-btrfs
sudo `chmod` 755 /var/lib/refind-btrfs
`pikman` install `pika-refind-btrfs-hooks` `refind-btrfs`
sudo `systemctl` enable `refind-btrfs` --now
```

---

## What's Next

After completing the setup, **reboot your system**. You should see:

- Two new sets of entries per installed kernel in `rEFInd`
- Base boot entries for each kernel
- Snapshot entries listing available rollback points

### Using Snapshots

**To access snapshots:**
1. Boot into `rEFInd`
2. Press **Tab** on snapshot entries to browse available versions
3. Select a snapshot to boot from that point in time

> 💡 **Tip:** To declutter the boot menu, consider reducing the number of installed kernels via `PikaOS` Welcome app or kernel manager.

---

## Troubleshooting

### Snapshots Not Appearing?

Check if `Snapper` is properly configured:

```bash
sudo `snapper` list
```

If no snapshots appear, verify your boot partition label:

```bash
`lsblk` -f | `grep` `PikaOS`
```

### Secure Boot Conflicts

`Snapper` with `UKIs` may cause issues when `Secure Boot` is enabled. Consider:
- Disabling `UKI` usage in kernel parameters
- Using standard kernel images instead
- Following the [Secure Boot Setup Guide](./04-secure-boot.md) for proper configuration

---

## Advanced Configuration

### Custom Snapshot Configurations

For advanced users, customize snapshot creation rules:

```bash
sudo `snapper` create-config / --type `SINGLE` --after-options 'retention=5'
```

This creates snapshots with a retention policy of 5 versions.

### Manual Snapshot Creation

Create manual snapshots for specific points (e.g., before major updates):

```bash
sudo `snapper` create --description "Before update" --type `single`
```

---

## Related Guides

* [**Secure Boot Setup Guide**](./04-secure-boot.md) — Secure boot configuration reference