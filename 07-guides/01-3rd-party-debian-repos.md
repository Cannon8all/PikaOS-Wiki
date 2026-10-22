# 3rd-party Debian Repositories Setup Guide

## Problem

I Added a debian repo for a 3rd party program but it doesn't work.

## Cause

Many 3rd party applications provide scripts to add their repos

such as

```bash
curl -1sLf \
'https://dl.cloudsmith.io/public/coolercontrol/coolercontrol/setup.deb.sh' \
| sudo -E bash
```

these scripts attempt automatically find the distro codename, expecting something like `sid` or `trixie`, but on pika they will receive `pika` which invalid unless the 3rd party repo has a pika branch. (Which is very unlikely)

## Solution

Manually Supply a distro codename to the 3rd party script, which is valid like `trixie` or preferably `sid`.

## Examples

### Coolercontrol

Run their install script with the following options (distro and codename manually inputted), then just follow their normal debian guide.

```bash
curl -1sLf \
'https://dl.cloudsmith.io/public/coolercontrol/coolercontrol/setup.deb.sh' \
| sudo -E distro=debian codename=trixie bash
```
