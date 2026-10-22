# Chrooting from a Live ISO in PikaOS

Choose the guide that matches your setup. If you're not sure whether your installation is encrypted, run `sudo lsblk -f` in a live ISO terminal — if your root partition shows a filesystem type of `crypto_LUKS`, follow the **LUKS-Encrypted** guide. Otherwise, follow the **Standard (Non-Encrypted)** guide.

## Standard (Non-Encrypted) Installations

### Step 1: Identify Your Partitions

**Open a terminal in your live ISO environment. Run the following command to list all available drives and partitions:**

```bash
sudo lsblk -f
```

**Identify and write down your specific partition names:**

- Root partition (/): Typically a large Btrfs or EXT4 partition.
- Boot partition (/boot): The partition holding the Linux kernel.
- EFI partition: A small FAT32 formatted partition.

### Step 2: Mount the Installed System

**Replace the example partition names (nvme0n1pX) with the actual partitions found in Step 1.**

#### Option A: For Btrfs Filesystems

```bash
sudo mkdir -p /mnt
sudo mount -o subvol=@ /dev/nvme0n1p3 /mnt
```

#### Option B: For Non-Btrfs Filesystems (XFS, EXT4)

**If you did not use Btrfs during installation, remove the subvolume flag:**

```bash
sudo mkdir -p /mnt
sudo mount /dev/nvme0n1p3 /mnt
```

### Mount the Boot and EFI Partitions

```bash
sudo mount /dev/nvme0n1p2 /mnt/boot
sudo mount /dev/nvme0n1p1 /mnt/boot/efi
```

### Step 3: Mount Virtual Filesystems and Configure DNS

**Bind the host system runtime directories to the target mount point:**

```bash
sudo mount --types proc /proc /mnt/proc
sudo mount --rbind /sys /mnt/sys
sudo mount --rbind /dev /mnt/dev
sudo mount --rbind /run /mnt/run
```

**Set the propagation state to slave to prevent host environment lockups:**

```bash
sudo mount --make-rslave /mnt/sys
sudo mount --make-rslave /mnt/dev
sudo mount --make-rslave /mnt/run
```

**Copy DNS resolution settings so the chroot has network access (needed for `apt update`, downloading packages, etc). The `-L` flag dereferences `/etc/resolv.conf` in case it's a symlink (common with systemd-resolved):**

```bash
sudo cp -L /etc/resolv.conf /mnt/etc/resolv.conf
```

### Step 4: Enter the Chroot Environment

**Execute the chroot command to log into your installed system as the root user:**

```bash
sudo chroot /mnt
```

> You can now run commands, fix updates, or repair the bootloader directly on your installed operating system.

### Step 5: Safe Exit and Cleanup

**Once repairs are complete, exit the chroot environment and cleanly unmount the partitions before rebooting:**

```bash
exit
sudo umount -R /mnt
sudo reboot
```

## CHROOT for LUKS-Encrypted Installations

### Step 1: Identify Your Partitions

**Open a terminal in your live ISO environment. Run the following command to list all available drives and partitions:**

```bash
sudo lsblk -f
```

**Identify and write down your specific partition names:**

- Root partition (/): Shows a filesystem type of `crypto_LUKS`.
- Boot partition (/boot): The partition holding the Linux kernel.
- EFI partition: A small FAT32 formatted partition.

### Step 2: Unlock the LUKS Container

**Unlock the LUKS container, replacing the example partition name (nvme0n1pX) with your actual root partition found in Step 1. You will be prompted for your disk password:**

```bash
sudo cryptsetup luksOpen /dev/nvme0n1p3 pikaos-root
```

**This creates a decrypted mapping at /dev/mapper/pikaos-root. Use this mapper path for all mounting steps below.**

### Step 3: Mount the Installed System

#### Option A: For Btrfs Filesystems

```bash
sudo mkdir -p /mnt
sudo mount -o subvol=@ /dev/mapper/pikaos-root /mnt
```

#### Option B: For Non-Btrfs Filesystems (XFS, EXT4)

**If you did not use Btrfs during installation, remove the subvolume flag:**

```bash
sudo mkdir -p /mnt
sudo mount /dev/mapper/pikaos-root /mnt
```

### Mount the Boot and EFI Partitions

**Replace the example partition names (nvme0n1pX) with your actual boot and EFI partitions found in Step 1 — these are typically not encrypted themselves.**

```bash
sudo mount /dev/nvme0n1p2 /mnt/boot
sudo mount /dev/nvme0n1p1 /mnt/boot/efi
```

### Step 4: Mount Virtual Filesystems and Configure DNS

**Bind the host system runtime directories to the target mount point:**

```bash
sudo mount --types proc /proc /mnt/proc
sudo mount --rbind /sys /mnt/sys
sudo mount --rbind /dev /mnt/dev
sudo mount --rbind /run /mnt/run
```

**Set the propagation state to slave to prevent host environment lockups:**

```bash
sudo mount --make-rslave /mnt/sys
sudo mount --make-rslave /mnt/dev
sudo mount --make-rslave /mnt/run
```

**Copy DNS resolution settings so the chroot has network access (needed for `apt update`, downloading packages, etc). The `-L` flag dereferences `/etc/resolv.conf` in case it's a symlink (common with systemd-resolved):**

```bash
sudo cp -L /etc/resolv.conf /mnt/etc/resolv.conf
```

### Step 5: Enter the Chroot Environment

**Execute the chroot command to log into your installed system as the root user:**

```bash
sudo chroot /mnt
```

> You can now run commands, fix updates, or repair the bootloader directly on your installed operating system.

### Step 6: Safe Exit and Cleanup

**Once repairs are complete, exit the chroot environment and cleanly unmount the partitions before rebooting:**

```bash
exit
sudo umount -R /mnt
```

**Close the LUKS container:**

```bash
sudo cryptsetup luksClose pikaos-root
sudo reboot
```
