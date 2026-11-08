# falcond - Advanced Linux Gaming Performance Daemon

---

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Configuration](#configuration)
  - [Configuration Options](#configuration-options)
- [Profile Modes](#profile-modes)
- [Game Profiles](#game-profiles)
  - [Example Profile](#example-profile)
  - [Available Options](#available-options)
  - [User Profiles](#user-profiles)
- [Service Management](#service-management)
- [Monitoring](#monitoring)
- [Source Code](#source-code)
- [Important Notes](#important-notes)
  - [Why falcond?](#why-falcond)
- [Related Guides](#related-guides)

---

falcond is a powerful system daemon designed to automatically optimize your Linux gaming experience. It intelligently manages system resources and performance settings on a per-game basis, eliminating the need for manual configuration for each game.

---

## Features

- **Automatic Game Detection:** Detects running games and applies optimized settings
- **Per-Game Profiles:** Customizable profiles for different games
- **Performance Mode:** Enables system-wide optimizations when gaming
- **3D VCache Management:** Smart management of AMD 3D VCache settings
- **SCX Scheduler Integration:** Dynamically picks the best scheduler for each game
- **Proton Compatibility:** Full support for Steam Proton games with global profile coverage
- **Low Overhead:** Minimal system resource usage
- **Device Modes:** Profiles for desktops, handhelds, HTPCs, and more

---

## Installation

falcond is available on PikaOS via the falcond package or through the pika-gameutils-meta metapackage. It's also packaged by Nobora and CachyOS. For other distributions, check your package manager or build from source.

```bash
pikman install falcond
```

---

## Configuration

The configuration file is located at `/etc/falcond/config.conf`. It will be generated automatically on first run:

```ini
enable_performance_mode = true
scx_sched = none
scx_sched_props = default
vcache_mode = none
profile_mode = none
```

This is global configuration. All options other than `profile_mode` override individual game profiles.

There is also a list of proton/wine system processes in `/usr/share/falcond/system.conf`. This list can be updated if, for example, a crash handler intercepts your profile and needs to be ignored.

### Configuration Options

| Option | Description | Default |
| :--- | --- | :---: |
| `enable_performance_mode` | Enable/disable performance mode | `true` |
| `scx_sched` | SCX scheduler (none, bpfland, lavd, rusty, flash) | `none` |
| `scx_sched_props` | SCX scheduler mode (default, gaming, power, latency, server) | `default` |
| `vcache_mode` | VCache management mode (none, cache, freq) | `none` |
| `profile_mode` | Device type (none=desktop, handheld, htpc) | `none` |

---

## Profile Modes

falcond supports different profile modes for different device types:

- **Default (none):** Uses profiles from `/usr/share/falcond/profiles`
- **Handheld:** Uses profiles from `/usr/share/falcond/profiles/handheld`
- **HTPC:** Uses profiles from `/usr/share/falcond/profiles/htpc`

To set a profile mode, add this to your config file:

```ini
profile_mode = "handheld"  # or "htpc" or "none"
```

---

## Game Profiles

Game profiles are stored in `/usr/share/falcond/profiles/` and define specific optimizations for individual games. You can contribute new profiles via PR:

[Falcond Profiles Repository](https://github.com/PikaOS-Linux/falcond-profiles)

### Example Profile

```ini
name = "game.exe"
performance_mode = true
scx_sched = bpfland
scx_sched_props = gaming
vcache_mode = cache
start_script = "/home/user/start.sh"
stop_script = "notify-send 'game stopped'"
idle_inhibit = false
```

### Available Options

| Option | Description |
| :--- | --- |
| `name` | The executable name (e.g., `cs2`, `PathOfExileSteam.exe`) |
| `performance_mode` | Enable/disable performance mode (default: `true`) |
| `scx_sched` | SCX scheduler (none, bpfland, lavd, rusty, flash, central, cosmos, layered, nest, qmap, rlfifo, rustland, userland, p2dq, tickless) |
| `scx_sched_props` | SCX scheduler mode (none, gaming, power, latency, server) |
| `vcache_mode` | VCache management mode (none, cache, freq) |
| `start_script` | Script to run when the game starts |
| `stop_script` | Script to run when the game stops |
| `idle_inhibit` | Prevent screensaver/idle while game is running (default: `false`) |

### User Profiles

falcond supports user-specific profiles that override system profiles. User profiles are stored in `/usr/share/falcond/profiles/user/` and take precedence over system profiles with the same name. This allows you to customize game settings without modifying system files.

**To create a user profile:**

1. Create the directory if it doesn't exist:
   ```bash
   sudo mkdir -p /usr/share/falcond/profiles/user/
   ```
2. Create a profile file with the game's name:
   ```bash
   sudo nano /usr/share/falcond/profiles/user/game.conf
   ```
3. Add your custom settings

User profiles follow the same format as system profiles but will override any system profile with the same name. If a user profile doesn't exist for a game, the system profile will be used.

---

## Service Management

To restart the daemon:

```bash
sudo systemctl restart falcond
```

To check the status:

```bash
sudo systemctl status falcond
```

---

## Monitoring

Check the detailed status of falcond by reading the status file (also available at `/tmp/falcond-status` for apps like MangoHud):

```bash
cat /var/lib/falcond/status
```

**Example output:**

```text
FEATURES:
  Performance Mode: Available

CONFIG:
  Profile Mode: none
  Global VCache Mode: none
  Global SCX Scheduler: none

AVAILABLE_SCX_SCHEDULERS:
  - scx_bpfland
  - scx_cosmos
  - scx_flash
  - scx_lavd
  - scx_p2dq
  - scx_tickless
  - scx_rustland
  - scx_rusty

LOADED_PROFILES: 7

ACTIVE_PROFILE: cs2

QUEUED_PROFILES:
  (None)

RESTORE_STATE:
  SCX Scheduler: (None)
  Power Profile: power-saver

CURRENT_STATUS:
  Performance Mode: Active
  VCache Mode: cache
  SCX Scheduler: none
  Screensaver Inhibit: Active
```

---

## Source Code

The source code for falcond can be found at:

[Falcond Source Repository](https://git.pika-os.com/general-packages/falcond)

---

## Important Notes

> ⚠️ **Compatibility Warning:** Do not use falcond alongside Feral GameMode or Falcon GameMode. They may conflict with each other. falcond provides similar functionality with additional features and optimizations.

### Why falcond?

Traditional gaming on Linux often requires manual optimization for each game—tweaking CPU governors, scheduling priorities, and cache settings. falcond automates this entire process by:

1. Automatically detecting when games are running
2. Applying optimized settings based on pre-configured profiles
3. Reverting settings when games are closed
4. Providing a centralized way to manage gaming performance
5. Enabling easy switching of options for different device types

This means you can focus on gaming while falcond handles all the technical optimizations in the background!

---

## Related Guides

* [**Gaming on PikaOS**](01-gaming-on-pikaos.md) — Gaming performance optimization overview
* [**Falcon Gamemode**](03-falcon-gamemode.md) — Alternative gaming performance profile