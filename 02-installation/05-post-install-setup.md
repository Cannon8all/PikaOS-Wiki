# PikaOS Post-Installation Setup Guide

---

## Table of Contents

- [First Boot Experience](#first-boot-experience)
  - [Immediate Actions After Installation](#immediate-actions-after-installation)
- [Desktop Loading & Welcome Wizard](#desktop-loading-welcome-wizard)
  - [First Boot Sequence](#first-boot-sequence)
- [Welcome App Overview](#welcome-app-overview)
  - [What the Welcome App Helps Configure](#what-the-welcome-app-helps-configure)
- [Essential First Steps Checklist](#essential-first-steps-checklist)
  - [Priority 1: System Updates (Critical)](#priority-1-system-updates-critical)
  - [Priority 2: Verify Installation Integrity](#priority-2-verify-installation-integrity)
  - [Priority 3: Configure Repositories](#priority-3-configure-repositories)
  - [Priority 4: Install Recommended Applications](#priority-4-install-recommended-applications)
- [Final Reboot After Setup](#final-reboot-after-setup)
  - [When to Reboot](#when-to-reboot)
  - [How to Reboot Properly](#how-to-reboot-properly)
- [Post-Installation Status Checklist](#post-installation-status-checklist)
  - [Before You Start Using Your System](#before-you-start-using-your-system)
- [What's Next: Exploring PikaOS](#whats-next-exploring-pikaos)
  - [Recommended Learning Path](#recommended-learning-path)
- [Troubleshooting First Boot Issues](#troubleshooting-first-boot-issues)
  - [Issue: Welcome app doesn't appear automatically](#issue-welcome-app-doesnt-appear-automatically)
  - [Issue: System updates fail or hang](#issue-system-updates-fail-or-hang)
  - [Issue: Graphics display issues after reboot](#issue-graphics-display-issues-after-reboot)
- [Related Guides](#related-guides)
- [Quick Reference: First Day Tasks](#quick-reference-first-day-tasks)
  - [Immediate (Within 1 Hour of Installation)](#immediate-within-1-hour-of-installation)
  - [Within First Week](#within-first-week)
  - [Ongoing Maintenance](#ongoing-maintenance)
- [System Health Monitoring](#system-health-monitoring)
  - [Recommended Tools to Install](#recommended-tools-to-install)
- [Security Considerations](#security-considerations)
  - [Immediate Post-Installation Security Steps](#immediate-post-installation-security-steps)
- [Congratulations!](#congratulations)

---

**Essential first steps after installing PikaOS.** This guide covers the initial boot experience, Welcome app configuration, system updates, and recommended setup procedures for a smooth start with your new system.

---

## First Boot Experience

### Immediate Actions After Installation

When installation completes and system prompts reboot:

1. **Remove USB drive** when prompted (or before reboot)
2. System begins automatic restart sequence
3. Wait for PikaOS bird logo to appear on screen
4. **Press `Enter`** at the bird logo to start your new system

> 💡 **Tip:** If you don't press Enter, system may attempt to boot from existing OS (if dual-booting) or show the rEFInd bootloader menu instead of starting PikaOS directly.

---

## Desktop Loading & Welcome Wizard

### First Boot Sequence

**Expected flow after pressing Enter:**
1. System loads PikaOS desktop environment
2. **First boot wizard appears automatically** — titled "Pika Hub" or "Welcome to PikaOS"
3. Click **"Let's Start"** button to begin setup steps
4. Follow guided configuration process
5. System may prompt for final reboot when complete

> 💡 **Tip:** Take your time through the wizard — it guides you through essential configuration steps tailored to your system and preferences.

---

## Welcome App Overview

The Welcome app (Pika Hub) is PikaOS's central configuration interface, designed to help new users get started quickly while providing advanced options for experienced users.

### What the Welcome App Helps Configure

| Feature | Description | Priority |
| :--- | :--- | :---: |
| **System Updates** | Check and install latest updates | Critical |
| **Repository Selection** | Choose software sources | Recommended |
| **Recommended Apps** | Install popular applications | Optional |
| **Desktop Customization** | Personalize appearance and behavior | Optional |
| **System Tools** | Access to PikaOS utilities | Optional |

> 💡 **Tip:** The Welcome app opens automatically after installation. If it doesn't appear, you can launch it from the application menu or by running `pika-welcome` in terminal.

---

## Essential First Steps Checklist

### Priority 1: System Updates (Critical)

**Run system updates immediately after first boot:**

```bash
# Update package lists and upgrade installed packages
pikman upgrade
```

**What this does:**
- Installs latest security patches
- Updates all installed applications
- Ensures kernel is current version
- Fixes any installation-time issues

> ⚠️ **Warning:** Always update immediately after installation to ensure system stability and security. Outdated packages may have known vulnerabilities.

---

### Priority 2: Verify Installation Integrity

**Check that core components are working properly:**

| Component | Verification Command | Expected Result |
| :--- | :---: | :--- |
| **Desktop Environment** | `echo $XDG_CURRENT_DESKTOP` | GNOME, KDE, HYPRLAND, etc. |
| **Package Manager** | `pikman --version` | Version number displayed |
| **Internet Connection** | `ping -c 3 archlinux.org` | Successful ping responses |
| **Graphics Drivers** | `nvidia-smi` (NVIDIA) or `glxinfo` | Driver info displayed |

> 💡 **Tip:** If any verification fails, check our [Common Troubleshooting Guide](../08-common-faults/01-common-troubleshooting-steps.md) for specific solutions.

---

### Priority 3: Configure Repositories

**Select appropriate software sources via Welcome app or terminal:**

```bash
# View available repository options
pikman repo list

# Enable additional repositories (if needed)
sudo pikman repo enable extra
```

> 💡 **Tip:** Most users should keep default repository settings. Additional repositories are only needed for specific hardware or software requirements.

---

### Priority 4: Install Recommended Applications

**Use the Welcome app to install common applications:**

| Category | Suggested Apps | Purpose |
| :--- | :---: | :--- |
| **Productivity** | LibreOffice, GIMP, Inkscape | Office suite and graphics editing |
| **Media** | VLC, MPV, Audacity | Video/audio playback and editing |
| **Development** | VS Code, Git, Terminal tools | Software development environment |
| **Utilities** | Timeshift, Disk Usage Analyzer | System backup and monitoring |

> 💡 **Tip:** The Welcome app provides curated recommendations based on your desktop environment. Review suggestions before installing to avoid unnecessary bloat.

---

## Final Reboot After Setup

### When to Reboot

The Welcome wizard may instruct you to reboot in these scenarios:

| Scenario | Reason for Reboot |
| :--- | :--- |
| **Kernel updated** | New kernel requires restart to load |
| **Graphics drivers changed** | Proprietary NVIDIA/AMD drivers need reload |
| **System configuration modified** | Core settings changes take effect |
| **Welcome wizard complete** | Final setup steps require fresh session |

### How to Reboot Properly

1. **Save all open work** before rebooting
2. Close all applications (or use Welcome app's "Reboot" button)
3. Click **"Reboot Now"** when prompted by the wizard
4. System shuts down cleanly and restarts

> 💡 **Tip:** After reboot, you should see a fully configured PikaOS desktop ready for regular use.

---

## Post-Installation Status Checklist

### Before You Start Using Your System

Verify these items are complete:

| Task | Status | Notes |
| :--- | :---: | :--- |
| **System updated** | ☐ | `pikman upgrade` completed successfully |
| **Welcome app configured** | ☐ | All recommended setup steps finished |
| **Essential apps installed** | ☐ | Productivity, media, and utility software added |
| **Desktop personalized** | ☐ | Wallpaper, themes, and settings adjusted |
| **Backup configured** | ☐ | Timeshift or similar tool set up (optional) |

> 💡 **Tip:** Don't rush through these steps. A properly configured system from the start saves time and prevents issues later.

---

## What's Next: Exploring PikaOS

### Recommended Learning Path

After completing initial setup, explore these topics in order:

1. **System Basics** (Understanding Core Tools)
   * [**Pikman CLI Guide**](../03-system-basics/01-pikman-cli.md) — Command-line package management
   * [**Pikman GUI**](../03-system-basics/02-pikman-gui.md) — Graphical software manager
   * [**Repository Management**](../03-system-basics/03-repositories.md) — Configure software sources

2. **Hardware & Drivers** (Optimizing Your System)
   * [**NVIDIA Drivers Setup**](../04-hardware-and-drivers/01-nvidia-drivers.md) — Complete NVIDIA GPU configuration
   * [**Intel AMD Drivers**](../04-hardware-and-drivers/02-intel-amd-drivers.md) — Older hardware compatibility

3. **Gaming Setup** (If Applicable)
   * [**Gaming on PikaOS**](../05-gaming/01-gaming-on-pikaos.md) — Complete gaming configuration guide
   * [**Falcond**](../05-gaming/02-falcond.md) — Choose the right Proton version for games

---

## Troubleshooting First Boot Issues

### Issue: Welcome app doesn't appear automatically

**Possible causes and solutions:**

| Cause | Solution |
| :--- | :--- |
| **System didn't complete setup** | Reboot system manually, try again |
| **Desktop environment issue** | Launch from menu or terminal (`pika-welcome`) |
| **Configuration corrupted** | Run `sudo pikman reinstall pika-welcome` |

> 💡 **Tip:** You can always access the Welcome app later through the application menu under "System" or by running `pika-welcome` in terminal.

---

### Issue: System updates fail or hang

**Common causes and fixes:**

1. **Network connectivity issue** — Check internet connection
2. **Repository mirror slow** — Switch to different mirror via Welcome app
3. **Package conflict** — Run `pikman upgrade --skip-conflicts` (advanced)
4. **Disk space insufficient** — Free up space or remove unused packages

> ⚠️ **Warning:** Don't interrupt an update once it starts. Interrupted updates can corrupt system state and require repair.

---

### Issue: Graphics display issues after reboot

**Quick fixes for common problems:**

| Symptom | Solution |
| :--- | :--- |
| **Low resolution** | Install proprietary drivers via Welcome app or `pikman` |
| **Black screen on boot** | Add `nomodeset` to kernel parameters temporarily |
| **Flickering display** | Update graphics drivers, check cable connections |
| **Wrong refresh rate** | Adjust settings in desktop environment display panel |

> 💡 **Tip:** For NVIDIA users, ensure you installed the correct `ISO` (NVIDIA edition vs Standard) for your GPU model.

---

## Related Guides

* [**BIOS Checklist**](../01-getting-started/03-bios-checklist.md) — Configure BIOS settings before installation
* [**Creating Install Media**](../02-installation/02-creating-install-media.md) — Write `ISO` to USB drive, verify integrity
* [**Booting the Installer**](../02-installation/03-booting-the-installer.md) — Boot modes, BIOS settings, troubleshooting boot issues
* [**Guided Installation**](../02-installation/04-guided-install.md) — Automated partitioning with advanced filesystem options
* [**Dual Boot Windows**](../02-installation/06-dual-boot-windows.md) — Safe Windows coexistence configuration and setup
* [**Pikman CLI Guide**](../03-system-basics/01-pikman-cli.md) — Command-line package management
* [**Kernel Manager**](../03-system-basics/05-kernel-manager.md) — Update and manage kernel versions
* [**Secure Boot Setup**](../07-guides/04-secure-boot.md) — Enable Secure Boot for enhanced security (optional)
* [**Common Troubleshooting Steps**](../08-common-faults/01-common-troubleshooting-steps.md) — Comprehensive troubleshooting guide

---

## Quick Reference: First Day Tasks

### Immediate (Within 1 Hour of Installation)
- [ ] System updates completed (`pikman upgrade`)
- [ ] Welcome app configuration finished
- [ ] Essential applications installed
- [ ] Desktop environment customized

### Within First Week
- [ ] Backup solution configured and tested
- [ ] Gaming setup complete (if applicable)
- [ ] Development tools installed (if needed)
- [ ] Advanced features explored via Welcome app

### Ongoing Maintenance
- [ ] Weekly system updates (`pikman upgrade`)
- [ ] Monthly backup verification
- [ ] Quarterly review of installed software
- [ ] Annual kernel update check

> 💡 **Tip:** Establish a regular maintenance routine early. Consistent updates and backups prevent most common issues before they occur.

---

## System Health Monitoring

### Recommended Tools to Install

| Tool | Purpose | Installation Command |
| :--- | :---: | :--- |
| **Timeshift** | System snapshots and recovery | `pikman install timeshift` |
| **Gnome Disk Usage Analyzer** | Storage usage visualization | Included by default in GNOME |
| **htop** | Real-time process monitoring | `pikman install htop` |
| **Neofetch/Fastfetch** | System information display | `pikman install fastfetch` |

> 💡 **Tip:** Timeshift is highly recommended for system protection. Configure automatic snapshots weekly to enable quick recovery from problems.

---

## Security Considerations

### Immediate Post-Installation Security Steps

1. **Enable firewall** (if not already active):
   ```bash
   sudo systemctl enable --now firewalld
   ```

2. **Configure automatic security updates**:
   - Via Welcome app or system settings
   - Set to install critical updates automatically

3. **Review installed applications** — Remove any unnecessary software that could pose security risks

> 💡 **Tip:** For most home users, default security settings are sufficient. Enterprise environments may require additional hardening measures.

---

## Congratulations!

You've successfully completed the initial PikaOS setup. Your system is now ready for regular use with:
- ✅ Latest updates and security patches installed
- ✅ Properly configured desktop environment
- ✅ Essential applications available
- ✅ Foundation for advanced customization laid

**Next steps:** Explore the [Gaming Guide](../05-gaming/01-gaming-on-pikaos.md) if you want to start playing games, or dive into [System Basics](../03-system-basics/) to master PikaOS tools and commands.