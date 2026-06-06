# Test Metrics and Reporting — Tracking Progress
> Source: QA Learn the Fundamentals — Module 5, Lesson 4 | roadmap.sh
> Last updated: 2026

---

## What are Test Metrics?

Test metrics are **quantitative indicators used to measure the efficiency, quality, and progress of testing activities**. Without them, QA relies on intuition rather than data — and intuition alone cannot determine if a release is stable enough for production.

> Test metrics = the data that turns QA from an opaque process into a transparent, managed function.

---

## Essential Quality Metrics

---

### 1. Defect Density

Measures the number of bugs discovered in a module **relative to its size** (lines of code or number of requirements).

```
Formula: Defect Density = Total Confirmed Bugs / Size of Module
```

**Example:**

| Module | Bugs Found | Size (requirements) | Defect Density |
|---|---|---|---|
| Payment | 50 | 100 | **0.50** |
| User Profile | 5 | 100 | **0.05** |

The payment module is clearly the higher-risk area. Use defect density to **prioritize regression testing** on the most fragile parts of the system.

---

### 2. Test Case Execution Status

A real-time snapshot of the testing lifecycle showing progress of the test suite against the plan.

**Data points to track:**

| Status | Meaning |
|---|---|
| **Passed** | Test executed and behavior matched requirements |
| **Failed** | Test executed and behavior did not match requirements |
| **Blocked** | Prerequisite failed — test could not be run |
| **Skipped** | Test no longer applicable to the current build |
| **Not Run** | Test has not been executed yet |

**Application:**
> If you are 3 days from release and only 40% of test cases are "Passed" while 30% are "Not Run" — you have an immediate resource or scope issue that must be escalated to stakeholders.

---

### 3. Defect Age

Measures the time elapsed between a bug being opened and its resolution.

```
Formula: Defect Age = Date Closed - Date Opened
```

**Application:** A high average defect age indicates a bottleneck — developers may be overwhelmed, or there is a communication breakdown between QA and engineering. It signals the need to investigate workflow, not just recount bugs.

---

## Reporting Test Progress

A test report is the **bridge between QA and project management**. It must be actionable, concise, and focused on risk — not just raw numbers.

### Weekly Status Report — Standard Structure

| Section | Content |
|---|---|
| **Executive Summary** | High-level assessment: is the build ready for UAT or launch? |
| **Execution Progress** | Visual comparison of planned vs. actual test execution |
| **Top Defects** | List of critical/blocker bugs currently stalling progress |
| **Risk Assessment** | Areas that could not be fully tested due to environment issues or time constraints |

---

## Test Case Lifecycle — Flow

```
         NOT RUN
            │
            ▼
        IN PROGRESS
         /        \
        /          \
   [Pass]        [Bug Found]    [Environment Issue]
      │                │                │
      ▼                ▼                ▼
   PASSED           FAILED           BLOCKED
                       │                │
                       ▼                ▼ (after fix)
                   RETESTING       IN PROGRESS
                    /     \
                   /       \
          [Verified]    [Fix Incomplete]
               │                │
               ▼                ▼
            PASSED           FAILED (reopened)
```

---

## Interpreting Data Trends

The true value of metrics is in **tracking them over time**, not just reading a static snapshot.

---

### Defect Removal Efficiency (DRE)

Tracks how many bugs were caught **before release** versus those found by users in production.

```
DRE = (Bugs found before release / Total bugs) × 100
```

> If DRE is dropping — your testing is losing effectiveness. Review test case coverage and design techniques.

---

### Pass Rate Trend

As you approach the release date, the percentage of passed test cases should **climb steadily**.

```
Healthy trend:   20% → 45% → 70% → 90% → Release ✅
Danger sign:     55% → 57% → 56% → 58% (plateau) ⚠️
```

A **plateau in pass rate** means new bugs are being introduced at the same rate old ones are being fixed — the build is unstable.

---

## The Golden Rule of Reporting

> Never present raw data without context.

```
❌ "20 bugs were found this week."
✅ "20 bugs were found this week — up from 12 last week. The increase is
   concentrated in the payment module following last Thursday's API update.
   This poses a risk to the release date if not addressed by end of sprint."
```

Data is the foundation of your argument when you need to advocate for more time, more resources, or a delayed release.

---

## Key Takeaway

> Metrics transform QA from an art into a science. Defect density tells you where to focus. Execution status tells you how far you've come. Defect age tells you where the process is breaking down. Together, they give you and your stakeholders a clear, honest picture of software quality.

---

## Quick Reference

```
3 Core Metrics:

1. Defect Density
   = Total Confirmed Bugs / Module Size
   → Identifies highest-risk modules for regression focus

2. Test Case Execution Status
   = Passed / Failed / Blocked / Skipped / Not Run
   → Real-time snapshot of testing progress vs. plan

3. Defect Age
   = Date Closed - Date Opened
   → High average = bottleneck in dev or QA workflow

Weekly Report Structure:
  ✔ Executive Summary    (release-ready?)
  ✔ Execution Progress   (planned vs. actual)
  ✔ Top Defects          (blockers and criticals)
  ✔ Risk Assessment      (untested areas, constraints)

Trend Signals:
  DRE dropping      → review test coverage
  Pass rate plateau → build is unstable, new bugs = fixed bugs
```

---

*Module 5 — Test Planning and Strategy*
*Previous: test-scheduling-and-execution.md | Next: risk-based-testing.md*
