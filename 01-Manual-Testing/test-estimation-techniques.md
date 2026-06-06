# Test Estimation Techniques — Effort and Time
> Source: QA Learn the Fundamentals — Module 5, Lesson 2 | roadmap.sh
> Last updated: 2026

---

## What is Test Estimation?

Test estimation is the process of **predicting the effort and time required to complete testing activities**. Accurate estimates are essential for project planning, resource management, and setting realistic stakeholder expectations.

> Test estimation = forecasting how long testing will take and what it will cost in time and people.

---

## Factors That Influence Test Estimation

| Factor | Impact |
|---|---|
| **Project Complexity** | More interconnected modules, integrations, and business logic = more testing effort |
| **Team Skills & Experience** | Experienced teams test faster and more effectively; new teams need ramp-up time |
| **Requirements Stability** | Unstable or unclear requirements cause rework and retesting — inflate estimates |
| **Tools & Environment** | Unstable environments or missing tools slow progress significantly |
| **Expected Quality & Risk** | High-risk apps (medical, financial) require deeper, broader testing |

---

## Estimation Techniques

---

### 1. Expert Judgment — Delphi Technique

A group of experienced individuals provide anonymous estimates independently. Estimates are compiled, shared, and revised over multiple rounds until a consensus is reached. Anonymity prevents bias from more senior voices dominating.

**How it works:**
```
Round 1: Each expert submits estimate independently (no discussion)
         ↓
         Compile + anonymize + share results with reasoning
         ↓
Round 2: Experts revise based on others' reasoning
         ↓
         Repeat until estimates converge
         ↓
Final:   Agreed estimate range
```

**Example — Estimating a recommendation engine feature:**

| Expert | Round 1 | Round 2 (after reviewing reasons) |
|---|---|---|
| Lead QA Engineer | 30 person-days | 35 person-days |
| Senior Automation Engineer | 45 person-days | 40 person-days |
| Product Owner | 25 person-days | 30 person-days |

Final agreed range: **35–40 person-days**

---

### 2. Three-Point Estimation (PERT)

Three estimates are defined for each task, then combined using a weighted average formula.

| Estimate | Description |
|---|---|
| **O — Optimistic** | Best-case scenario, everything goes smoothly |
| **M — Most Likely** | Realistic estimate under typical conditions |
| **P — Pessimistic** | Worst-case scenario with significant problems |

**Formula:**
```
E = (O + 4M + P) / 6
```

**Example — User Profile Management module:**

```
O = 5 days  (stable environment, data ready, no major bugs)
M = 8 days  (typical fluctuations, minor data setup, some bugs)
P = 15 days (env issues, complex data, critical bugs blocking progress)

E = (5 + 4×8 + 15) / 6
E = (5 + 32 + 15) / 6
E = 52 / 6
E = 8.67 days ≈ 8.7 days
```

**More examples:**

| Feature | O | M | P | E |
|---|---|---|---|---|
| Cloud document upload | 2 days | 4 days | 9 days | **(2+16+9)/6 = 4.5 days** |
| Report generation | 7 days | 10 days | 18 days | **(7+40+18)/6 = 10.8 days** |

---

### 3. Work Breakdown Structure (WBS)

Break the entire testing project into small, manageable tasks. Estimate each task individually. Sum them up for the total.

> Bottom-up approach — more detailed and typically more accurate than top-down methods.

**Example — Online Shopping Cart feature:**

| Task Category | Sub-Task | Estimated Hours |
|---|---|---|
| **Test Planning** | Understand requirements | 4 |
| | Create test strategy | 3 |
| | Review existing test cases | 2 |
| **Test Design** | Add items test cases | 8 |
| | Remove items test cases | 6 |
| | Quantity updates test cases | 5 |
| | Coupon application test cases | 7 |
| **Test Execution** | Execute initial pass | 15 |
| | Log and track defects | 10 |
| | Retest defect fixes | 8 |
| | Execute regression tests | 12 |
| **Test Reporting** | Prepare test summary report | 4 |
| **Total** | | **84 hours** |

---

### 4. Test Point Analysis (TPA)

A quantitative technique that assigns weighted **Test Points** to each testing task based on functional and non-functional complexity. Points are then multiplied by a team productivity rate to calculate effort.

**Formula:**
```
Estimated Effort = Total Test Points × Productivity Rate (hours/point)
```

**Example — User Search feature:**

| Function | Complexity | Points |
|---|---|---|
| Search by name + city with filters | Medium | 10 |
| Pagination and sorting | Complex | 15 |
| Basic performance testing | — | 3 |
| Usability testing | — | 2 |
| **Total** | | **30 points** |

