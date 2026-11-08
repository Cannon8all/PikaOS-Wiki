# NVIDIA DLSS Switcher

---

## Table of Contents

- [Requirements](#requirements)
- [How It Works](#how-it-works)
- [Verification](#verification)
  - [3x and 4x Multi Frame Generation](#3x-and-4x-multi-frame-generation)
- [Related Guides](#related-guides)

---

PikaOS includes a helper wrapper script that simplifies NGX and DSR override settings for Proton's NVAPI. The code can be found [here](https://git.pika-os.com/gfx-packages/nvidia-dlss-switcher).

---

## Requirements

You need to be running a version of proton running [this commit](https://github.com/jp7677/dxvk-nvapi/commit/c13ab338cd8d2e890fd69e695f5f830e345e2f37) of dxvk-nvapi or newer.

The easiest way to ensure this is to use Proton Bleeding Edge directly from the beta branch of Proton Experimental in Steam.

---

## How It Works

In Steam launch options to override and update DLSS to DLSS 4 transformer model, latest ray reconstruction and the latest frame gen models prefix your game with `nv_dlss_full`.

```bash
nv_dlss_full %command%
```

If you are having trouble with the game not starting then it may not support the NGX updater, if that is the case prefix it with `nv_dlss_override` instead and manually copy the latest DLSS dlls from techpowerup into your game's bin directory.

```bash
nv_dlss_override %command%
```

---

## Verification

You can verify it's working by checking the NVIDIA overlay. Look for "override" and preset **K** in the bottom corner. You can turn this on using `nv_hud_on` and then off using `nv_hud_off` (this is a per game/prefix toggle).

```bash
nv_dlss_full nv_hud_on %command%
```

It will then look something like this (check the bottom corner):

### 3x and 4x Multi Frame Generation:

In Steam launch options to override and update DLSS to DLSS 4 transformer model, latest ray reconstruction and the latest frame gen models alongside 4x MFG prefix your game with `nv_dlss_full_4x`.

```bash
nv_dlss_full_4x %command%
```

If you are having trouble with the game not starting then it may not support the NGX updater, if that is the case prefix it with `nv_dlss_override_4x` instead and manually copy the latest DLSS dlls from techpowerup into your game's bin directory.

```bash
nv_dlss_override_4x %command%
```

You can use the same commands but 3x for 3x MFG.

---

## Related Guides

* [**Gaming on PikaOS**](01-gaming-on-pikaos.md) — Gaming performance optimization overview