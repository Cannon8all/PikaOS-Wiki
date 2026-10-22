# Nvidia drivers

## Usage of Basic Profiles

### For Nvidia GPUs

- Choose between:
  - **Nvidia Open** (open-source kernel modules, GTX 16-series and newer)
  - **Nvidia Closed**: _TODO: two-line "why Open" note (wording needed)_
- Users who prefer the fully open-source **Nouveau** driver can uninstall Nvidia profiles and use Mesa profiles instead.

All profiles default to the latest non-experimental drivers.

## Usage of Advanced Profiles

### Select Different Nvidia Driver Versions

![pikaos-device-manager.png](/pikaos-device-manager.png)

PikaOS provides a wide selection of Nvidia drivers from version 550 onward, including Beta and New Branch releases. This is ideal for users who need older versions for compatibility or want to test the newest builds.

**Warning:**

Older drivers may require rolling back to a compatible kernel. Using mismatched versions can cause kernel panics and prevent the system from booting. Experimental drivers are clearly labeled and never set as defaults.