```
Productivity rate: 2 person-hours per Test Point
Estimated Effort: 30 × 2 = 60 person-hours
```

**More examples:**

| Feature | Total Points | Productivity Rate | Estimated Effort |
|---|---|---|---|
| Product review submission | 41 points | 1.5 hrs/point | **61.5 person-hours** |
| Patient data export (healthcare) | 70 points | 2 hrs/point | **140 person-hours** |

---

## Case Study — WBS + Three-Point Estimation Combined

**Feature:** Course Progress Tracking on "EduBridge" online learning platform

**Requirements:** Display completion %, mark lessons complete, resume last watched lesson, backend API + UI integration.

**Estimation Factors:**
- Complexity: Medium (UI + API + database + video player integration)
- Team: Experienced with the platform, but new API endpoints need thorough testing
- Requirements: Fairly stable
- Quality: High — core to student experience

### WBS + PERT Table

| Sub-Task | O (hrs) | M (hrs) | P (hrs) | E = (O+4M+P)/6 |
|---|---|---|---|---|
| Analyze requirements | 4 | 6 | 8 | **6.00** |
| Create test strategy | 3 | 4 | 6 | **4.17** |
| UI test cases (dashboard, lessons) | 10 | 15 | 25 | **15.83** |
| API test cases (progress update, retrieve) | 8 | 12 | 18 | **12.33** |
| Video player integration test cases | 6 | 9 | 15 | **9.50** |
| Negative / edge case scenarios | 5 | 7 | 10 | **7.17** |
| Execute initial manual test pass | 12 | 18 | 28 | **18.67** |
| Log and track defects | 8 | 12 | 18 | **12.33** |
| Retest defect fixes | 10 | 15 | 25 | **15.83** |
| Basic regression testing | 6 | 9 | 14 | **9.33** |
| Prepare test summary report | 3 | 4 | 6 | **4.17** |
| **Total** | | | | **115.33 hours** |

### Converting to Calendar Days

```
115.33 hours ÷ 8 hours/day = 14.42 days
Add 15% buffer for unforeseen issues:
14.42 × 1.15 = 16.58 days

Final estimate: ~16–17 working days (1 dedicated QA engineer)
```

> If two engineers are assigned, calendar days roughly halve — but total person-hours remain the same.

---

## Exercises

### Exercise 1 — WBS + Three-Point Estimation
An e-commerce site is adding **Wishlist Functionality** (save products, view wishlist, move items to cart).

Create a WBS table with your own O, M, P estimates for each sub-task:
- Requirement analysis, test strategy, test case design (add/view/manage/move/edge cases), execution, defect logging, retesting, regression, reporting

Then:
1. Calculate Expected (E) for each sub-task using `(O + 4M + P) / 6`
2. Sum all Expected values for the total estimate in hours
3. Convert to working days (8 hrs/day) and add a 10% buffer

---

### Exercise 2 — Test Point Analysis
A mobile app is adding a **Dark Mode** feature across all screens.

**Given TPA values:**

| Category | Points |
|---|---|
| Simple screen (e.g., Splash) | 3 pts |
| Medium screen (e.g., Settings) | 6 pts |
| Complex screen (e.g., Main Dashboard) | 10 pts |
| Detailed readability/accessibility check | 5 pts |
| Minor performance check | 3 pts |

**App has:** 2 Complex screens, 5 Medium screens, 3 Simple screens
**Team productivity:** 1.8 person-hours per Test Point

Tasks:
1. Calculate total UI complexity points
2. Add readability + performance points (applied once each)
3. Calculate total Test Points
4. Calculate total effort in person-hours

---

## Key Takeaway

> Test estimation is not a one-time activity — it is iterative. Start with high-level expert judgment, refine with WBS and PERT as requirements solidify, and revisit whenever scope, risk, or resources change. The goal is not a perfect number; it is a defensible, transparent forecast.

---

## Quick Reference

```
4 Estimation Techniques:

1. Expert Judgment (Delphi)
   → Experienced team members estimate independently → converge through rounds

2. Three-Point Estimation (PERT)
   → E = (O + 4M + P) / 6
   → Accounts for best case, worst case, and most likely

3. Work Breakdown Structure (WBS)
   → Break testing into small tasks → estimate each → sum totals
   → Most detailed and accurate approach

4. Test Point Analysis (TPA)
   → Assign points by complexity → multiply by productivity rate
   → Effort = Total Test Points × Hours per Point

Always add a buffer (10–15%) for unforeseen issues.
```

---

*Module 5 — Test Planning and Strategy*
*Previous: introduction-to-test-plans.md | Next: test-scheduling-and-execution.md*
