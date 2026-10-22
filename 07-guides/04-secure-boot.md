# Secure boot guide

## Problem

The PikaOS Live medium, and the actual PikaOS Installation fail to boot due to various errors such as:

`invalid key`

`invalid magic number`

`secure boot violation`

etc...

## Cause

PikaOS is unable to pay Microsoft for a secure boot signing key.

## Solutions

### Disable Secure boot from UEFI

This is the easy way!

it simply disables the check for a Microsoft signing key, and allows you to boot the medium and installation.

The process varies from hardware manufacturer to another, so search online for yours.

But usually goes like [this](https://www.youtube.com/shorts/UHu4NcUzEY0)

### Sign kernel and bootloader with custom Secureboot key

This method allows secure boot to be enabled

which is useful for security or for programs that require it in a Windows dualboot (Valorant)

> This can only be done post installation, you must initially install the OS with secure boot disabled
> and boot into it to complete this guide.

Follow these instructions, replacing the kernel number (Using 6.14.6-pikaos as an example here) with the currently running one:

```bash
pikman install sbctl-booster-extra
sudo sbctl setup --setup
sudo sbctl create-keys
sudo sbctl enroll-keys --microsoft
sudo apt reinstall linux-image-6.14.6-pikaos
```

Now if refind is installed in `root`/`standard` mode

```bash
sudo sbctl sign /boot/efi/EFI/refind/refind_x64.efi
sudo sbctl sign /boot/efi/EFI/refind/drivers_x64/ext4_x64.efi
```

But if refind is installed in `usedefault`/`bootx64` mode

```bash
sudo sbctl sign /boot/efi/EFI/BOOT/refind_x64.efi
sudo sbctl sign /boot/efi/EFI/BOOT/drivers_x64/ext4_x64.efi
```

And Lastly:

```bash
sudo sbctl verify
```

- Reboot to bios and turn on secure boot

- Reboot and select the vmlinuz-6.14.6-pikaos-uki.efi option in refind rather than regular option
