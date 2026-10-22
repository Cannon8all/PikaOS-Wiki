# Booster and SCSI LUKS Crash

## Problem

Booster initramfs crashes when attempting to unlock LUKS encrypted drive.

## Cause

Some Sketchy USB Drive's firmware identify themselves as SCSI drives instead of USB flash drives,

this causes booster to crash.

## Solution

Make sure you do not have a usb drive plugged in that is incorrectly reporting as a SCSI drive.
