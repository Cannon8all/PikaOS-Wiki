# Pikman GUI — Package Manager Interface

---

## Table of Contents

- [Main Updates Page](#main-updates-page)
- [Native Updates (APT)](#native-updates-apt)
  - [Overview](#overview)
  - [Description Tab](#description-tab)
  - [Additional Info Tab](#additional-info-tab)
  - [Download URIs Tab](#download-uris-tab)
  - [Transaction Window](#transaction-window)
- [Flatpak Updates](#flatpak-updates)
  - [Overview](#overview-flatpak)
- [Repository Management](#repository-management)
  - [Add Remote by URL](#add-remote-by-url)
  - [Add Remote by File](#add-remote-by-file)
  - [Installation Target Options](#installation-target-options)
- [Best Practices](#best-practices)
- [Troubleshooting](#troubleshooting)
  - [No updates available](#no-updates-available)
  - [Update commit fails](#update-commit-fails)
- [Related Guides](#related-guides)
- [Next Steps](#next-steps)

---

> 💡 **Overview:** The Pikman GUI provides a visual interface for managing packages from multiple sources including native `APT` repositories, `Flatpak` remotes, and cross-distribution containers. It shows available updates, manages third-party repositories, and simplifies package operations through an intuitive graphical interface.

---

## Main Updates Page

The main page displays:

- **Update counts** from each package manager
- **Sum total** of all available updates
- **Commit button** in the bottom-right corner to install all selected updates at once

---

## Native Updates (APT)

### Overview

This section shows a list of packages with upgrades available. Each row provides:

| Information | Description |
| :--- | :--- |
| **Currently installed version** | The version currently on your system |
| **New version** | The version you will receive, highlighted in the difference column |
| **Package Architecture** | The CPU architecture (`amd64`, `i386`, etc.) |

At the end of each row is a checkbox that marks the package for upgrade. Packages are selected by default.

### Description Tab

Click on any row to expand it and reveal:

- Full package description
- Detailed functionality information

### Additional Info Tab

View additional metadata:

| Field | Description |
| :--- | :--- |
| **Maintainer/Developer** | Name of the package maintainer |
| **Download Size** | Network bandwidth required |
| **Installed Size** | Disk space used after installation |

### Download URIs Tab

Shows the exact repository sources where packages are hosted.

### Transaction Window

The **Commit** page displays:

- All selected packages for upgrade
- Detailed transaction information
- Final confirmation before applying changes

---

## Flatpak Updates

### Overview

Similar to the native `APT` section, but includes additional fields:

| Information | Description |
| :--- | :--- |
| **Remote Name** | The `Flatpak` remote repository name |
| **Application ID** | Unique identifier for the application |
| **Version** | Current and available versions |
| **Branch** | Installation branch (e.g., stable, unstable) |

---

## Repository Management

### Add Remote by URL

Add a new `Flatpak` remote repository:

1. Enter the URL of `.flatpakrepo` file
2. Choose installation target: User or System
3. Click **Add** to confirm

### Add Remote by File

Provide a path to an existing `Flatpak` configuration file:

- Type the path manually, or press **Browse** to select a file
- Supports `.flatpakref` and `.flatpakrepo` files

### Installation Target Options

Same as "Add remote by URL":

| Option | Description |
| :--- | :--- |
| **User** | User-specific installation (portable across reinstalls) |
| **System** | System-wide installation (shared among all users) |

---

## Best Practices

- Keep automatic update checking enabled for security patches
- Only add trusted third-party repositories
- Regularly review and remove unused remotes
- Document custom mirrors for system restoration

---

## Troubleshooting

### No updates available

**Possible causes:**
- All packages are already up to date
- Internet connection issues preventing repository sync
- Repository servers experiencing downtime

**Solution:** Click the refresh/sync button in the top toolbar.

### Update commit fails

**Common errors and fixes:**

| Error | Cause | Solution |
| :--- | :---: | :--- |
| **Dependency conflict** | Package conflicts with existing software | Review dependencies, consider manual resolution via terminal |
| **Download failed** | Network interruption or server issue | Retry the operation; check network connection |
| **Disk space insufficient** | Not enough free storage | Clean up disk space or expand partition |

---

## Related Guides

* [**Pikman CLI Guide**](01-pikman-cli.md) — Command-line package management
* [**Repository Management**](03-repositories.md) — Configure software sources and repositories
* [**Pika Welcome App**](04-pika-welcome.md) — Central configuration interface for new users

---

## Next Steps

After updating your packages:

1. **Review installed updates:** Check what changed in major packages
2. **Restart applications:** Some updates require application restarts
3. **Clean unused dependencies:** Run `pikman autoremove` periodically
4. **Consider Secure Boot:** Enable for enhanced security (optional)

See the [Complete System Basics Collection](../03-system-basics/) for everything you need to manage your PikaOS system.