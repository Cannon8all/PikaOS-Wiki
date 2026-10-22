# Pikman GUI

## Main Updates Page

![pikman-update-manager-main-updates-page.png](/pikman-update-manager-main-updates-page.png)

This Page shows how many updates from each package manager are available, and their sum total, and the commit button on the bottom right of the screen allows installing them all.

## Native Updates (APT)

### Overview

![pikman-native-update-page.png](/pikman-native-update-page.png)

This page show a list of packages with upgrades available, each row provides the following information:

- Currently installed version.
- The version you will receive, with the version difference being highlighted
- The Package [Architecture](https://en.wikipedia.org/wiki/Computer_architecture)

At the end of a row there's a checkbutton that marks the package for the upgrade (The package is marked by default).

### Description Tab

![pikman-native-update-page-description.png](/pikman-native-update-page-description.png)

By clicking on the row you can expand its contents revealing the package description.

### Additional Info Tab

![pikman-native-update-page-commit.png](/pikman-native-update-page-commit.png)

You can also view the additional info tab, which reveals:

- The package maintainer/developer name.
- The Download Size.
- The Actual Package size on the disk after it's uncompressed.

### Download URIs Tab

![pikman-native-update-page-info.png](/pikman-native-update-page-info.png)

This tab just shows where the package is exactly coming from.

### Transaction Window

![pikman-native-update-page-url.png](/pikman-native-update-page-url.png)

The Commit page shows all the details of your selection.

## Flatpak Updates

### Overview

![pikman-flatpak-update-page.png](/pikman-flatpak-update-page.png)

This page is practically identical to its native counterpart, however it shows the remote name, alongside the installation target (System/User)

## APT Settings

### Overview

![pikman-apt-settings.png](/pikman-apt-settings.png)

- At the top of the page you can enter a mirror url for the PikaOS Repos (aka the system repo).

- In the middle there's list of 3rd-party unofficial APT Sources, these can appear when you install 3rd party scripts or apps, to auto-update them, they are usually fine, but can cause technical or security issues.

- If the sources have `(Legacy)` `(Legacy src)` they use the old deb `.list` format, If not they use the modern [deb822 standard](https://manpages.debian.org/unstable/apt/sources.list.5.en.html#DEB822-STYLE_FORMAT).

> Make sure to only add ones you TRUST!

- at the bottom there's 3 buttons to `Add new repository` - `Edit Selected Repo` - `Delete Selected Repo`

  We will go over them soon.

- Finally there's the Automatic Update Checking toggle, if it's enabled, the update manager will do an `apt update` (aka refresh the repos and check for new upgrades) at an interval you define in the button next to the toggle. (The value is in Hours)

### Add new repository page

Explaining the values:

- `Name`: Just the visual name of repository, it doesn't matter what it is, and APT doesn't really read it.
- `URI`: Just the base URL of the repository.
- `Suites`: The version of the repo this `sid` or `unstable` is recommended unless the 3rd party has `pika` specific repository, or it could use universal version like `beta`.
- `Components`: usually is `main` or something like `non-free` or even the program name like `steam`
- `Architectures`: An optional value, leave empty unless the repo errors for not having an `i386` arch, then simply input `amd64` so it only scans for x86_64
- `With source repository`: Enable if you want to get the source code repo via `apt source`
- Signing: Important security measure to prevent [Man in the middle Attacks](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) and other security risks.
  - Sign by Keyring: Simply uses the APT Keyring, no extra input need.
  - Sign by File: Input the path to repository Keyfile, the repository will use it for Verification.
  - Sign by URL: The Update manager will automatically fetch it and store in a safe place for the repo to use.

### Edit Selected Repository Page

![pikman-apt-settings-edit.png](/pikman-apt-settings-edit.png)

Simply allows editing the same values in the `Add` page

## Flatpak Settings

### Overview

![pikman-flatpak-settings.png](/pikman-flatpak-settings.png)

Shows a list of installed remotes and their installation locales `System`/`User`

However they are immutable, can only be added or removed.

- at the bottom there's 3 buttons to `Add remote by URL` - `Add remote by file` - `Delete Selected Remote`

### Add remote by URL

![pikman-flatpak-settings-add-url0.png](/pikman-flatpak-settings-add-url0.png)

Explaining the values:

- `Remote Name`: Just the visual name of remote, it doesn't matter what it is, and Flatpak doesn't really use it.
- `Remote Ref URL`: The url to the flatpak remote usually ends with `.flatpakrepo`
- `User`: Installs the remote on the current user home directory.

  (allows keeping your apps after reinstalling/distrohopping)

  (Can't be accessed by other users on the same system)

- `System`: Install the remote in system root.

  (Allows all users to access the applications)

  (Gets wiped if the system is wiped)

### Add remote by File

![pikman-flatpak-settings-add-flatref.png](/pikman-flatpak-settings-add-flatref.png)

Simply type the path to the flatpakref or press the button to Browse for it

- `User`: Installs the remote on the current user home directory.

  (allows keeping your apps after reinstalling/distrohopping)

  (Can't be accessed by other users on the same system)

- `System`: Install the remote in system root.

  (Allows all users to access the applications)

  (Gets wiped if the system is wiped)
