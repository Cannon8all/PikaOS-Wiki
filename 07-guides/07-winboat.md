# Winboat Installation Guide

---

## Table of Contents

- [Pre-Requisites](#pre-requisites)
- [Enable Virtualization in BIOS](#enable-virtualization-in-bios)
  - [Common BIOS Setting Names for Intel](#common-bios-setting-names-for-intel)
  - [Common BIOS Setting Names for AMD](#common-bios-setting-names-for-amd)
- [Install Podman Components](#install-podman-components)
- [Install FreeRDP](#install-freerdp)
- [Download and Install Winboat](#download-and-install-winboat)
  - [Step 1: Download Winboat](#step-1-download-winboat)
  - [Step 2: Install the Package](#step-2-install-the-package)
- [First-Time Configuration](#first-time-configuration)
  - [Launch Winboat](#launch-winboat)
  - [Initial Setup Steps](#initial-setup-steps)
- [System Performance Considerations](#system-performance-considerations)
  - [Performance Impact](#performance-impact)
- [Optimize Performance](#optimize-performance)
  - [Disable Automatic Container Startup](#disable-automatic-container-startup)
  - [When to Use On-Demand Mode](#when-to-use-on-demand-mode)
- [Troubleshooting](#troubleshooting)
  - [Container Won't Start?](#container-wont-start)
  - [Connection Issues with FreeRDP?](#connection-issues-with-freerdp)
- [Related Guides](#related-guides)

---

`Winboat` enables you to run `Windows` applications in a containerized virtual environment using `Podman` and `FreeRDP`. This guide covers installation, configuration, and optimization.

---

## Pre-Requisites

Before installing Winboat, ensure your system meets these requirements:

- **RAM:** At least 4 GB (8+ GB recommended)
- **CPU:** Minimum 2 cores (4+ cores recommended)
- **Virtualization:** Must be enabled in `BIOS`/`UEFI` settings
- **Software:** `Podman` and `Podman Compose` installed
- **Display:** `FreeRDP` for remote desktop functionality

---

## Enable Virtualization in BIOS

During system startup, press the designated key to enter your motherboard's `BIOS`/`UEFI` setup:

**Common keys:** `Delete`, `F10`, `F1`, `F2` (consult your manual if unsure)

### Common `BIOS` Setting Names for `Intel`

- `Intel Virtualization Technology`
- `Intel VT-x` / `Intel VT`
- `Intel (VMX) Virtualization Technology`

### Common `BIOS` Setting Names for `AMD`

- `SVM Mode` (`Secure Virtual Machine`)
- `AMD` Virtualization
- `AMD-V`

| Brand | Navigation Path | Setting Name |
| :--- | :--- | :--- |
| **`ASUS`** | Advanced Mode > Advanced > CPU Configuration | `Intel VT` / `SVM Mode` |
| **`MSI`** | Overclocking > CPU Features | `Intel VT-x` / `SVM Mode` |
| **`Gigabyte`** | Tweaker > Advanced CPU Core Settings | `Intel VT` / `SVM Mode` |
| **`HP`** | Configuration > System Configuration | `Virtualization Technology` |
| **`Dell`** | Settings > Virtualization Support | `Virtualization` |
| **`Lenovo`** | Security > Virtualization | `Intel VT-x` / `AMD-V` |

> 💡 **Tip:** After enabling virtualization, save changes and `reboot` before proceeding with the installation.

---

## Install Podman Components

Install `Podman` and required dependencies from the `PikaOS` repository:

```bash
`pikman` i `podman` `podman-compose` `aardvark-dns`
```

**Components installed:**
- `podman` - Container runtime
- `podman-compose` - Compose file support
- `aardvark-dns` - `DNS` server for containers

---

## Install FreeRDP

`FreeRDP` provides the remote desktop functionality needed by `Winboat`. Choose one of two installation methods:

### Option A: Stable Version (Recommended) via Flatpak

```bash
`flatpak` install `com.freerdp.FreeRDP`
```

**Advantages:**
- Latest stable release
- Automatic updates through your package manager
- Best compatibility for most users

### Option B: Experimental Version via Repository

For the latest features and nightly builds, follow instructions at: [FreeRDP Pre-Builds Wiki](https://github.com/FreeRDP/FreeRDP/wiki/PreBuilds)

> ⚠️ **Warning:** The experimental version may have bugs or compatibility issues. Use only if you need specific features not available in the stable release.

---

## Download and Install Winboat

### Step 1: Download Winboat

Download the latest `.deb` package from the official website:

**Winboat Official Site:** <https://winboat.app/>

### Step 2: Install the Package

Navigate to your Downloads folder or run this command (adjust filename to match your download):

```bash
pikman i ~/Downloads/winboat-0.9.2-amd64.deb
```

> 💡 **Tip:** Replace `winboat-0.9.2-amd64.deb` with the actual version number you downloaded.

---

## First-Time Configuration

### Launch Winboat

Open the newly installed **`Winboat`** application from your application menu or launcher.

### Initial Setup Steps

1. **Toggle Docker to Podman:**
   - Open `Winboat`'s settings
   - Toggle the `docker` checkmark to enable `podman` mode
   
2. **Basic Configuration:**
   - Go to the **Configuration** menu (left sidebar)
   - Set **`FreeRDP` Port** to `3389` (default `RDP` port)

---

## System Performance Considerations

> 💡 **Important Note:** `Winboat` runs a containerized `Windows` environment in the background. By default, `Podman` and `Winboat` are configured to start automatically when your system boots.

### Performance Impact

- **Boot times** may increase slightly
- **`CPU` and `RAM`** resources consumed by background container
- **Lower-end systems** (4GB `RAM`, 2 cores) may experience noticeable slowdowns

---

## Optimize Performance

### Disable Automatic Container Startup

If you experience performance degradation on lower-end systems, configure `Winboat` to run only on demand:

1. Open **`Winboat`**
2. Navigate to **Configuration** menu (left sidebar)
3. Turn off the **Auto Start Container** toggle
4. Press **Save** to apply changes

**Benefits:**
- Faster boot times
- Lower idle resource usage
- Manual control over when `Windows` environment starts

### When to Use On-Demand Mode

Recommended for:
- Systems with limited `RAM` (<8 GB)
- Occasional use of `Windows` applications
- Desktop/laptop users prioritizing performance

Avoid on-demand mode if you frequently switch between `Linux` and `Windows` apps.

---

## Troubleshooting

### Container Won't Start?

Check `Podman` service status:

```bash
`systemctl` --user status `podman.socket`
`podman` info
```

### Connection Issues with FreeRDP?

Verify port `3389` is not blocked by firewall:

```bash
sudo `ufw` allow `3389`/tcp
```

---

## Related Guides

* [**Wiki Home**](../README.md) — Complete PikaOS documentation hub