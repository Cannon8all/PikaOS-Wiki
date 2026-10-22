# Repositories

## Base Repository (Nest)

The Base Repository is a mix of Repositories compiled with x86_64-v3, LTO, and O3, and resulting packages are compiled against each other preventing ABI conflicts that would sometime occur when using these repos as is.

The Repositories include:

- Debian Sid (main, contrib, non-free, non-free-firmware)
- Debian Experimental (Only Certain Packages Such As Desktop Environments)
- DEB Multimedia (Provides up to date multimedia packages with full features, such as ffmpeg with AMF and NVENC, or new gstreamer)

## GFX/Compute Repository (Raven/Pigeon)

- Modified AMDGPU Stack (Allows packages depending on amdgpu to install on a modern Debian Base like PikaOS)
- AMF (1.5 branch, RDNA3 and above) and AMF Legacy (1.4 branch, RDNA2 and below)
- Modified Intel Level Zero Stack (Allows packages depending on base intel-level-zero to install on a modern Debian Base like PikaOS, such as OneAPI)
- Full ROCm Stack with versioning (with dev packages) + HIPRT Package (Compute on AMD GPUs)
- Full OneAPI Stack with versioning (with dev packages) (Compute on Intel GPUs)
- Full CUDA Stack with versioning (with dev packages) (Compute on NVIDIA GPUs)

## 3rd-Party Sync Repository (Parrot)

- Steam sourced from the official Steampowered Repository.
- VS Code sourced from the official Microsoft Repository.
- Discord and Discord-Canary sourced from [Palfrey discord-apt](https://github.com/palfrey/discord-apt).
- xivlauncher sourced from [Maia Everett PPA](https://launchpad.net/~linneris/+archive/ubuntu/xivlauncher-core-stable).
- Brave sourced from the official Brave repository.
- Floorp sourced from the official Floorp repository.
- Mullvad sourced from the official Mullvad repository.
- ProtonVPN sourced from the official Proton repository.
- Many WM Packages sourced from [AvengeMedia OBS](https://download.opensuse.org/repositories/home:/AvengeMedia/Debian_13/).

## Custom Repository (Cockatiel)

- Includes custom packages made by the PikaOS package maintainers on <https://git.pika-os.com/>
- This is also used by PikaOS to provide the latest version of certain packages (obs-studio, blender, lutris, mesa, firmware, sof-firmware, goverlay, mangohud, wine-staging, gamescope, kernel, etc.....)
