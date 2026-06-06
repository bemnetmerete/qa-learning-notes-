# Introduction to Test Plans — Scope, Objectives, and Resources
> Source: QA Learn the Fundamentals — Module 5, Lesson 1 | roadmap.sh
> Last updated: 2026

---

## What is a Test Plan?

A test plan is a document that **formalizes the strategy, approach, and logistics for testing a software product**. It is the primary communication tool between QA engineers, developers, project managers, and stakeholders — ensuring everyone agrees on what is being tested, how it will be verified, and what a successful result looks like.

> Test plan = the contract that defines what gets tested, why, and with what resources.

---

## The Three Pillars of a Test Plan

```
         ┌─────────────┐
         │  TEST PLAN  │
         └──────┬──────┘
                │
    ┌───────────┼───────────┐
    │           │           │
 SCOPE     OBJECTIVES   RESOURCES
(What?)     (Why?)      (With what?)
```

---

## Pillar 1 — Scope: In-Scope vs. Out-of-Scope

The scope defines the **boundaries of the testing effort**. Without a clear scope, teams fall into "scope creep" — wasting resources on non-critical features or missing core functionality entirely.

| | Description | Example (Banking App) |
|---|---|---|
| **In-Scope** | Modules, features, or user journeys explicitly included for testing | User Login, Fund Transfers, Account Balance View |
| **Out-of-Scope** | What will NOT be tested in this cycle — just as important to state | Third-party payment gateway, Legacy Module X |

> Defining out-of-scope items protects the team. If someone asks "Why wasn't the legacy login page tested?", you can point directly to the test plan.

---

## Pillar 2 — Test Objectives

Objectives define the **goals of the testing effort and the criteria for success**. An objective is not just "find bugs" — it is a measurable outcome tied to software quality.

| Type | Description | Example |
|---|---|---|
| **Quantitative** | Measurable metrics | "Achieve 90% test case execution" / "Reduce high-severity defect density to below 2%" |
| **Qualitative** | User experience and behavior goals | "Verify UI consistency across mobile and desktop" / "Ensure checkout completes within 3 seconds under normal load" |

Setting objectives at the start aligns the entire team on what success looks like. If the objective is to prioritize critical bug detection over UI aesthetics, the team knows to focus exploratory testing on high-risk functional flows first.

---

## Pillar 3 — Resources

Resources are the **raw requirements needed to execute the plan**. Miscalculating resources is the most common cause of project delays.

### Human Resources
- Define who is doing what
- Specify the number of QA engineers, their expertise level, and availability
- Identify if manual testers, automation engineers, or developer support is needed

### Test Environments
- Specify the hardware (devices, servers), operating systems, and browsers required
- Define the environment status — is it a mirror of production? Shared or dedicated?
- An unstable environment makes testing unreliable — always define this upfront

### Testing Tools

| Category | Examples |
|---|---|
| **Bug Tracking** | Jira, Bugzilla, Azure DevOps |
| **Test Management** | TestRail, Zephyr, Xray |
| **Automation Frameworks** | Selenium, Playwright, Cypress |
| **Performance Testing** | JMeter, k6 |

---

## The Constraint Triangle

The three pillars are interconnected. Changing one affects the others.

```
              SCOPE
              /    \
             /      \
      RESOURCES ── OBJECTIVES

If SCOPE increases → add RESOURCES or lower OBJECTIVES (accept higher risk)
If RESOURCES decrease → reduce SCOPE or adjust OBJECTIVES
If OBJECTIVES are raised → increase RESOURCES or narrow SCOPE
```

### Risks of Underspecification

| Component | Risk if Underspecified |
|---|---|
| **Scope** | Scope creep — team loses focus and misses core features |
| **Objectives** | Misaligned expectations — stakeholders expect perfection when team focused on critical bugs only |
| **Resources** | Bottlenecks — tests can't run due to missing accounts, data, or hardware |

---

## Test Plan as a Living Document

A test plan is not written once and forgotten. As the project moves from planning into execution, you will constantly refer back to these three pillars to ensure the plan stays grounded in the project's real constraints.

> A well-crafted test plan moves QA from reactive "firefighting" to a proactive, managed approach to quality.

---

## Key Takeaway

> Test planning is the foundation of a predictable QA process. Define **what to test (Scope)**, **why you are testing it (Objectives)**, and **what you need to do it (Resources)** — and you give the entire team the visibility needed to coordinate effectively and manage expectations.

---

## Quick Reference

```
Test Plan = Scope + Objectives + Resources

Scope:
  ✔ In-Scope  → explicitly list what WILL be tested
  ✔ Out-of-Scope → explicitly list what will NOT be tested

Objectives:
  ✔ Quantitative → measurable metrics (% coverage, defect density)
  ✔ Qualitative  → UX and behavior goals (speed, consistency)

Resources:
  ✔ People      → who, what role, how available
  ✔ Environment → hardware, OS, browser, production mirror or not
  ✔ Tools       → bug tracking, test management, automation frameworks

Constraint Triangle:
  Scope ↑ → Resources ↑ or Objectives ↓
```

---

*Module 5 — Test Planning and Strategy*
*Next: test-estimation-and-scheduling.md*
