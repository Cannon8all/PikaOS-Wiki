# Snapper btrfs with automatic boot entries

Here we will explain how to set up snapper and Pika to automatically take btrfs snapshots on apt package install and removals and for those snapshots to be bootable in refind.

A couple of points of note:

1. Your boot partition MUST be labelled as "PikaOS" - check this in gparted or blivet
2. You cannot be using LUKS
3. You cannot be using UKIs with secure boot

## How to get started

```bash
pikman update
pikman install snapper snapper-gui
sudo snapper create-config /
sudo mkdir -p /var/lib/refind-btrfs
sudo chmod 755 /var/lib/refind-btrfs
pikman install pika-refind-btrfs-hooks refind-btrfs
sudo systemctl enable refind-btrfs --now
```

## Now what

It should just be working. When you reboot you should see two new sets of entries (per kernel installed), one the base for the kernel and the other listing the snapshots.

Press tab on the snapshots to switch between them.

To declutter it is likely you will need to reduce the number of kernels you have installed.
