# LACT - Fixing performance/stuttering issues

## Problem

Stuttering and performance drops in-game.

## Cause

GPU not using the correct power profiles.

## Solutions

Open the Terminal run this cmd :

```bash
pikman update && pikman install lact
```

1. Open LACT software or run it via terminal `lact` <https://packages.pika-os.com/packages/lact>
2. Select your dedicated GPU.
3. Go to `OC` tab and under the section `Performance` you will find Performance Level and Power Profile Mode
4. On the drop down menu of Performance Level set it from `Automatic` to `Manual`
5. On the drop down menu of Power Profile Mode set it from `BOOTUP_DEFAULT` to `3D_FULL_SCREEN`
6. Apply/Save and Reboot your System (as a precaution)

![lact_pika_settings_1.png](/screenshots/lact_pika_settings_1.png)

![lact_pika_settings_2.png](/screenshots/lact_pika_settings_2.png)

![lact_pika_settings_3.png](/screenshots/lact_pika_settings_3.png)
