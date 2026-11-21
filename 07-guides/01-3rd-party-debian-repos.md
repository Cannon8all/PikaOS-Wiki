# 3rd-Party Debian Repositories Setup Guide

---

## Table of Contents

- [Problem Description](#problem-description)
  - [Root Cause](#root-cause)
- [Solution: Specify Valid Codename Manually](#solution-specify-valid-codename-manually)
  - [Modified Command Format](#modified-command-format)
- [Examples](#examples)
  - [CoolerControl Installation](#coolercontrol-installation)
  - [General Pattern for Other Repositories](#general-pattern-for-other-repositories)
- [Important Considerations](#important-considerations)
  - [Security & Compatibility](#security-compatibility)
  - [When NOT to Use This Method](#when-not-to-use-this-method)
- [Troubleshooting](#troubleshooting)
  - [Still Getting Invalid Codename Errors?](#still-getting-invalid-codename-errors)
  - [Repository Key Errors?](#repository-key-errors)
- [Related Guides](#related-guides)

---

`PikaOS` is based on `Debian`, but some 3rd-party repositories may fail to install correctly due to codename mismatches. This guide explains how to manually specify valid `Debian` codenames.

---

## Problem Description

You've added a 3rd-party repository for an application, but the installation fails or reports invalid distribution names.

### Root Cause

Many 3rd-party applications provide automated setup scripts that attempt to detect your distribution:

```bash
curl -1sLf \
'https://dl.cloudsmith.io/public/coolercontrol/coolercontrol/setup.deb.sh' \
| sudo -E bash
```

**The Issue:** These scripts expect standard `Debian` codenames like `sid` or `trixie`, but on `PikaOS` they receive `pika` which is **not a valid `Debian` distribution name**. This causes repository setup to fail unless the 3rd-party repo has created a specific `Pika` branch (which is uncommon).

---

## Solution: Specify Valid Codename Manually

Manually provide a valid `Debian` codename when running the installation script. Use either:
- `trixie` (`Debian` testing) - Recommended for stability
- `sid` (`Debian` unstable) - For latest packages

### Modified Command Format

Add `distro` and `codename` parameters before `bash`:

```bash
curl -1sLf \
'https://dl.cloudsmith.io/public/coolercontrol/coolercontrol/setup.deb.sh' \
| sudo -E distro=debian codename=trixie bash
```

> 💡 **Tip:** Always verify the script URL is from an official source before running it with elevated privileges.

---

## Examples

### CoolerControl Installation

Run their install script with manually specified `Debian` parameters:

```bash
curl -1sLf \
'https://dl.cloudsmith.io/public/coolercontrol/coolercontrol/setup.deb.sh' \
| sudo -E distro=debian codename=trixie bash
```

Then follow the normal installation steps provided by `CoolerControl`.

### General Pattern for Other Repositories

For any 3rd-party `Debian` repository setup script:

1. **Download and inspect** the script first (optional but recommended)
2. **Add parameters:** `distro=debian codename=trixie`
3. **Pipe to `bash` with `sudo`:** `| sudo -E distro=debian codename=trixie bash`

---

## Important Considerations

### Security & Compatibility

- **Verify repository sources** before adding them to your system
- **Test applications** after installation to ensure compatibility
- **Monitor for updates** from 3rd-party maintainers

### When NOT to Use This Method

- If the application provides a native PikaOS package (use that instead)
- If the repository already supports Debian testing/unstable directly
- For critical production systems where stability is paramount

---

## Troubleshooting

### Still Getting Invalid Codename Errors?

Try using `sid` instead of `trixie`:

```bash
| sudo -E distro=debian codename=sid bash
```

### Repository Key Errors?

Some repositories require manual key import:

1. Download the GPG key from the provider's website
2. Add it to your system's keyring:
   ```bash
   sudo apt-key add repository-key.gpg
   ```

---

## Related Guides

* [**Documentation Guidelines**](../10-getting-involved/02-documentation-guidelines.md) — Markdown standards reference