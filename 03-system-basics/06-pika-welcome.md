# PikaOS Welcome

The **PikaOS Welcome App** is a Rust-based GTK4 + Libadwaita application that streamlines the setup process on PikaOS. It helps new users get their desktop environment configured quickly and painlessly—no terminal needed (unless you want to).

The welcome app offers a curated, centralized setup experience that ensures:

- You’re not missing critical drivers or codecs
- Gaming tools and peripherals are installed and configured easily
- No need to dig through documentation. No wondering what you forgot.

By default, the Welcome App will **open automatically at each startup** to help guide new users. You can disable this at any time by **unchecking** the `Show on startup` box at the top-left corner of the window.

![welcome.png](/welcome.png)

## Key Features

### Setup Steps

Quickly install, configure and maintain the essentials:

- **Update My System**

  This launches the **Pikman Update Manager** where installed packages are updated.

- **Install Patented Media Codecs and Libraries**

  Adds codecs like FFMPEG, VA-API, and more to ensure video and audio playback works out of the box.

- **Setup Printer Support**

  Installs CUPS and printer drivers. These are excluded by default for security-conscious setups.

- **Open Driver Manager**

  Helps you install proprietary NVIDIA drivers, CPU microcode, and more with a few clicks.

- **Open Kernel Manager**

  Switch between kernel versions and schedulers for performance tuning or hardware compatibility.

- **Software Manager Access**

  Quickly launch the **PikaOS Software Manager** to explore and install packages.

- **Install WebApps**

  Run your favorite web apps (like Spotify, Discord, etc.) as native windows using your browser as a backend.

### Recommended Additions

Here you'll find hand-picked tools and packages for gamers and creatives like Steam, OBS, font support and more:

- **PikaOS Game Utilities**

  One-click install for Steam, Lutris, MangoHud, VKBasalt, Wine, Winetricks, and more.

- **Game Utilities Extras**

  Adds Heroic Games Launcher and Bottles.

- **Device Configs for Controllers & VR Gear**

  Udev rules for HID gamepads, VR devices, and specialty controllers.

### Other Stuff

- For you to explore!
