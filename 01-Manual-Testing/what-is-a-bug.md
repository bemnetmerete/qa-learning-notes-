# What is a Bug? — Understanding Bug Severity and Priority
> Source: QA Learn the Fundamentals — Module 4, Lesson 1 | roadmap.sh
> Last updated: 2026

---

## What is a Bug?

A bug is any **deviation from the expected or required behavior** of a software application. It can range from minor cosmetic issues to critical errors that crash the system or corrupt data. Bugs arise from mistakes made during the design, coding, or implementation phases of the SDLC.

> Bug = actual behavior ≠ expected behavior.

---

## Types of Bugs

| Type | Description | Example |
|---|---|---|
| **Functional** | A feature doesn't work as intended | A button that doesn't submit a form |
| **Performance** | Affects speed, responsiveness, or stability | Slow loading times, crashes under heavy load |
| **Usability** | Makes the app difficult or confusing to use | Unclear error messages, inconsistent navigation |
| **Security** | Creates vulnerabilities that can be exploited | SQL injection, XSS vulnerabilities, weak passwords |
| **Compatibility** | App malfunctions on certain hardware, OS, or browsers | Broken layout on a specific browser |
| **Cosmetic** | Minor visual defects that don't affect functionality | Misaligned text, blurry logo, typos |

---

## Examples of Bugs — ShopSmart E-Commerce

| Bug Type | Example |
|---|---|
| **Functional** | User adds item to cart, but it doesn't appear |
| **Performance** | Product page takes 10+ seconds to load |
| **Usability** | "Forgot Password" link is hidden at the bottom of the page |
| **Security** | Passwords stored in plain text |
| **Compatibility** | Website displays incorrectly on Internet Explorer 11 |
| **Cosmetic** | Company logo is slightly blurry on high-resolution displays |

---

## Why Bugs Occur

- **Misunderstood requirements** — Developer didn't fully understand the intended behavior
- **Coding errors** — Typos, incorrect logic, memory leaks
- **Complex code** — Poorly written code is more prone to mistakes
- **Time pressure** — Tight deadlines lead to rushed development and inadequate testing
- **Lack of testing** — Insufficient coverage allows bugs to slip through
- **Changing requirements** — Frequent changes introduce inconsistencies

---

## Understanding Bug Severity

Bug severity describes **how badly a bug impacts the system**. It is determined from the **end-user's perspective**.

| Severity Level | Description |
|---|---|
| **Critical** | Complete system failure, data loss, or major security vulnerability — app is unusable |
| **High** | Major functional defect that significantly impacts usability — workaround may or may not exist |
| **Medium** | Noticeable defect that impairs experience but doesn't block usage — workaround usually available |
| **Low** | Minor cosmetic issue or slight inconvenience with minimal impact |

### Severity Examples — ShopSmart

| Severity | Example |
|---|---|
| **Critical** | Payment gateway not working — no purchases can be completed |
| **High** | Users cannot add items to their cart |
| **Medium** | Product search returns irrelevant results |
| **Low** | Typo on the "About Us" page |

### Factors That Influence Severity

- Does the bug prevent a core feature from working?
- Does it cause data loss or corruption?
- Does it create a security vulnerability?
- Is there a workaround available?
- How often does it occur?
- How many users are affected?

---

## Understanding Bug Priority

Bug priority describes **how urgently a bug needs to be fixed**. It is determined from the **business perspective**, considering customer impact, revenue loss, and market reputation.

| Priority Level | Description |
|---|---|
| **Immediate** | Must be fixed right now — critical business impact |
| **High** | Fix as soon as possible — significantly impacting users or operations |
| **Medium** | Fix in the next development cycle |
| **Low** | Fix when resources are available |

### Priority Examples — ShopSmart

| Priority | Example |
|---|---|
| **Immediate** | Payment gateway down — direct revenue loss |
| **High** | Users can't add to cart, especially during a promotional period |
| **Medium** | Search returns irrelevant results, impacting sales |
| **Low** | Typo on the "About Us" page |

### Factors That Influence Priority

- How much revenue is being lost?
- How many customers are affected, and how severely?
- Is the company's reputation at risk?
- Is the bug blocking a release?
- How much effort is required to fix it?
- Are there dependencies that need to be resolved first?

---

## Severity vs. Priority — Key Differences

| | Severity | Priority |
|---|---|---|
| **Definition** | Impact of the bug on the application | Urgency of fixing the bug |
| **Perspective** | End-user | Business |
| **Focus** | How badly the system is affected | How quickly it needs to be resolved |

> A bug can have **high severity but low priority**, or **low severity but high priority** — they are independent of each other.

**Examples:**
- A security vulnerability that's hard to exploit → **High Severity, Medium Priority**
- A typo on the homepage during a major marketing campaign → **Low Severity, High Priority**

---

## Practical Scenarios

### Scenario 1
```
Bug:      App crashes when user tries to print a document
Context:  Printing is a core feature used frequently
Severity: High   — app is unusable for printing
Priority: High   — core feature affected
```

### Scenario 2
```
Bug:      App displays incorrect date format in a specific report
Context:  Report used internally by a small group of users
Severity: Medium — report is still usable
Priority: Medium — limited user impact
```

### Scenario 3
```
Bug:      Security vulnerability allows unauthorized access to user accounts
Context:  Vulnerability is relatively easy to exploit
Severity: Critical  — major security risk
Priority: Immediate — must be fixed before anything else
```

---

## Real-World Example — Banking App

**Bug:** Users can transfer funds even without sufficient balance.

```
Severity: Critical
→ Directly impacts core functionality (fund transfers)
→ Can cause significant financial loss
→ Represents a major security vulnerability

Priority: Immediate
→ Must be fixed right away
→ Dev team should halt other work and focus solely on this
```

---

## Exercise — Practice Assigning Severity & Priority

For each bug below, determine the severity and priority levels and explain your reasoning:

1. A button on the settings page is misaligned
2. The application leaks memory, causing it to slow down over time
3. Users are unable to log in using their Facebook accounts
4. The application displays a generic error message instead of a helpful one

---

## Key Takeaway

> Severity tells you **how bad** the bug is. Priority tells you **how soon** it needs to be fixed. Always assess both — they are related but never the same thing.

---

## Quick Reference

```
Severity Levels (End-User Perspective):
Critical → App unusable, data loss, security breach
High     → Major feature broken, significant impact
Medium   → Noticeable issue, workaround exists
Low      → Minor cosmetic defect

Priority Levels (Business Perspective):
Immediate → Fix now, critical business impact
High      → Fix ASAP, significant user/ops impact
Medium    → Fix next development cycle
Low       → Fix when resources allow

Key Rule:
High Severity ≠ High Priority (always assess independently)
```

---

*Module 4 — Bug Reporting and Tracking*
*Next: writing-bug-reports.md*
