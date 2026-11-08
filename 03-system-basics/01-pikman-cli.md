# Pikman CLI - PikaOS Package Manager

---

## Table of Contents

- [Usage](#usage)
  - [Basic Commands](#basic-commands)
- [Global Options](#global-options)
- [Available Commands](#available-commands)
  - [pikman install](#pikman-install-install-packages)
  - [pikman remove](#pikman-remove-remove-packages)
  - [pikman search](#pikman-search-find-packages)
  - [pikman show](#pikman-show-package-details)
  - [pikman update](#pikman-update-update-database)
  - [pikman upgrade](#pikman-upgrade-upgrade-system)
- [System Updates](#system-updates)
- [Native Application Management](#native-application-management)
- [Container Management](#container-management)
  - [Creating Your First Container Package](#creating-your-first-container-package)
  - [Installing Your First Container Package](#installing-your-first-container-package)
  - [Exporting to Application Launcher](#exporting-to-application-launcher)
  - [Removing from Application Launcher](#removing-from-application-launcher)
- [Related Guides](#related-guides)

---

> 💡 **Overview:** Pikman is the unified command-line interface for managing packages, containers, and system updates in PikaOS. It provides a simple, consistent way to install software from multiple sources including native repositories, `AUR`, `Fedora` packages, and more.

**Quick Start:**

```bash
# Update package database
pikman update

# Search for applications
pikman search firefox

# Install an application
pikman install firefox

# Remove an application
pikman remove firefox

# Upgrade all packages
pikman upgrade
```

---

## Usage

Pikman follows a simple command structure: `pikman <command> [options] [arguments]`

### Basic Commands

| Command | Alias | Description |
| :--- | :---: | :--- |
| `install, i` | `i` | Install one or more packages |
| `remove, r` | `r` | Remove an installed package |
| `search, s` | `s` | Search for a package |
| `show` | — | Show details for a package |
| `unexport` | — | Unexport/Remove a program's desktop entry |
| `update` | — | Update the list of available packages |
| `upgrade` | — | Upgrade the system by installing/upgrading available packages |
| `upgrades` | — | List the available upgrades |
| `help, h` | `h` | Shows a list of commands or help for one command |

---

## Global Options

Use these flags to install packages from different distributions:

| Option | Alias | Description | Default |
| :--- | :---: | :--- | :---: |
| `--aur` | — | Install Arch packages (including from the `AUR`) | false |
| `--fedora, --dnf` | `--dnf` | Install Fedora packages | false |
| `--debian, --apt` | `--apt` | Install Debian packages | false |
| `--ubuntu` | — | Install Ubuntu packages | false |

**Example:**

```bash
# Install from AUR
pikman --aur install youtube-music

# Install from Fedora
pikman --fedora install vim
```

---

## Available Commands

### pikman install — Install Packages

Install one or more native PikaOS packages:

```bash
# Install a single package
pikman install git

# Install multiple packages
pikman install git vim htop
```

### pikman remove — Remove Packages

Remove an installed package:

```bash
pikman remove firefox
```

> ⚠️ **Warning:** Use `pikman purge` for a more thorough removal of an application and its dependencies.

### pikman search — Find Packages

Search for available packages:

```bash
# Search by name
pikman search terminal

# Search with regex pattern
pikman search '^gimp'
```

### pikman show — Package Details

Display detailed information about a package:

```bash
pikman show firefox
```

### pikman update — Update Database

Update the local package database from repositories:

```bash
pikman update
```

> 💡 **Tip:** Always run `pikman update` before `upgrade` to ensure you have the latest package database.

### pikman upgrade — Upgrade System

Upgrade all installed packages to their latest versions:

```bash
pikman upgrade
```

---

## System Updates

For system-wide updates, use:

```bash
# Update and upgrade in one command
pikman update && pikman upgrade
```

> 💡 **Best Practice:** Schedule regular updates to keep your system secure and up-to-date with the latest packages.

---

## Native Application Management

Pikman can be used to search for, install, and remove native applications found in its optimized repository.

**Searching:**

To search for an application in the repository use the `search` command:

```bash
pikman search fish
```

**Installing:**

Once you have found the name of the application as it is listed in the repository, install it with the `install` command:

```bash
pikman install fish
```

> ✅ **Note:** Applications installed by Pikman in the CLI will automatically appear in your application launcher with no additional steps required.

**Removing:**

To remove a package, use the `remove` command:

```bash
pikman remove fish
```

---

## Container Management

Pikman allows you to install packages from other distributions using Global Options flags through an implementation of `APX`. This creates isolated containers for cross-distribution compatibility.

### Creating Your First Container Package

Initialize the container you wish to install a package from:

```bash
pikman --aur init
```

Pikman will initialize a new container by downloading the appropriate files and setting them within the `APX` application.

> 💡 **Tip:** Replace `--aur` with your preferred distribution flag (`--fedora`, `--debian`, etc.).

### Installing Your First Container Package

Ensure you use the exact package name that your container's distribution uses:

```bash
pikman --aur install youtube-music
```

> ⚠️ **Warning:** If the installation fails, verify the exact package name in your target distribution. An incorrect name will cause the installation to fail.

### Exporting to Application Launcher

Make container packages visible in your GUI application launcher:

```bash
pikman --aur export youtube-music
```

### Removing from Application Launcher

Remove a package from the launcher without uninstalling it:

```bash
pikman --aur unexport youtube-music
```

> ℹ️ **Info:** Unexporting only removes the launcher entry, not the installed application. Use `remove` to uninstall from your system.

---

## Related Guides

* [**Pikman GUI**](02-pikman-gui.md) — Graphical software manager for package management
* [**Repository Management**](03-repositories.md) — Configure software sources and repositories
* [**Pika Welcome App**](04-pika-welcome.md) — Central configuration interface for new users