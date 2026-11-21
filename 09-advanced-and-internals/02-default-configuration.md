# Default Configuration

---

## Table of Contents

- [Configuration Changes](#configuration-changes)
- [Related Guides](#related-guides)

---

## Configuration Changes

- `fish` configured to source `/etc/profile`
- All desktop environments configured with mouse acceleration off by default.
- All desktop environments configured with Papirus icon theme and a yellow color scheme.
- mutter VRR and fractional scaling support enabled by default.
- mutter check-alive-timeout increased.
- i915 module with `options i915 enable_guc=3`
- amdgpu module with ci and si support

```text
options amdgpu si_support=1
options amdgpu cik_support=1
options radeon si_support=0
options radeon cik_support=0
blacklist radeon
```

---

- nvidia module with

```text
options nvidia-drm modeset=1 fbdev=1
options nvidia NVreg_UsePageAttributeTable=1
options nvidia NVreg_RegistryDwords="OverrideMaxPerf=0x1"
options nvidia NVreg_PreserveVideoMemoryAllocations=1
options nvidia NVreg_RegistryDwords=EnableBrightnessControl=1
options nvidia NVreg_EnableS0ixPowerManagement=1
options nvidia NVreg_EnableGpuFirmware=0
```

---

## Related Guides

* [**Wiki Home**](../README.md) — Complete PikaOS documentation hub