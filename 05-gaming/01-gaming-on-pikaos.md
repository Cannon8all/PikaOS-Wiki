# Gaming on PikaOS

PikaOS ships with the latest graphics drivers out of the box. Your GPU is ready for gaming from the first boot.

---

## Table of Contents

- [Quick Start](#quick-start)
- [Which Proton Version Should I Use?](#which-proton-version-should-i-use)
  - [Official Proton Versions (Valve)](#official-proton-versions-valve)
  - [Community Proton Builds](#community-proton-builds)
    - [Proton-GE (GloriousEggroll)](#proton-ge-gloriouseggroll)
    - [Proton-CachyOS](#proton-cachyos)
    - [Proton-EM (Etaash-mathamsetty)](#proton-em-etaash-mathamsetty)
  - [Which One Should I Pick?](#which-one-should-i-pick)
- [Proton Launch Commands](#proton-launch-commands)
  - [How to Use Launch Commands](#how-to-use-launch-commands)
  - [What Is `%command%`?](#what-is-command)
  - [Command Structure](#command-structure)
  - [General Commands (Any GPU)](#general-commands-any-gpu)
  - [NVIDIA Commands](#nvidia-commands)
  - [DLSS and Frame Generation (NVIDIA)](#dlss-and-frame-generation-nvidia)
    - [What Your GPU Supports](#what-your-gpu-supports)
    - [Step 1: Add the Launch Command](#step-1-add-the-launch-command)
    - [Step 2: Enable In-Game](#step-2-enable-in-game)
    - [If the Game Won't Start](#if-the-game-wont-start)
  - [NVIDIA Hybrid Laptops](#nvidia-hybrid-laptops)
  - [AMD Commands](#amd-commands)
  - [AMD Hybrid Laptops](#amd-hybrid-laptops)
- [Gamescope](#gamescope)
  - [Common Options](#common-options)
  - [Examples](#examples)
    - [Example: 1080p Upscaling](#example-1080p-upscaling)
    - [Example: Integer Scaling with VRR](#example-integer-scaling-with-vrr)
    - [Example: Borderless Window Mode](#example-borderless-window-mode)
    - [Example: Framerate Capping](#example-framerate-capping)
- [Steam Shader Pre-caching](#steam-shader-pre-caching)
  - [Increasing the Shader Cache Size](#increasing-the-shader-cache-size)
    - [Configure Shader Cache Size](#configure-shader-cache-size)
- [falcond Performance Daemon](#falcond)
  - [Features](#features)
- [Troubleshooting Proton](#troubleshooting-proton)
  - [Capturing and Sharing Proton Logs](#capturing-and-sharing-proton-logs)
- [Related Guides](#related-guides)

---

## Quick Start

Install all essential gaming tools:

```bash
pikman i pika-gameutils-meta
```

> 💡 **Tip:** You can also install this package via the **PikaOS Welcome** app.

This preinstalls launchers and utilities including Steam, Heroic, Lutris, ProtonPlus, GOverlay, MangoHud, and Gamescope.

---

## Which Proton Version Should I Use?

**Proton** is the compatibility layer that lets Windows games run on Linux. Steam picks a version for each game by default, but some games run better with different versions.

### Official Proton Versions (Valve)

- **Proton 11.0:** The current stable series. Recommended as the default for most games and updated automatically through Steam.
- **Proton Experimental:** Valve's bleeding-edge branch. New fixes land here first. Use it for new games or titles that don't work well on stable Proton.
- **Proton 10.0 and older:** Previous stable series. Only use if a game works with an older version but not with newer ones.

To choose a version for one game in Steam: right-click the game, select **Properties → Compatibility**, tick **Force the use of a specific Steam Play compatibility tool**, then pick from the list.

### Community Proton Builds

Community builds add extra features and fixes that Valve's Proton doesn't have yet. They are made by volunteers and are not supported by Valve.

Install and update community builds with ProtonPlus, which comes with pika-gameutils-meta. It can set them up for Steam, Lutris, and Heroic.

#### Proton-GE (GloriousEggroll)

Made by GloriousEggroll and based on Valve's Proton. Known features:

- Video playback fixes for games with missing or broken cutscenes
- Many game-specific fixes
- Optional OptiScaler support

The most widely used community build.

#### Proton-CachyOS

Made by the CachyOS team and based on Proton Experimental. Adds:

- Quality-of-life features and performance work
- Low-latency versions of DXVK and VKD3D
- FSR4 upscaling for AMD GPUs
- Winewayland improvements
- Different builds for different CPUs (`x86_64_v3` or plain `x86_64`)

Choose x86_64_v3 if your CPU supports it; otherwise use the plain x86_64 build. Available in SLR (Steam Linux Runtime) and native variants.

#### Proton-EM (Etaash-mathamsetty)

Focuses on:

- Native Wayland support (winewayland)
- HDR and FSR4 upscaling
- Latest Wayland development work

Many of Proton-CachyOS's and Proton-GE's Wayland improvements originate here. Choose this if you want the latest Wayland development.

### Which One Should I Pick?

| If You... | Try |
| :--- | :---: |
| Just want your games to work | **Proton 11.0** (or Steam's default) |
| Play a brand new game, or one that doesn't run well | **Proton Experimental**, and check [ProtonDB](https://www.protondb.com) |
| Have a game that only works with an older version | **Proton 10.0** or older |
| See missing videos or cutscenes, or need a game-specific fix | **Proton-GE** |
| Want FSR4 upgrading and low-latency extras | **Proton-CachyOS** |
| Want native Wayland or HDR | **Proton-EM** |

> ⚠️ **Note:** FSR 4 support in Proton-CachyOS is experimental and may change between releases. Verify game compatibility before relying on it.

---

## Proton Launch Commands

Launch commands (also called launch options) let you change how a game starts. You can switch Proton features on or off, show an FPS overlay, run the game inside Gamescope, and more.

### How to Use Launch Commands

In Steam, right-click the game, select **Properties**, and type the command into the **Launch Options** box under the **General** tab.

### What Is `%command%`?

`%command%` stands for the game's normal start command. Steam replaces it with the real command when you press Play. Everything you write around it changes how the game is started:

```bash
VARIABLE=value program %command% -game-argument
```

### Command Structure

| Position | Content | Description |
| :--- | :--- | :--- |
| **Before** `%command%` | `VARIABLE=value` | Environment variables that change behavior (e.g., `PROTON_LOG=1`) |
| **Before** `%command%` | `program` | Tools that wrap the game (e.g., `mangohud`, `gamescope`) |
| **After** `%command%` | `-game-argument` | Arguments passed directly to the game (e.g., `-novid`) |

You can combine as many as you like, separated by spaces:

```bash
PROTON_LOG=1 mangohud %command% -novid
```

> ⚠️ If a game won't start after you change its launch options, clear the box and try one option at a time. A typo is the most common cause.

### General Commands (Any GPU)

| Command | Description |
| :--- | --- |
| `PROTON_LOG=1 %command%` | Writes a Proton log to your home folder (see [Troubleshooting Proton](#troubleshooting-proton)). |
| `mangohud %command%` | Shows an overlay with FPS, temperatures and usage (requires MangoHud). |
| `PROTON_ENABLE_WAYLAND=1 %command%` | Runs the game with the Wayland driver instead of XWayland. Experimental; only available in custom Proton builds such as Proton-CachyOS and Proton-GE. |
| `PROTON_USE_WINED3D=1 %command%` | Uses OpenGL-based WineD3D instead of DXVK/VKD3D. Only for older games or GPUs without good Vulkan support. |
| `PROTON_NO_ESYNC=1 %command%` | Turns off esync. Try it if a game crashes or freezes. |
| `PROTON_NO_FSYNC=1 %command%` | Turns off fsync. Try it if a game crashes or freezes. |
| `VKD3D_CONFIG=dxr %command%` | Enables ray tracing in DirectX 12 games, if your GPU supports it. |

### NVIDIA Commands

| Command | Description |
| :--- | --- |
| `PROTON_ENABLE_NVAPI=1 %command%` | Enables NVAPI, which games need for features like DLSS. |
| `PROTON_HIDE_NVIDIA_GPU=0 %command%` | Stops Proton from hiding your NVIDIA GPU from the game. Some games need this to detect the card. |
| `__GL_THREADED_OPTIMIZATIONS=1 %command%` | Moves some of the NVIDIA OpenGL driver's CPU work to a separate thread. Off by default because it can lower performance in some games. Only affects OpenGL games. |
| `__GL_MaxFramesAllowed=1 %command%` | Limits how many frames the NVIDIA driver queues ahead (2 by default), which can lower input latency. |

### DLSS and Frame Generation (NVIDIA)

DLSS is NVIDIA's technology for upscaling and frame generation on RTX GPUs. Games ship with their own copy of DLSS, which is often an older version. PikaOS includes launch commands that update a game to the latest DLSS models and turn on 4x multi frame generation (MFG) for you.

#### What Your GPU Supports

| Feature | Description | GPUs |
| :--- | --- | :---: |
| DLSS 4 super resolution and ray reconstruction | Sharper upscaling and cleaner ray tracing | All RTX GPUs |
| Frame generation | Creates extra frames for higher FPS | RTX 40 and 50 series |
| 3x and 4x multi frame generation | Creates two or three extra frames per rendered frame | RTX 50 series only |

> ⚠️ The game itself must support DLSS. The commands below upgrade what a game already has. They can't add DLSS to a game that has none.

#### Step 1: Add the Launch Command

In the game's Steam launch options, enter:

```bash
nv_dlss_full_4x %command%
```

This does three things:

- Updates DLSS to the DLSS 4 transformer model
- Updates ray reconstruction and frame generation to their latest models
- Enables 4x multi frame generation

#### Step 2: Enable In-Game

Start the game and open its graphics settings. Turn on DLSS, and turn on frame generation if you want it. The command upgrades the models, but the game still decides which features are active.

#### If the Game Won't Start

Some games don't support the NGX updater used by the command above. For those games, use this instead:

```bash
nv_dlss_override_4x %command%
```

It applies the same overrides but doesn't update the DLSS files for you. You have to replace them yourself:

1. Download the latest DLSS file from [TechPowerUp](https://www.techpowerup.com/download/nvidia-dlss-dll/).
2. Find nvngx_dlss.dll in the game's folder (same location as other DLSS files).
3. Replace it with the downloaded file.

### NVIDIA Hybrid Laptops

To run a game on the dedicated NVIDIA GPU instead of the integrated one:

```bash
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia __VK_LAYER_NV_optimus=NVIDIA_only %command%
```

### AMD Commands

| Command | Description |
| :--- | --- |
| `mesa_glthread=true %command%` | Enables threaded OpenGL in Mesa, which can reduce CPU load in OpenGL games. Some games already have it on by default. |
| `PROTON_FSR4_UPGRADE=1 %command%` | Upgrades FSR 3.1 games to FSR4 on supported AMD GPUs. Recent Proton-CachyOS builds do this automatically. |

### AMD Hybrid Laptops

To run a game on the dedicated AMD GPU instead of the integrated one:

```bash
DRI_PRIME=1 %command%
```

---

## Gamescope

Gamescope runs the game inside its own small window or fullscreen session. It's useful for fixing resolution or scaling problems, capping the framerate, and upscaling.

```bash
gamescope -W 2560 -H 1440 -r 144 -f -- %command%
```

The `--` separates Gamescope's options from the game. Everything before it is for Gamescope; `%command%` comes after it.

### Common Options

| Option | Description |
| :--- | --- |
| `-W` / `-H` | Output resolution (your screen) |
| `-w` / `-h` | The game's internal resolution. Set this lower than the output resolution to upscale. |
| `-r` | Limits the game's refresh rate (frames per second) |
| `-o` | Refresh rate limit while not focused, e.g., `-o 30` to save power in the background |
| `-f` | Starts fullscreen |
| `-b` | Starts in a borderless window |
| `-F fsr` | Upscales with FSR 1.0. Other filters: nis, linear, nearest, pixel, sgsr |
| `-S integer` | Scales the game in whole-number steps for sharp pixels. Other modes: `fit`, `fill`, `stretch` |
| `--sharpness 5` | Sets sharpness for FSR and NIS from 0 to 20. Lower values are sharper |
| `--adaptive-sync` | Enables variable refresh rate (VRR) if your display supports it |
| `-e` | Enables Steam integration, so the Steam overlay works inside Gamescope |
| `--force-grab-cursor` | Always uses relative mouse mode instead of switching depending on cursor visibility. Use if the cursor escapes or limits camera movement |
| `--mangoapp` | Shows the MangoHud overlay from inside Gamescope |

> ⚠️ Use `--mangoapp` instead of `mangohud` when running a game inside Gamescope. Using both shows two overlays.

### Examples

#### Example: 1080p Upscaling

```bash
gamescope -w 1920 -h 1080 -W 2560 -H 1440 -r 144 -F fsr -f -- %command%
```

#### Example: Integer Scaling with VRR

```bash
gamescope -W 2560 -H 1440 -S integer -e --adaptive-sync -f -- %command%
```

#### Example: Borderless Window Mode

```bash
gamescope -W 2560 -H 1440 -b --force-grab-cursor --mangoapp -- %command%
```

#### Example: Framerate Capping

```bash
gamescope -W 2560 -H 1440 -r 60 -f -- %command%
```

---

## Steam Shader Pre-caching

Games compile shaders (small programs for your GPU) while you play. The first time you meet a new effect, this can cause stutter or long loading times.

Steam can compile some shaders ahead of time. With Proton-CachyOS, Proton-GE, or Proton-EM, it's better to turn this off. These builds already include the codecs needed for in-game videos, and a reasonably modern CPU and GPU can handle compiling shaders on the fly.

Steam's pre-caching also doesn't cover everything, and updating the Proton version can force all shaders to be compiled again. If you have time to spare, you can leave it on.

To turn it off, open **Steam → Settings → Downloads** and untick:

- Allow background processing of Vulkan shaders
- Enable Shader Pre-caching

> ⚠️ After turning off Steam's shader pre-caching, increase your maximum shader cache size (see below).

### Increasing the Shader Cache Size

Compiled shaders are stored on your system and reused later. By default, the cache has a size limit, and once it's full, the oldest shaders are dropped. Some large games have over 1 GB of shaders, so they can end up recompiling on every launch. Raising the limit avoids repeated stutter and long load times.

#### Configure Shader Cache Size

**Create the config directory if it doesn't exist:**

```bash
mkdir -p ~/.config/environment.d
```

**Create and open the file in nano:**

```bash
nano ~/.config/environment.d/gaming.conf
```

**Paste the correct configuration line below:**

**AMD**:

```bash
MESA_SHADER_CACHE_MAX_SIZE=12G
```

**NVIDIA**:

```bash
__GL_SHADER_DISK_CACHE_SIZE=12000000000
```

Save with `Ctrl + O`, press `Enter`, then exit nano with `Ctrl + X`. Log out and back in for the change to apply.

---

## falcond Performance Daemon

falcond is PikaOS's profile-based gaming performance daemon. It runs quietly in the background, notices when you start a game, and applies the right performance settings for that game. You can make your own profiles and tweak settings by hand for each title.

A selection of popular profiles is already included, like the Proton profile that activates for any game running in a Proton compatibility layer.

**falcond-gui** is the PikaOS app you can use to configure everything.

> ⚠️ Don't use `falcond` together with `feral gamemode`. They will interfere.  
> falcond does not have to be added to game launch options.

### Features

- **Automatic game detection:** Detects running games and applies optimized settings
- **Per-game profiles:** Each game can have its own profile
- **Performance mode:** Turns on system-wide performance optimizations while you play
- **3D V-Cache Management:** On AMD X3D processors with two CCDs, switches the V-Cache mode for each game so games that benefit from extra cache use the V-Cache cores
- **SCX scheduler integration:** Picks the CPU scheduler (scx) that suits the specific game
- **VRAM prioritization (dmem):** Uses the Linux dmem cgroup to manage GPU video memory. The foreground game gets priority, so background programs can't cause stutter
- **Proton support:** Works with Steam Proton games; a global profile covers games without their own profile
- **Device modes:** Profiles for desktops, handhelds, HTPCs, and more
- **Low overhead:** Uses very few system resources

---

## Troubleshooting Proton

### Capturing and Sharing Proton Logs

To turn on Proton logging for a game:

1. In Steam, right-click the game and select **Properties**
2. Under **Launch Options**, enter:

```bash
PROTON_LOG=1 %command%
```

The next time you start the game, Proton writes a log file to your home folder named steam-[AppID].log. For example, Counter-Strike 2 has AppID 730, so its log is steam-730.log.

---

## Related Guides

* [**Proton Versions Guide**](02-falcond.md) — Choose the right compatibility layer
* [**Falcon Gamemode**](03-falcon-gamemode.md) — Alternative gaming performance profile