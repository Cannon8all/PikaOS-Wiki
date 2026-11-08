# PikaOS - pika-paste CLI Tool

---

## Table of Contents

- [Usage](#usage)
- [Options](#options)
- [Examples](#examples)
  - [Paste Command Output (with hardware info)](#paste-command-output-with-hardware-info)
  - [Paste a Config File (without hardware info)](#paste-a-config-file-without-hardware-info)
  - [Paste a Screenshot](#paste-a-screenshot)
  - [Password-Protected Paste with Custom Expiry](#password-protected-paste-with-custom-expiry)
- [Related Guides](#related-guides)

---

> ℹ️ **Overview:** `pika-paste` is a command-line pastebin utility that pipes text or images directly to [paste.pika-os.com](https://paste.pika-os.com). It provides a quick way to share logs, config files, command output, or screenshots—especially useful when asking for help in the PikaOS Discord or filing bug reports.

**Key Feature:** By default, text pastes are prefixed with `pikafetch` output (basic hardware/system info), giving context for support requests without needing to paste system details separately.

---

## Usage

The command follows this structure:

```bash
pika-paste [options]
```

> ℹ️ **Info:** `pika-paste` reads from standard input, so it's designed to be used at the end of a pipe: `<command> | pika-paste`

**Success Output:** Prints the resulting paste URL as a clickable link in your terminal (e.g., `https://paste.pika-os.com/...`) that you can copy and share.

## Expiry Settings

- **Default:** 7 days (604,800 seconds)
- **Override:** Use `--ttl-seconds` to customize expiry time (1 to 31,536,000 seconds / up to 1 year)

---

## Options

| Option | Description | Default/Range |
| :--- | :---: | :--- |
| `--no-hwinfo` | Do not prepend pikafetch output | Disabled by default |
| `--language NAME` | Syntax highlighting language | `log` (default) |
| `--password PASSWORD` | Protect paste with a password | None (public by default) |
| `--ttl-seconds SECONDS` | Expiry time in seconds | 604,800 (7 days) |
| `--kind text\|image` | Override detected paste type | Auto-detect |
| `--mime TYPE` | Override detected MIME type | Auto-detect |
| `-h, --help` | Show help message | — |

---

## Examples

### Paste Command Output (with hardware info)

Recommended for support requests:

```bash
journalctl -b -1 -p err --no-pager | pika-paste
```

> 💡 **Tip:** This includes system context automatically, making it easier for others to help diagnose issues.

### Paste a Config File (without hardware info)

Use `--no-hwinfo` and specify the language:

```bash
cat ~/.config/hypr/hyprland.conf | pika-paste --no-hwinfo --language ini
```

### Paste a Screenshot

Pipe an image file directly:

```bash
pika-paste < screenshot.png
```

**Example with specific file:**

```bash
pika-paste < ~/Pictures/Screenshots/"Screenshot from 2026-08-07 14-24-10.png"
```

> ⚠️ **Note:** Supported image formats: PNG, JPEG, GIF, WebP

### Password-Protected Paste with Custom Expiry

For sensitive data:

```bash
cat secrets.log | pika-paste --password "hunter2" --ttl-seconds 3600
```

This creates a paste that:
- Requires password `hunter2` to view
- Expires after 1 hour (3,600 seconds)
- Contains contents from `secrets.log`

---

## Related Guides

* [**Troubleshooting Common Faults**](../08-common-faults/01-common-troubleshooting-steps.md) — Diagnose and fix common issues
* [**PikaOS Device Manager**](07-pikaos-device-manager.md) — GPU driver management tool