# Feedback & Suggestions

---

## Table of Contents

- [Where to Submit Feedback](#where-to-submit-feedback)
- [Project Boards](#project-boards)
- [Issue Types](#issue-types)
- [Status Workflow](#status-workflow)
- [How to Submit Effective Feedback](#how-to-submit-effective-feedback)
  - [For Bug Reports](#for-bug-reports)
  - [For Feature Requests](#for-feature-requests)
- [Follow Project Progress](#follow-project-progress)
  - [Roadmap View](#roadmap-view)
  - [Changelog](#changelog)
- [Search & Filter](#search-filter)
- [Community Engagement](#community-engagement)
  - [Voting on Features](#voting-on-features)
  - [Discussion Threads](#discussion-threads)
- [Response Time Expectations](#response-time-expectations)
- [What Happens After Submission?](#what-happens-after-submission)
  - [Review Process](#review-process)
  - [If Your Request is Declined](#if-your-request-is-declined)
- [Track Your Feedback](#track-your-feedback)
- [Quick Links](#quick-links)
- [Related Guides](#related-guides)

---

Share your feedback, follow the project roadmap, and see what features have shipped! Your input helps shape PikaOS's development priorities.

---

## Where to Submit Feedback

All feedback and feature requests are handled through our structured project board:

**Main Platform:** [PikaOS Projects](https://projects.pika-os.com/)

**Sign-in Required:** Use your Discord account to submit feedback

*Expected result:* You'll be redirected to authenticate with Discord, then see the project dashboard.

---

## Project Boards

Our projects are organized by component:

| Board Name | Focus Area | Examples |
| :--- | :--- | :--- |
| **Otter-shell** | Custom shell environment | Commands, features, improvements |
| **Pika** | Core PikaOS system | Package manager, Welcome app, settings |
| **Pika Sites** | Web properties | Documentation, website, download mirrors |

---

## Issue Types

When creating a new feedback item, select the appropriate type:

- **Bug**: Something isn't working as expected
  - *Example:* "Package manager shows error on upgrade"

- **Feature**: New functionality or enhancement
  - *Example:* "Add dark mode to Welcome application"

- **Improvement**: Make existing features better
  - *Example:* "Speed up boot time by optimizing startup services"

---

## Status Workflow

Track the lifecycle of any feedback item:

| Status | Meaning | What to Expect |
| :--- | :--- | :--- |
| **Pending** | Needs initial review | Awaiting triage from maintainers |
| **Reviewing** | Being evaluated | Maintainers discussing feasibility |
| **Planned** | Approved for implementation | On roadmap, not yet started |
| **In Progress** | Actively being worked on | Development underway |
| **Completed** | Feature/fix implemented | Ready for next release |
| **Closed** | Resolved or declined | No further action needed |

---

## How to Submit Effective Feedback

### For Bug Reports

Include these details:
1. **Clear title**: Summarize the issue in one sentence
2. **Steps to reproduce**: Numbered list showing how to trigger the bug
3. **Expected behavior**: What should happen normally
4. **Actual behavior**: What actually happens instead
5. **Environment details**: PikaOS version, hardware specs if relevant

*Example:*
```markdown
**Title:** Package manager crashes during upgrade

**Steps:**
1. Open terminal
2. Run `pikman upgrade`
3. Wait for dependency resolution

**Expected:** Packages update successfully
**Actual:** Terminal shows segmentation fault error

**Environment:** PikaOS 2024.1, NVIDIA GPU system
```

### For Feature Requests

Include these details:
1. **Problem statement**: What issue or need does this address?
2. **Proposed solution**: How should it work?
3. **Use case example**: When would you use this feature?
4. **Alternatives considered**: Other approaches you've thought about

*Example:*
```markdown
**Title:** Add automatic backup to external drive

**Problem:** Currently need manual commands for backups

**Solution:** Welcome app includes one-click backup option

**Use case:** Weekly automated backups without terminal knowledge

**Alternative:** Could use existing tools like Timeshift with GUI wrapper
```

---

## Follow Project Progress

### Roadmap View

See upcoming features and their planned release: [PikaOS Roadmap](https://projects.pika-os.com/roadmap)

*Expected result:* Timeline view showing features organized by quarter or milestone.

### Changelog

Track what's new in each release: [Changelog](https://projects.pika-os.com/changelog)

*Tip:* Check the changelog before submitting feedback to avoid duplicate requests!

---

## Search & Filter

Make the most of the project board:

**Search Bar:** Type keywords to find related issues  
**Filters:** Narrow by status, type, or assignee  
**Sort Options:** Order by date created, votes, or priority  

*Pro tip:* Use filters to see only "Planned" items for your area of interest.

---

## Community Engagement

### Voting on Features
- Upvote features you'd like to see implemented
- Higher vote counts increase priority
- Check existing votes before submitting similar requests

### Discussion Threads
- Comment on issues to share experiences
- Provide additional details or workarounds
- Stay updated on implementation progress

---

## Response Time Expectations

| Item Type | Typical Response Time |
| :--- | :--- |
| **Bug Reports** | 24-72 hours |
| **Feature Requests** | 3-7 days |
| **Improvement Suggestions** | 1-2 weeks |
| **High Priority Issues** | Within 24 hours |

> 💡 **Tip:** Provide complete information in your initial submission to avoid back-and-forth questions.

---

## What Happens After Submission?

### Review Process
1. **Triage**: Maintainers review and categorize the feedback
2. **Labeling**: Add tags for priority, component, and status
3. **Discussion**: Community may weigh in with additional insights
4. **Decision**: Approved items move to "Planned" or "In Progress"

### If Your Request is Declined
- Maintainers will provide reasoning
- Alternative solutions may be suggested
- You can discuss the decision respectfully

---

## Track Your Feedback

- **Your Dashboard**: View all submissions you've created
- **Notifications:** Get updates when status changes
- **Milestone Tracking**: See which features reached completion

*Tip:* Bookmark your personal dashboard for quick access to your contributions!

---

## Quick Links

| Resource | Purpose | Link |
| :--- | :--- | :--- |
| **New Issue** | Submit feedback | [Create New](https://projects.pika-os.com/issues/new) |
| **Roadmap** | See upcoming features | [View Roadmap](https://projects.pika-os.com/roadmap) |
| **Changelog** | Track releases | [Release Notes](https://projects.pika-os.com/changelog) |
| **Documentation** | Wiki guides | [Wiki Home](../README.md) |

> ⚠️ **Note:** Verify that `projects.pika-os.com` is the correct URL for the PikaOS issue tracker and roadmap. Update links if the project uses a different platform (e.g., GitHub, GitLab).

---

## Related Guides

* [**Getting Involved Overview**](../10-getting-involved/01-overview.md#community-participation) — Community contribution paths reference