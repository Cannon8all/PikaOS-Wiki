# PikaOS - pika-paste CLI

## Overview

`pika-paste` is a command-line pastebin utility.

> It pipes text or an image (PNG, JPEG, GIF, or WebP) directly to [paste.pika-os.com](https://paste.pika-os.com), making it a quick way to share logs, config files, command output, or screenshots — for example when asking for help in the PikaOS Discord or filing a bug report. By default, text pastes are prefixed with `pikafetch` output (basic hardware/system info), which is useful for support requests since it gives context on your system without you needing to paste it separately.

## Usage

`pika-paste` follows the following structure for commands

```text
pika-paste [options]
```

## Options

```text
--no-hwinfo           Do not prepend pikafetch output
--language NAME       Syntax language (default: log)
--password PASSWORD   Protect paste with a password
--ttl-seconds SECONDS Expiry from 1 to 31536000 (default: 604800)
--kind text|image     Override detected paste kind
--mime TYPE           Override detected MIME type
-h, --help            Show this help
```

`pika-paste` reads from standard input, so it's meant to be used at the end of a pipe:

```bash
<command> | pika-paste
```

> On success, pika-paste prints the resulting paste URL as a link directly in your terminal (e.g. `https://paste.pika-os.com/...`), which you can then copy and share.
>
> By default, pastes expire after 7 days (604800 seconds) unless you override it with `--ttl-seconds`.

## Examples

**Paste command output (with hardware info, useful for support requests):**

```bash
journalctl -b -1 -p err --no-pager | pika-paste
```

**Paste a config file without hardware info:**

```bash
cat ~/.config/hypr/hyprland.conf | pika-paste --no-hwinfo --language ini
```

**Paste a screenshot:**

```bash
pika-paste < screenshot.png
```

Example:

```bash
pika-paste < ~/Pictures/Screenshots/"Screenshot from 2026-08-07 14-24-10.png"
```

**Paste something password-protected that expires in an hour:**

```bash
cat secrets.log | pika-paste --password "hunter2" --ttl-seconds 3600
```

Example:

```bash
cat ~/Documents/secrets.log | pika-paste --password "hunter2" --ttl-seconds 3600
```
