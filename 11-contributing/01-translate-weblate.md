# Translate with Weblate

---

## Table of Contents

- [Why Contribute Translations?](#why-contribute-translations)
- [Quick Start Guide](#quick-start-guide)
  - [Step 2: Select Component Type](#step-2-select-component-type)
  - [Step 3: Choose Sub-component](#step-3-choose-sub-component)
  - [Step 4: Select Your Language](#step-4-select-your-language)
  - [Step 5: Find Untranslated Strings](#step-5-find-untranslated-strings)
  - [Step 6: Translate & Save](#step-6-translate-save)
- [Translation Guidelines](#translation-guidelines)
  - [Preserving Formatting](#preserving-formatting)
  - [Common Pitfalls to Avoid](#common-pitfalls-to-avoid)
- [Translation Best Practices](#translation-best-practices)
  - [Context Matters](#context-matters)
  - [Quality Checks](#quality-checks)
- [Translation Review Process](#translation-review-process)
- [Pro Tips for Translators](#pro-tips-for-translators)
- [Track Your Impact](#track-your-impact)
- [Collaboration Features](#collaboration-features)
  - [Discussion Threads](#discussion-threads)
  - [Translation Memory](#translation-memory)
- [Troubleshooting](#troubleshooting)
- [Related Guides](#related-guides)

---

PikaOS on Weblate to make the distribution accessible to speakers worldwide! Your translations directly impact user experience and grow our global community.

---

## Why Contribute Translations?

- **Global Accessibility**: Remove language barriers for users worldwide
- **Community Growth**: Welcome new users from different linguistic backgrounds
- **Inclusivity**: Make PikaOS truly welcoming for everyone, everywhere
- **Quality Improvement**: Native speakers catch nuances and cultural context

---

## Quick Start Guide

### Step 1: Visit Weblate Project

Open our Weblate instance: [hosted.weblate.org/projects/pikaos](https://hosted.weblate.org/projects/pikaos/)

*Expected result:* You'll see a dashboard showing all available translation components.

---

### Step 2: Select Component Type

Choose what you want to translate:

| Component Type | Description | Examples |
| :--- | :--- | :--- |
| **GUI Applications** | User interface text in apps | PikaOS Welcome, Device Manager |
| **Documentation** | Wiki pages and guides | This documentation, user manuals |
| **System Messages** | Error messages and notifications | Package manager output, system alerts |

---

### Step 3: Choose Sub-component

Select the specific application or documentation set. For example:
- **PikaOS Welcome** — Main welcome application
- **Device Manager** — Hardware configuration tool
- **Wiki Documentation** — All wiki pages in your language

*Expected result:* You'll see a translation dashboard with progress bars and string counts.

---

### Step 4: Select Your Language

**For New Languages:**
1. Click "Add new translation" or "Start new translation"
2. Choose your language from the dropdown
3. Review project guidelines for that component

**For Existing Languages:**
1. Browse the available languages list
2. Click on a language with progress below 100%
3. See untranslated strings ready for review

---

### Step 5: Find Untranslated Strings

Navigate to the **Untranslated** tab to see strings needing translation:

- **Green highlight**: Ready for translation
- **Yellow highlight**: Needs review or has suggestions
- **Red highlight**: Conflicting translations or errors

*Tip*: Start with strings marked as "high priority" or frequently used.

---

### Step 6: Translate & Save

**Translation Process:**
1. Click on an untranslated string to open the editor
2. Review context and source English text
3. Write your translation in the provided field
4. Check for proper formatting (see Guidelines below)

**Saving Options:**
- **Save**: Submit without moving to next string
- **Save and continue**: Submit and jump to next untranslated string
- **Skip**: Move past this string for later

---

## Translation Guidelines

### Preserving Formatting

Always maintain the original structure of strings:

| Type | Example | Do This | Not This |
| :--- | :--- | :--- | :--- |
| **Brackets** | `Must be 512MB!` | `Debe tener 512 MB!` | `Tiene que ser 512 MB!` |
| **Code Blocks** | `[pikaos-welcome]` | `[pikaos-entorno]` | `pikaos-entorno` |
| **Spaces** | ` PikaOS Welcome` | ` Bienvenido de PikaOS` | `Bienvenido de PikaOS` |
| **Symbols** | `⚠️ Warning!` | `⚠️ ¡Advertencia!` | `¡Cuidado! ⚠️` |

---

### Common Pitfalls to Avoid

- **Removing formatting markers**: Keep all brackets, code blocks, and symbols  
- **Changing capitalization**: Match the original's capital style  
- **Omitting spaces**: Preserve leading/trailing whitespace  
- **Altering line breaks**: Keep multi-line strings intact  
- **Translating variables**: Leave `{variable}` placeholders unchanged  

---

## Translation Best Practices

### Context Matters
- **Read the full sentence**: Understand how the string is used
- **Check screenshots**: Some components show preview images
- **Review comments**: Translators may add helpful notes

### Quality Checks

Before submitting:
✅ Read your translation aloud in the target language  
✅ Verify numbers and measurements are correct  
✅ Ensure technical terms match existing translations  
✅ Check for proper punctuation (especially question marks!)  

---

## Translation Review Process

1. **Submit Translation**: Save your work to Weblate
2. **Community Review**: Other translators review suggestions
3. **Project Manager Approval**: Maintainers approve final versions
4. **Merge to Repository**: Approved translations merge into code/docs
5. **Release in Update**: Users see new translations in next update

**Typical timeline:** 1-7 days from submission to approval

---

## Pro Tips for Translators

> 💡 **Tip:** Start with short strings (under 20 words) to build confidence before tackling longer documentation.

> 💡 **Tip:** Use Weblate's "Copy from source" feature if you're unsure about a translation.

> 💡 **Tip:** Join language-specific teams or channels for peer support and terminology discussions.

---

## Track Your Impact

Monitor your contributions:
- **Personal Stats**: View your contribution count on Weblate profile
- **Language Progress**: See how much of the project is translated in your language
- **Community Recognition**: Top contributors featured in release notes

*Example:* If you've translated 500 strings for Spanish, your name appears as a top contributor!

---

## Collaboration Features

### Discussion Threads
- Ask questions about ambiguous strings
- Discuss terminology choices with other translators
- Get clarification from project maintainers

### Translation Memory
- Reuse approved translations for similar strings
- Maintain consistency across different components
- Speed up your translation workflow

---

## Troubleshooting

| Issue | Solution |
| :--- | :--- |
| **Can't find my language** | Request it from project maintainers or start a new translation |
| **String looks wrong in context** | Check the screenshot and comments for usage details |
| **Translation rejected** | Review feedback and adjust accordingly |
| **Conflicting translations** | Wait for resolution or discuss with other translators |

---

## Related Guides

* [**Getting Involved Overview**](../10-getting-involved/01-overview.md#documentation-contributions) — Community contribution paths reference