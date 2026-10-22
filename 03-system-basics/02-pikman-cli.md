# PikaOS Package Manager CLI

## Overview

Pikman is the package manager for PikaOS. It is a dynamic tool for installing, removing, and updating your system. This entry is for the Command Line Interface (CLI) version of Pikman. Please see the Pikman Graphic User Interface (GUI) entry if you are interested in a graphical tool.

## Usage

Pikman follows the following structure for commands

```text
pikman [global options] command [command options] [arguments...]
```

## Available Commands

```text
autoremove  Remove all unused packages
clean, cl   Clean the package manager cache
enter       Enter the container instance for select package manager
export      Export/Recreate a program's desktop entry from the container
init        Initialize a managed container
install, i  Install the specified package(s)
list, l     List installed packages
log         Show package manager logs
purge       Fully purge a package
run         Run a command inside a managed container
remove, r   Remove an installed package
search, s   Search for a package
show        Show details for a package
unexport    Unexport/Remove a program's desktop entry
update      Update the list of available packages
upgrade     Upgrade the system by installing/upgrading available packages
upgrades    List the available upgrades
help, h     Shows a list of commands or help for one command
```

## Global Options

```text
--arch, --aur    Install Arch packages (including from the AUR) (default: false)
--fedora, --dnf  Install Fedora packages (default: false)
--alpine, --apk  Install Alpine packages (default: false)
--flatpak, --fl  Install Flatpak packages (default: false)
--name value     Name of the managed container
--help, -h       show help (default: false)
--version, -v    Version number (default: false)
--installed     List installed packages with "list" command (default: false)
```

## System Updates

Pikman provides the ability to update your PikaOS system.

> **Please note the use of SUDO is NOT required and should not be invoked when using Pikman**
>
> **Pikman self authenticates when required.**

To update available system updates enter:

```bash
pikman update
```

To view available system updates enter:

```bash
pikman updates
```

If you wish to **both** check for system updates **and** apply them only the following command is required:

```bash
pikman upgrade
```

To update container applications use the appropriate flag along with the upgrade command. In this example we will update arch user repository applications.

```bash
pikman --aur upgrade
```

To update flatpaks use the appropriate flag along with the update command. This is a deviation from the rest of Pikman's commands to keep it inline with flatpaks update command which prefers the use of 'update' over 'upgrade' In this example we will update flatpaks.

```bash
pikman --flatpak update
```

## PikaOS Native Application Management

Pikman can be used to search for, install, and remove native applications found in its optimized repository.

**Searching**:

To search for an application in the repository use the search command. In the following example we will search for the terminal shell called fish:

```bash
pikman search fish
```

**Installing**:

Once you have found the name of the application as it is listed in the repository you may install it with the install command. Following our example:

```bash
pikman install fish
```

> **Note that applications installed by pikman in the command line interface (CLI) will appear in your application launcher with no additional steps required.**

**Removing**:

To remove a package, you may do so using the remove command, or for a more thorough removal of an application and its dependencies you may use the purge command. In the following example we will remove fish using the standard command:

```bash
pikman remove fish
```

## Pikman Container Management

Pikman allows you to install packages from other distributions using the appropriate Global Options flags, (i.e. --aur for the arch user repository) through an implementation of APX.

## Creating Your First Container

First initialize the container that you wish to install a package from with the following command (replace the example aur with your preferred distribution):

```bash
pikman --aur init
```

Pikman will initialize a new container by downloading the appropriate files and setting them within the APX application.

## Installing Your First Container Package

> _**Please ensure the name you are using is the exact name your containers distribution uses for the application or the installation will fail as the application cannot be found**_

In the following example we will be installing Youtube Music from the Arch User Repository:

```bash
pikman --aur install youtube-music
```

## Exporting Your Container Package To The Application Launcher

After you install your package, you may wish to make the package viewable in your GUI application launcher. Pikman provides this functionality. Using the same example:

```bash
pikman --aur export youtube-music
```

## Removing A Container Package From The Application Launcher

Should you wish to remove a package from the application launcher you may do so with the unexport command. Using the same example:

```bash
pikman --aur unexport youtube-music
```

> **Please note that unexporting a package does not remove it from your system, it merely removes it from your application launcher. See the remove command to remove a package from your system.**
