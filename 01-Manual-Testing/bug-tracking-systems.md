# Introduction to Bug Tracking Systems
> Source: QA Learn the Fundamentals — Module 4, Lesson 3 | roadmap.sh
> Last updated: 2026

---

## What is a Bug Tracking System?

A bug tracking system (also called a defect tracking or issue tracking system) is a software application that helps development teams **record, assign, track, and resolve software defects** in a structured and centralized way.

> Bug tracking system = the single source of truth for every bug on a project.

---

## Key Features

| Feature | Description |
|---|---|
| **Bug Reporting** | Submit bug reports with steps to reproduce, expected/actual results |
| **Bug Tracking** | Centralized repository — track status, priority, and assigned developer |
| **Workflow Management** | Define bug lifecycle statuses (Open → In Progress → Resolved → Closed) |
| **Assignment & Notifications** | Assign bugs to developers; auto-notify on assignment or status change |
| **Reporting & Analytics** | Generate reports, identify trends, track team progress |
| **Search & Filtering** | Find bugs by ID, status, priority, assignee, and more |
| **Tool Integration** | Connect with Git, Jenkins, test management tools, and more |

---

## Benefits of Bug Tracking Systems

| Benefit | Description |
|---|---|
| **Improved Communication** | Central platform — everyone knows what's open, in progress, or fixed |
| **Increased Efficiency** | Streamlines the full bug resolution cycle |
| **Better Organization** | Structured management — no bugs fall through the cracks |
| **Enhanced Collaboration** | Developers, testers, and stakeholders work from the same system |
| **Data-Driven Decisions** | Bug data reveals patterns that improve future development |
| **Audit Trail** | Full history of all changes for compliance and accountability |

---

## Popular Bug Tracking Tools

| Tool | Type | Best For |
|---|---|---|
| **Jira** | Proprietary (Atlassian) | Large teams, Agile workflows, deep customization |
| **Bugzilla** | Open-source (Mozilla) | Free, simple, great for open-source projects |
| **Azure DevOps** | Proprietary (Microsoft) | Teams using Microsoft ecosystem |
| **Redmine** | Open-source | Project management + bug tracking combined |
| **Trello** | Web-based (Kanban) | Lightweight bug management via boards |
| **Linear** | Proprietary | Developer-focused, fast, clean UI |

---

## Jira — Deep Dive

Jira is the most widely used issue tracking tool in the industry, developed by Atlassian.

### Key Features
- **Customizable Workflows** — define statuses and transitions to match your team's process
- **Advanced Search & Filtering** — find issues quickly using powerful query options
- **Reporting & Analytics** — track velocity, trends, and bug density
- **Agile Support** — built-in Scrum and Kanban boards
- **Integrations** — Git, Jenkins, Confluence, test management tools
- **User Roles & Permissions** — control who can view, edit, or close issues

### Jira Bug Lifecycle Example — "Add to Cart" Button Not Working

```
Step 1: Tester creates a new issue → Issue Type: Bug
Step 2: Tester fills in description, steps to reproduce, expected/actual result
Step 3: Tester assigns the bug to a developer
Step 4: Developer investigates → finds JavaScript error on product page
Step 5: Developer fixes the code → adds comment explaining the fix
Step 6: Developer changes status → "Resolved"
Step 7: Tester retests the fix → confirms it works
Step 8: Tester changes status → "Closed"
```

---

## Bugzilla — Deep Dive

Bugzilla is a free, open-source bug tracking system developed by the Mozilla Foundation. It is a popular choice for open-source projects and teams needing a no-cost solution.

### Key Features
- Bug reporting, tracking, and workflow management
- Assignment and email notifications on status changes
- Customizable fields for capturing specific information
- Reporting and analytics tools

### Bugzilla Bug Lifecycle Example — Security Vulnerability in Open-Source CMS

```
Step 1: User reports a security vulnerability → Severity: Security Vulnerability
Step 2: User provides description, reproduction steps, and potential impact
Step 3: Bug assigned to a security expert
Step 4: Expert investigates → confirms critical vulnerability (unauthorized access risk)
Step 5: Expert fixes the vulnerability → comments with explanation
Step 6: Expert changes status → "Resolved"
Step 7: Team releases a new version with the security fix
Step 8: Bug report closed
```

---

## Linear — Hypothetical Scenario

A startup uses Linear for its mobile app development due to its speed and developer-friendly design.

```
Step 1: QA tester finds app crashes on certain Android devices during profile picture upload
Step 2: Tester creates issue in Linear → includes device model, Android version, steps to reproduce
Step 3: Issue assigned to the Android developer responsible for image uploads
Step 4: Developer reproduces the crash on a test device using the provided info
Step 5: Developer identifies a memory management issue specific to those devices
Step 6: Developer fixes the issue → commits code → marks issue "Resolved"
Step 7: QA tester verifies fix on affected devices
Step 8: Tester confirms crash is gone → closes the issue
```

---

## Bug Lifecycle — Universal Flow

```
OPEN → IN PROGRESS → RESOLVED → CLOSED
         ↑                ↓
         └──── REOPEN ────┘
              (if fix fails)
```

| Status | Meaning |
|---|---|
| **Open** | Bug reported and confirmed, not yet assigned |
| **In Progress** | Developer is actively working on the fix |
| **Resolved** | Developer has applied a fix |
| **Closed** | Tester verified the fix — bug is gone |
| **Reopened** | Fix didn't work — bug sent back to development |

---

## Exercises

1. **Jira Bug Report** — You find that search functionality is broken on a web app. Write a full Jira bug report including summary, description, steps to reproduce, expected/actual result, severity, priority, and component.

2. **Bugzilla Workflow** — Describe the full lifecycle of a bug in Bugzilla from initial report to closure. Include all statuses and the actions taken at each stage.

3. **Feature Request** — Write a clear feature request for adding Google Calendar integration to a project management app. Include the benefit and potential use cases.

4. **Linear Issue** — A UI element in a mobile app is not displaying correctly on smaller screens. Write a detailed Linear issue description with all the information a front-end developer would need to reproduce and fix it.

---

## Key Takeaway

> Bug tracking systems are not just tools — they are the communication backbone of a QA process. A bug that isn't tracked is a bug that gets forgotten. As a QA engineer, your ability to use these systems effectively is just as important as your ability to find the bugs in the first place.

---

## Quick Reference

```
Popular Tools:
Jira        → Industry standard, Agile-ready, highly customizable
Bugzilla    → Free, open-source, simple
Azure DevOps → Microsoft ecosystem
Linear      → Fast, clean, developer-focused

Bug Lifecycle:
OPEN → IN PROGRESS → RESOLVED → CLOSED
                         ↓
                      REOPEN (if fix fails)

Key Features to Know:
✔ Bug reporting and tracking
✔ Workflow and status management
✔ Assignment and notifications
✔ Reporting and analytics
✔ Integration with Git, CI/CD tools
```

---

*Module 4 — Bug Reporting and Tracking*
*Previous: writing-bug-reports.md | Next: bug-lifecycle.md*
