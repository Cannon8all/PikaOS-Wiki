# AMD FSR4 Switcher - Upscaling for AMD GPUs

> ⚠️ **Note:** FSR 4 support depends on your Proton version and game compatibility. Not all games support FSR 4, and the feature requires a compatible AMD GPU. Check [ProtonDB](https://www.protondb.com) for individual game compatibility.

---

## Table of Contents

- [Setup Steps](#setup-steps)
- [Compatibility](#compatibility)
- [Related Guides](#related-guides)

---

---

## Setup Steps

1. Close Steam completely
2. Open ProtonPlus and install either:

- Latest Proton-EM
- Proton CachyOS
- Proton GE

3. Set your game to use the Proton version you installed
4. Add the following to your game's Steam launch options:

```bash
`fsr4_on` %command%
```

5. Launch your game

> 💡 **Note:** Some supported games will display the FSR version (e.g., in Monster Hunter Wilds), while others won't show this information.

---

## Compatibility

> 💡 **Important:** FSR 4 overrides require the game to already support FSR 3.1.

If your game doesn't natively support FSR 3.1, you can use [OptiScaler](https://github.com/optiscaler/OptiScaler):

1. Install OptiScaler into your game directory from: [OptiScaler](https://github.com/cdozdil/OptiScaler)
2. Use the same `fsr4_on` launch command as described above

---

## Related Guides

* [**Gaming on PikaOS**](01-gaming-on-pikaos.md) — Gaming performance optimization overview