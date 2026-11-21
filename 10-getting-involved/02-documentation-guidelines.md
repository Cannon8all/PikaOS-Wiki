# Documentation Guidelines

---

## Table of Contents

- [Writing Standards](#writing-standards)
  - [Heading Style](#heading-style)
  - [Emoji Usage](#emoji-usage)
- [Structural Guidelines](#structural-guidelines)
  - [Horizontal Rules (`---`)](#horizontal-rules)
  - [Callout Boxes](#callout-boxes)
- [Data Presentation](#data-presentation)
  - [Tables for Dense Information](#tables-for-dense-information)
  - [Code Examples with Expected Output](#code-examples-with-expected-output)
- [Cross-Linking](#cross-linking)
  - [Related Guides Section](#related-guides-section)
  - [Body Text Links](#body-text-links)
- [Micro-Formatting Best Practices](#micro-formatting-best-practices)
  - [Inline Code](#inline-code)
  - [Bold Leading Phrases](#bold-leading-phrases)
- [Checklist for New Guides](#checklist-for-new-guides)
- [Maintaining Consistency](#maintaining-consistency)

---

Welcome to the PikaOS Wiki documentation standards! This guide explains how to write clear, consistent, and professional wiki pages that help users understand PikaOS.

---

## Writing Standards

### Heading Style

All headings (H1, H2, H3) should be **clean without emojis**. Use descriptive, clear titles:

```markdown
# Gaming on PikaOS

## Quick Start

Install all essential gaming tools:

## Which Proton Version Should I Use?

**Proton** is the compatibility layer that lets Windows games run on Linux.
```

### Emoji Usage

Emojis are **only used inside callout boxes and informational sections**, never in headings:

| Emoji | Purpose | Location |
| :--- | :--- | :---: |
| `💡` | Tips, recommendations | Callout boxes only (`> 💡 **Tip:**`) |
| `⚠️` | Warnings, important notes | Callout boxes only (`> ⚠️ **Warning:**`) |
| `ℹ️` | Informational notes | Callout boxes only (`> ℹ️ **Info:**`) |
| `🔧` | Tool references | Body text or callout boxes |
| `📚` | Reference links | Body text or callout boxes |
| `🔄` | Review/update actions | Best practices lists, body text |
| `📝` | Documentation/writing tasks | Best practices lists, body text |

**Status indicators in tables are acceptable:**
- `✅`, `❌`, `☐` — checklists and table status columns
- `🔴`, `🟡`, `🟢` — priority/status indicators in tables

---

## Structural Guidelines

### Horizontal Rules (`---`)

Use horizontal rules to separate major sections and improve readability:

```markdown
## Section Title

Content here.

---

## Next Section
```

**Best practice:** Place a `---` after the introduction paragraph before the first H2 heading, and between major subsections.

### Callout Boxes

Highlight important information using blockquotes:

**Tips:**
```markdown
> 💡 **Tip:** This is helpful advice for users.
```

**Warnings:**
```markdown
> ⚠️ **Warning:** Important cautionary note here.
```

**Informational:**
```markdown
> ℹ️ **Info:** Additional context or reference information.
```

---

## Data Presentation

### Tables for Dense Information

Convert lists of settings, comparisons, or metrics into tables:

| Setting | Default | Recommended | Impact |
| :--- | :---: | :---: | --- |
| `Parameter` | `0` | **`1`** | High optimization |

### Code Examples with Expected Output

Show expected output for commands to help users verify results:

```bash
pikman upgrade
```

*Expected output:*
```
Reading package lists... Done
Building dependency tree... Done
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

## Cross-Linking

### Related Guides Section

At the bottom of each file, include a "Related Guides" section using this format:

```markdown
## Related Guides

* [**Title**](./relative-path.md) — Brief description (5-8 words) explaining relevance
* [**Another Guide**](../parent-folder/file.md) — Another brief description
```

**Rules:**
- Use relative paths (`./` for same folder, `../` for parent folder)
- Bold the title: `[**Title**]`
- Include a brief description (5-8 words) after an em dash (`—`)
- Sort links alphabetically by title when possible

### Body Text Links

In body text and callout boxes, use standard markdown links without bolding:

```markdown
Check our [BIOS Checklist](../01-getting-started/03-bios-checklist.md) for details.
```

**Rules:**
- Use relative paths (`./` for same folder, `../` for parent folder)
- Do not bold the title in body text
- Include a brief description when appropriate

---

## Micro-Formatting Best Practices

### Inline Code

Use backticks for technical terms, variables, and commands:

```
The `pikman install` command installs packages.
```

### Bold Leading Phrases

In lists, bold the leading phrase to guide the reader's eye:

```markdown
- **Automatic detection**: Finds running games automatically
- **Per-game profiles**: Each game can have custom settings
```

---

## Checklist for New Guides

Before publishing a new wiki page, ensure it includes:

✅ Clean main heading (no emoji)  
✅ Clear introduction explaining the guide's purpose  
✅ Step-by-step instructions where applicable  
✅ Code examples with expected output (for command guides)  
✅ Callout boxes for tips and warnings (`💡`, `⚠️`, `ℹ️`)  
✅ Horizontal rules separating major sections  
✅ Table formatting for settings/comparisons  
✅ Related Guides section at the end  

---

## Maintaining Consistency

When editing existing pages:
- Preserve the existing emoji style if already established
- Add missing callouts or tables where appropriate
- Ensure all links are current and functional
- Use clean headings (no emojis in H1, H2, or H3)

---

> 💡 **Tip:** When in doubt, follow the style of existing guides like [Secure Boot Setup](../07-guides/04-secure-boot.md) or [Gaming on PikaOS](../05-gaming/01-gaming-on-pikaos.md).

---

*For questions about documentation standards, contact the wiki maintainers.*