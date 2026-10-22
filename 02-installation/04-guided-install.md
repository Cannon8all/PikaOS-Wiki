# Guided install

This guide walks you through partitioning your PikaOS installation through the automatic partitioning process, including the advanced options.

## Selecting Automatic Partitioning

During installation you will be provided the option for an automatic or manual installation. For this guide we will be selecting the top listed option "Automatically Partition The Drive" as seen below:

![partitioning1.png](/partitioning-images/partitioning1.png)

### Selecting The Installation Disk

You will be required to select a disk to install the system into. Select the yellow box currently labeled (No Disk Selected for Installation)

![partitioning2.png](/partitioning-images/partitioning2.png)

A window will appear allowing you to select a disk to install your system.

It should be noted that _**this will erase all the data on the disk and cannot be undone**_.

> _**Before installing, it is your responsibility to back up all data.**_

![partitioning3.png](/partitioning-images/partitioning3.png)

## Advanced Options

### Selecting The Filesystem, Home Directory Separation, and Swap Size

By selecting the "Advanced Options" button, a new window will open:

![partitioning5.png](/partitioning-images/partitioning5.png)

### Selecting The Filesystem

PikaOS offers three filesystems for use:

- BTRFS _Default Selection_
- EXT4
- XFS

Select your preferred filesystem by selecting the circle to the left of your choice.

### Selecting The Directory Separation

PikaOS offers three options for Home Directory Separation Options

- No

> (no separate Home Directory)

- Yes, via a Subvolume _Default Selection_

> (a subvolume on the disk will be created for the Home Directory)

- Yes, via a Partition

> (a separate partition will be created for the Home Directory)

Select your preferred Home directory structure by selecting the circle to the left of your choice.

### Selecting The Swap Size

PikaOS offers three options for the swap size

- None/Zram _Default Selection_

> (no swap file will be created. Swap will be handled by Zram)

- 1/2 of System Ram

> (a swap file will be created equal to half of the installed system Ram)

- Equal to System Ram

> (a swap file will be created equal to all of the installed system Ram)

- Custom Swap Size

> (the user will manually select the swap file size in full gigabyte increments)

Select your preferred Swap size by selecting the circle to the left of your choice.

### Selecting Boot Options

PikaOS offers several additional boot options for ease of use and compatibility.

Select the "Boot" button to the left of "Partitioning" to see these options:

![partitioning7.png](/partitioning-images/partitioning7.png)

### ReFind Boot Options

PikaOS provides options during installation to manage how its default bootloader, [ReFind](https://www.rodsbooks.com/refind/) , is displayed during boot.

- Skip Selection and Boot up Automatically

> (ReFind will not display during boot and the user will be automatically booted into the last loaded system unless the user manually pushes the arrow keys to force the display of ReFind)

- Show Selection

> (ReFind will display at each boot per its default configuration)

- Show Selection with Autoboot Timeout

> (ReFind will display at each boot with the timeout in seconds manually selected by the user)

Select your preferred ReFind boot option by selecting the circle to the left of your choice.

> ### A Note For MSI Motherboards

_**If you are installing PikaOS to a MSI Motherboard or Laptop system, please select the "BOOTX64 Mode (MSI Compatibility Mode)" found in Advanced Options / Boot**_

![partitioning7.png](/partitioning-images/partitioning7.png)

## Confirming Changes And Installing The System

After selecting your disk for installation continue by pressing the yellow arrow to the right of the installer and you will be greeted with a summary of the changes.

Ensure that everything listed is accurate and then select the red (Confirm & Install PikaOS) button.

![partitioning8.png](/partitioning-images/partitioning8.png)

> Continue to the next section of the installation wiki
