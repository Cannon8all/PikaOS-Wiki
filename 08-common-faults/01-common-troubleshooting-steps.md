# Common Troubleshooting Steps

## Using PikaOS Paste for logs and command output

When asking for help in the Discord, avoid pasting lengthy logs, terminal output, or command results directly into chat, this clutters the channel and can make issues harder to read and track.

Instead, use _**PikaOS Paste**_:

<https://paste.pika-os.com/>

PikaOS Paste is the project's own encrypted, expiring paste service, and is the preferred way to share this kind of output.

- Copy the full output you want to share (e.g. the result of `pikman upgrade`, a log file, or a config file).
- Go to [paste.pika-os.com](https://paste.pika-os.com/) and paste the content into the box.
- **Optionally** select a language/syntax (e.g. `log`, `bash`), an expiry time, and a password if you'd like the paste protected.
- Click **Create encrypted paste** and copy the generated link.
- Post that link in the relevant Discord channel (e.g. **#update-issues, help-threads...**) instead of the raw text, along with a short description of the problem.

This keeps the channel readable and makes it much easier for helpers to review the full output.

## 1. How to access a terminal TTY from the greeter

**Linux provides virtual terminals called TTYs, separate from your graphical login screen.**

- Press **Ctrl+Alt+F1** (or F1–F6) to switch to a TTY.
- Most function keys F1–F6 are mapped to a TTY; your graphical session usually lives on F7 (or F1, depending on your setup).
- Log in with your normal username and password, you can troubleshoot from there.

## 2. How to access a terminal on a black screen

**Use this method when you can't get a graphical session and can't drop into a TTY either.**

- At the rEFInd bootloader, press **Tab** and select an older kernel. If the system boots normally, the issue is likely with your newest kernel.

**If that doesn't help**

- Go back to the rEFInd bootloader and press **Tab** twice. This reveals the full boot command line.
- Move to the end of the line, add a `space`, then type `3`. press `enter`

**This will land you into a terminal (runlevel 3) for further troubleshooting.**

If neither option works, you can still reach your installed system by chrooting from a live ISO. Follow the guide here:

[Chrooting from a Live ISO in PikaOS](../07-guides/06-chrooting-from-a-live-iso.md)

## 3. Older nvidia card users having bluescreen or greeter issues

**(10 series and older)**

- If you have a bluescreen, press tab and launch into an older kernel and proceed with the commands below in a terminal.

- If you get stuck at the greeter, press Ctrl+Alt F3 to start a TTY terminal, login and proceed with the commands below.

```bash
pikman i pika-nvidia-driver kernel-pika-kernel
```

Proceed to login and if needed remove the faulty kernel or non supported kernel with the PikaOS kernel manager

## 4. Greeter (login manager) issues

**If your greeter fails to start or behaves incorrectly, reconfigure it from a TTY:**

```bash
sudo dpkg-reconfigure otter-greeter
```

Replace `otter-greeter` with the package name of whichever greeter/display manager you have installed and want to use.

## 5. Keyboard layout issues

To reconfigure your keyboard layout system-wide:

```bash
sudo dpkg-reconfigure kbd-data
sudo dpkg --configure -a
pikman upgrade
```

**Note:** If you can't type at all, not even at the login manager or in a TTY, use [Section 1](#1-getting-a-terminal-on-a-black-screen) to get into a terminal first, then run the commands above.

## 6. Keyboard not working in otter-greeter

If your keyboard input isn't recognized specifically in otter-greeter (but works elsewhere):

- Switch to a TTY: **Ctrl+Alt+F1**
- Edit the otter-greeter Hyprland config:

```bash
sudo nano /etc/otter-shell/otter-greeter/otter-greeter-hyprland.lua
```

- Add (or edit) the keyboard layout line:

```lua
kb_layout = "gb",
```

**Replace `gb` with your required keyboard layout code (e.g. `us`, `de`, `fr`).**

- Save (**Ctrl+O**, Enter) and exit (**Ctrl+X**), then reboot or restart the greeter service.

## 7. Plasma/KWin crashing or freezing on newer AMD GPUs

On some newer AMD graphics cards (such as the Radeon RX 9070), KWin (Wayland) can repeatedly crash or fail to initialize, often accompanied by `Unsupported screen format RA24` errors in the logs. A temporary workaround (forcing a software cursor) is available until an upstream fix lands. See the full guide here:

[KWin Bug: Unsupported Screen Format RA24 (AMD GPUs)](05-kwin-ra24-freezing.md)

## 8. Bluescreen

- Press tab in the rEFInd bootloader and select an older kernel or try safe mode.

If that fails follow [Section 2](#2-getting-a-terminal-on-a-black-screen) to get a terminal for further troubleshooting.

You can always ask for further advice on the [PikaOS Discord](https://discord.gg/Ky4tUXkMZE)
