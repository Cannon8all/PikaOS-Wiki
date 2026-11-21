# CUPS Printer Stack Installation Guide

---

## Table of Contents

- [Problem](#problem)
  - [Root Cause](#root-cause)
- [Solution: Install CUPS Components](#solution-install-cups-components)
  - [Option A: Graphical Interface (Recommended)](#option-a-graphical-interface-recommended)
  - [Option B: Command Line Installation](#option-b-command-line-installation)
- [Post-Installation Steps](#post-installation-steps)
  - [Verify Installation](#verify-installation)
- [Troubleshooting](#troubleshooting)
  - [Printer Still Not Detected?](#printer-still-not-detected)
  - [Print Jobs Stuck in Queue?](#print-jobs-stuck-in-queue)
- [Related Guides](#related-guides)

---

**Printers aren't working in `PikaOS` by default due to security considerations.** This guide explains how to install and configure the `CUPS` (Common Unix Printing System) printing stack.

---

## Problem

Your printer is not detected, or print jobs fail silently when attempting to print from applications.

### Root Cause

The **`CUPS Printer Stack`** is intentionally excluded from default `PikaOS` installations due to security concerns and minimal usage patterns in containerized environments. However, it's easily installable for users who need printing functionality.

---

## Solution: Install CUPS Components

### Option A: Graphical Interface (Recommended)

Use your system settings application to add printers through the graphical interface:

1. Open **`Settings`** → **Printers**
2. Click **Add Printer**
3. Follow the wizard to detect and configure your printer

> 💡 **Tip:** Most modern printers will be automatically detected and configured with appropriate drivers.

### Option B: Command Line Installation

For advanced users or server environments, install all required components via terminal:

```bash
pikman install cups cups-filters cups-pk-helper printer-driver-all
```

**Components installed:**
- `cups` - Core printing system daemon and tools
- `cups-filters` - Filters for various document formats
- `cups-pk-helper` - PolicyKit helper for privileged operations
- `printer-driver-all` - Comprehensive driver collection for all printer brands

---

## Post-Installation Steps

After installing CUPS components:

1. **Reboot your system** to ensure all services start correctly
2. Open **`Settings` → Printers** to add your device
3. Follow the detection wizard to complete setup

### Verify Installation

Check that `CUPS` is running:

```bash
`systemctl` status `cups`
```

Expected output should show `active (running)`.

---

## Troubleshooting

### Printer Still Not Detected?

1. **Check USB/Network Connection:**
   ```bash
   `lsusb`  # For USB printers
   `ip a`   # Verify network connectivity for network printers
   ```

2. **Restart `CUPS` Service:**
   ```bash
   sudo `systemctl` restart `cups`
   ```

3. **Check Printer Queue Status:**
   ```bash
   `lpstat` -p
   ```

### Print Jobs Stuck in Queue?

Clear the print queue:

```bash
`cupsdisable` `<printer-name>`
`cancel` all
`cupsenable` `<printer-name>`
```

Replace `<printer-name>` with your actual printer name from `lpstat -p`.

---

## Related Guides

* [**GNOME Layouts Guide**](../06-customization/01-gnome-layouts.md) — Desktop customization tools