# Common Troubleshooting Steps

---

## Table of Contents

- [Using `PikaOS Paste` for Logs](#using-pikaos-paste-for-logs)
  - [How to Use PikaOS Paste](#how-to-use-pikaos-paste)
- [Access Terminal via TTY](#access-terminal-via-tty)
- [Troubleshooting Black Screen Boot](#troubleshooting-black-screen-boot)
  - [Option A: Boot Older Kernel](#option-a-boot-older-kernel)
  - [Option B: Boot to Runlevel 3 Terminal](#option-b-boot-to-runlevel-3-terminal)
  - [Option C: Chroot from Live ISO](#option-c-chroot-from-live-iso)
- [Legacy NVIDIA Cards (10 Series and Earlier)](#legacy-nvidia-cards-10-series-and-earlier)
  - [If You Get a Bluescreen](#if-you-get-a-bluescreen)
  - [If You're Stuck at the Greeter](#if-youre-stuck-at-the-greeter)
- [Greeter (Login Manager) Issues](#greeter-login-manager-issues)
- [Keyboard Layout Problems](#keyboard-layout-problems)
- [Keyboard Input Failure at Login Screen](#keyboard-input-failure-at-login-screen)
  - [Step 1: Switch to TTY](#step-1-switch-to-tty)
  - [Step 2: Edit Otter-Greeter Configuration](#step-2-edit-otter-greeter-configuration)
  - [Step 3: Add or Edit Keyboard Layout Line](#step-3-add-or-edit-keyboard-layout-line)
  - [Step 4: Save and Reboot](#step-4-save-and-reboot)
- [AMD GPU KWin Crashes (RX 7000/9000 Series)](#amd-gpu-kwin-crashes-rx-70009000-series)
- [Bluescreen on Boot](#bluescreen-on-boot)
- [Additional Support](#additional-support)
- [Related Documentation](#related-documentation)

---

## Using PikaOS Paste for Logs

When asking for help in the `Discord`, avoid pasting lengthy logs, terminal output, or command results directly into chat. This clutters the channel and makes issues harder to read and track.

**Instead, use _`PikaOS Paste`_**:

[`paste.pika-os.com`](https://paste.pika-os.com/)

### How to Use `PikaOS Paste`

1. **Copy your log output**  
   Copy the full output you want to share (e.g., result of `pikman upgrade`, a log file, or config file).

2. **Paste and configure**  
   Go to [`paste.pika-os.com`](https://paste.pika-os.com/) and paste the content into the box:
   - Optionally select a language/syntax (`log`, `bash`, etc.)
   - Choose an expiry time
   - Add a password if you want it protected

3. **Share the link**  
   Click **Create encrypted paste** and copy the generated link to post in your Discord channel, along with a short description of the problem.

> 💡 **Tip:** This keeps channels readable and makes it easier for helpers to review full logs and diagnose issues faster.

---

## Access Terminal via TTY

**Linux provides virtual terminals (`TTYs`) separate from your graphical login screen.**

### How to Access a TTY

- Press **Ctrl+Alt+F1** (or F1–F6) to switch to a `TTY`
- Most function keys F1–F6 are mapped to a `TTY`; your graphical session usually lives on F7 (or F1, depending on setup)
- Log in with your normal username and password

You can now troubleshoot from the terminal.

---

## Troubleshooting Black Screen Boot

**Use this method when you can't get a graphical session and can't drop into a `TTY`.**

### Option A: Boot Older Kernel

1. At the **`rEFInd` bootloader**, press **Tab**
2. Select an older kernel from the list
3. If the system boots normally, the issue is likely with your newest kernel

### Option B: Boot to Runlevel 3 Terminal

If booting an older kernel doesn't help:

1. At the `rEFInd` bootloader, press **Tab** twice (reveals full boot command line)
2. Move cursor to end of the line
3. Add a `space`, then type `3`
4. Press **Enter**

This boots you into a terminal (runlevel 3) for further troubleshooting.

### Option C: Chroot from Live ISO

If neither option works, you can still reach your installed system by chrooting from a live `ISO`:

[Chrooting from a Live `ISO` in `PikaOS`](../07-guides/06-chrooting-from-a-live-iso.md)

---

## Legacy `NVIDIA` Cards (10 Series and Earlier)

**If you have bluescreen or greeter issues with older `NVIDIA` cards:**

### If You Get a Bluescreen

1. Press **Tab** in the rEFInd bootloader
2. Launch into an older kernel
3. Proceed to terminal commands below

### If You're Stuck at the Greeter

1. Press **Ctrl+Alt+F3** to start a TTY terminal
2. Log in and proceed with commands below:

```
pikman install pika-nvidia-driver kernel-pika-kernel
```

After logging back in, you can remove the faulty or unsupported kernel using the `PikaOS` Kernel Manager if needed.

---

## Greeter (Login Manager) Issues

**If your greeter fails to start or behaves incorrectly:**

Reconfigure it from a `TTY`:

```
sudo dpkg-reconfigure otter-greeter
```

Replace `otter-greeter` with the package name of whichever greeter/display manager you have installed and want to use.

---

## Keyboard Layout Problems

**To reconfigure your keyboard layout system-wide:**

```
sudo dpkg-reconfigure kbd-data
sudo dpkg --configure -a
pikman upgrade
```

> ⚠️ **Note:** If you can't type at all (not even at login manager or in `TTY`), use [Access Terminal on Black Screen](#access-terminal-on-black-screen) to get into a terminal first, then run the commands above.

---

## Keyboard Input Failure at Login Screen

**If your keyboard input isn't recognized specifically in `otter-greeter` (but works elsewhere):

### Step 1: Switch to TTY

Press **Ctrl+Alt+F1** to switch to a `TTY`.

### Step 2: Edit `Otter-Greeter` Configuration

```
sudo nano /etc/otter-shell/otter-greeter/otter-greeter-hyprland.lua
```

### Step 3: Add or Edit Keyboard Layout Line

Add (or edit) this line in the `config.kdl` file:

```
kb_layout = "gb",
```

Replace `gb` with your required keyboard layout code (e.g., `us`, `de`, `fr`).

### Step 4: Save and Reboot

- Press **Ctrl+O**, then **Enter** to save
- Press **Ctrl+X** to exit `nano`
- Reboot or restart the greeter service

---

## `AMD` `GPU` `KWin` Crashes (RX 7000/9000 Series)

On some newer `AMD` graphics cards (such as Radeon RX 9070), `KWin` (`Wayland`) can repeatedly crash or fail to initialize, often accompanied by `Unsupported screen format RA24` errors in logs.

A temporary workaround (forcing a software cursor) is available until an upstream fix lands:

[`KWin` Bug: Unsupported Screen Format `RA24` (`AMD` `GPU`s)](05-kwin-ra24-freezing.md)

---

## Bluescreen on Boot

**If you get stuck at a bluescreen:**

1. Press **Tab** in the `rEFInd` bootloader
2. Select an older kernel or try safe mode

If that fails, follow [Access Terminal on Black Screen](#access-terminal-on-black-screen) to get terminal access for further troubleshooting.

---

## Additional Support

You can always ask for further advice on the [`PikaOS Discord`](https://discord.gg/Ky4tUXkMZE).

---

## Related Documentation

System recovery and diagnostics:

* [**Boot Failure Recovery**](../02-installation/13-boot-failure-recovery.md) — Restore system when boot fails
* [**Secure Boot Setup**](../../05-secure-boot/01-overview.md) — Enable Secure Boot for enhanced security
* [**Terminal Access on Black Screen**](../02-installation/10-accessing-the-terminal.md) — Get to terminal on black screen