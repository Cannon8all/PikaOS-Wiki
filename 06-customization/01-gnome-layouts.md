# GNOME Layouts — Desktop Customization Tool

---

## Table of Contents

- [Purpose](#purpose)
  - [How It Works in PikaOS](#how-it-works-in-pikaos)
  - [Available Layouts](#available-layouts)
- [Why PikaOS Includes It by Default](#why-pikaos-includes-it-by-default)
  - [Immediate Familiarity (Familiar Feel)](#immediate-familiarity-familiar-feel)
  - [Reduced Setup Time (Quick Start)](#reduced-setup-time-quick-start)
  - [Consistency and Reliability (Stable System)](#consistency-and-reliability-stable-system)
  - [Customization Without Complexity (Safe Experimentation)](#customization-without-complexity-safe-experimentation)
- [Limitations and Important Notes](#limitations-and-important-notes)
- [Related Guides](#related-guides)

---

GNOME Layouts is included by default in PikaOS as part of the system's desktop customization tools. It allows users to instantly switch between complete GNOME Shell interface styles without manually configuring extensions or modifying system settings. This integration supports the PikaOS goal of providing a flexible and user-friendly desktop experience from the moment the system is installed.

---

## Purpose

PikaOS includes GNOME Layouts to give users immediate control over how their desktop looks and behaves. Whether someone prefers a Windows-style workflow, a macOS-inspired layout, a Unity-like interface, or a traditional GNOME setup, the tool makes it possible with a single selection.

### How It Works in PikaOS

GNOME Layouts is fully integrated into the PikaOS desktop environment. When a layout is selected, the system applies a curated set of GNOME Shell extensions and configuration changes. These adjustments include:

- Panel and dock placement
- App launcher style
- Workspace behavior
- Hot corner settings
- Extension activation and deactivation

Most changes take effect after a shell reload or logout.

### Available Layouts

The exact selection may vary by release, but PikaOS typically includes layouts inspired by:

- **Windows-style interface** - Bottom taskbar with start menu
- **macOS-style interface** - Top panel and centered dock
- **Unity-like interface** - Left side dock with launcher
- **Traditional GNOME layout** - Minimal changes from stock GNOME
- **PikaOS-specific layouts** - Designed for productivity or familiarity

Each layout is preconfigured to provide a complete and polished experience.

---

## Why PikaOS Includes It by Default

### Immediate Familiarity (Familiar Feel)

Users coming from Windows or macOS can choose a layout that feels natural right away, reducing the learning curve when switching to Linux.

### Reduced Setup Time (Quick Start)

There is no need to manually install or configure extensions. Everything works out of the box.

### Consistency and Reliability (Stable System)

Layouts are tested and maintained as part of the PikaOS ecosystem, ensuring compatibility with system updates.

### Customization Without Complexity (Safe Experimentation)

Users can experiment freely without worrying about breaking their desktop configuration. Layouts provide safe experimentation.

---

## Limitations and Important Notes

Before switching layouts, be aware of these limitations:

- **Third-party dependencies** - Some layouts depend on third-party extensions that may require updates after GNOME Shell changes
- **Custom modifications** - Switching layouts may overwrite custom user modifications to the desktop configuration
- **Required reloads** - A logout or shell restart (`Alt+F2`, type `r`, press Enter) may be required for changes to apply

> 💡 **Tip:** If a layout doesn't work as expected after switching, try logging out and back in, or restart the GNOME Shell with `Alt+F2` → `r`.

---

## Related Guides

* [**Pikman CLI Guide**](../03-system-basics/01-pikman-cli.md) — Command-line package management