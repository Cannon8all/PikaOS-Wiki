# Auto mount disks with GNOME disk utility

## Problem

Additional disks do not stay mounted after clicking them in a GUI file manager.

## Cause

This is due to the disks not being properly mounted in `fstab`. You can manually edit the fstab if you have the competence to do so, or you may make use of the GUI utility `GNOME disk utility` called simply `disks` in the application launcher.

## Solution

Install `GNOME disk utility` (called `disks`) from the Software, Cosmic Store, or Discover. Or install via the terminal with:

```bash
pikman install gnome-disk-utility
```

Launch `disks`

_Note_ Your actual device name, serial number, and UUID will be different

![gnomedisks1.webp](/gnomedisks1.webp)

Select the volume you wish to mount by highlighting the box associated with the drive as shown above.

Click the second box from the left under the volume which will be labeled `additional partition options` .

![gnomedisks2.webp](/gnomedisks2.webp)

Select `Edit Mount Options`

![gnomedisks3.webp](/gnomedisks3.webp)

Deselect `User Session Defaults` as shown in the image above.

Select `Mount at system startup`.

Enter a display name for the drive that you would like to see in the file manager and Steam.

Select `OK` to complete the screen.

_**Note If Steam was open during this edit, you will have to close it and reopen it in order for the drive name to appear in your list of available drives.**_
