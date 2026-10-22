# NVIDIA GTK GSK renderer crash fix

## Problem

GTK Apps don't open when using NVIDIA GPU/ISO.

## Cause

Some versions of the proprietary NVIDIA driver are incompatible with the GSK Vulkan Renderer GTK 4.16+ uses, causing any gtk applications to crash.

## Solution

Upgrade your NVIDIA Driver or switch back to OpenGL GSK Renderer:

Drop to a tty or open terminal and do:

```bash
mkdir -p ~/.config/environment.d/
touch ~/.config/environment.d/gsk.conf
echo -e "GSK_RENDERER=opengl" | tee -a ~/.config/environment.d/gsk.conf
```
