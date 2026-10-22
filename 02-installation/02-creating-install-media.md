# Creating install media

## Getting Started

This guide begins after you have downloaded one of the ISO files from the [main page](/home).

Before continuing, make sure Secure Boot and CSM are both disabled in your UEFI settings.

## How to Verify ISO Integrity Using MD5

### Step 1: Copy the Download Link

- Go to the official PikaOS download page.
- Right-click the download button.
- Select **Copy link address**.

![copydllink.png](/copydllink.png)

### Step 2: Retrieve the MD5 Checksum

- Open a new tab in your web browser.
- Paste the copied link into the address bar.
- Change the file extension at the end of the URL from `.iso` to `.md5`
- Press **Enter** to view the checksum text.

![changeisotomd5edit.png](/changeisotomd5edit.png)

### Step 3: Generate the MD5 Hash Locally

- Open your terminal application.
- Navigate to your download folder:

```bash
cd ~/Downloads
```

- Run the MD5 command followed by your exact ISO filename:

```bash
md5sum filename.iso
```

![checkmd5.png](/checkmd5.png)

### Step 4: Compare the Checksums

- Compare the string of characters from your terminal with the text obtained in **Step 2**.
- If the two strings match exactly, your download is successful and uncorrupted.
- If they do not match, delete the file and download the ISO again.

![comparemd5.png](/comparemd5.png)

⚠️ **Warning:** Never install an ISO where the checksums do not match. This indicates a corrupted download or a compromised file.

## Preparing Your Installation Media

To install PikaOS, you will need to write the ISO to a USB drive. Choose the method that matches your device or operating system.

### Linux Methods

1. [Popsicle](https://github.com/pop-os/popsicle)
2. [Fedora Media Writer](https://docs.fedoraproject.org/en-US/fedora/latest/preparing-boot-media/)
3. [dd via terminal](https://linuxconfig.org/Dd)
4. [GNOME Disk Utility](https://gitlab.gnome.org/GNOME/gnome-disk-utility) listed as Disks in most application menus

### Windows Method

1. [Rufus](https://rufus.ie/)

### Cross Platform Tools

1. [Ventoy](https://github.com/ventoy/Ventoy)

   Works correctly as long as the VENTOY partition and PikaOS ISO names are not changed.

2. [BalenaEtcher](https://etcher.balena.io)

   Recommended for macOS users and also available on Windows and Linux.

### Android Method

1. [EtchDroid](https://etchdroid.app)

After writing the ISO to your USB drive, reboot your system and select the USB device from your boot menu.
