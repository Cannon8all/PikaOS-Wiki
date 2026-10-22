# NVIDIA DLSS Switcher

Here at PikaOS we have written a nice helper wrapper script to ease NGX and DSR override settings for Proton's NVAPI. The code can be found [here](https://git.pika-os.com/gfx-packages/nvidia-dlss-switcher).

## Requirements

You need to be running a version of proton running [this commit](https://github.com/jp7677/dxvk-nvapi/commit/c13ab338cd8d2e890fd69e695f5f830e345e2f37) of dxvk-nvapi or newer.

The easiest way to ensure this is to use Proton Bleeding Edge directly from the beta branch of Proton Experimental in steam.

## How does it work:

In steam launch options to override and update DLSS to DLSS 4 transformer model, latest ray reconstruction and the latest frame gen models prefix your game with nv_dlss_full.

```bash
nv_dlss_full %command%
```

If you are having trouble with the game not starting then it may not support the NGX updater, if that is the case prefix it with nv_dlss_override instead and manually copy the latest DLSS dlls from techpowerup into your game's bin directory.

```bash
nv_dlss_override %command%
```

## How do I know it is working

Luckily you can easily check if it is working using the provided overlay, if it says override and preset K then you are good to go. You can turn this on using nv_hud_on and then off using nv_hud_off (this is a per game/prefix toggle).

```bash
nv_dlss_full nv_hud_on %command%
```

It will then look something like this (check the bottom corner):

![dlssexample.jpg](/dlssexample.jpg)

## How do I do 3x and 4x multi framegen?:

In steam launch options to override and update DLSS to DLSS 4 transformer model, latest ray reconstruction and the latest frame gen models alongside 4x mfg prefix your game with nv_dlss_full_4x.

```bash
nv_dlss_full_4x %command%
```

If you are having trouble with the game not starting then it may not support the NGX updater, if that is the case prefix it with nv_dlss_override_4x instead and manually copy the latest DLSS dlls from techpowerup into your game's bin directory.

```bash
nv_dlss_override_4x %command%
```

You can use the same commands but 3x for 3x MFG.
