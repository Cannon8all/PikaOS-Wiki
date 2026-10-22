# PikaOS FSR 4 Setup Guide

## Setup Steps

1. Close Steam completely
2. Open ProtonPlus and install either:

- Latest Proton-EM
- Proton CachyOS
- Proton GE

3. Set your game to use the Proton version you installed
4. Add the following to your game's Steam launch options:

```bash
fsr4_on %command%
```

5. Launch your game

> Some supported games will show the FSR version as shown in the screenshot from Monster Hunter Wilds below, while others won't display this information.

![fsr4.png](/fsr4.png)

## Compatibility

> The FSR 4 overrides require the game to already support FSR 3.1.

If your game doesn't natively support FSR 3.1, you can use [OptiScaler](https://github.com/optiscaler/OptiScaler):

1. Install OptiScaler into your game directory from: <https://github.com/cdozdil/OptiScaler>
2. Use the same `fsr4_on` launch command as described above
