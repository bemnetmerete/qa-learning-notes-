# Testing in Scrum: Sprints and Daily Stand-ups

> **Course:** QA: Learn the Fundamentals | **Module 7 – Agile & DevOps** | **Lesson 2 of 35**

---

## Overview

Scrum provides a structured, iterative approach to managing software projects within the Agile framework. QA is integrated throughout the entire Scrum lifecycle — not added at the end. This lesson covers how QA operates within Sprints and Daily Stand-ups.

---

## Sprints: The Heartbeat of Scrum

A **Sprint** is a short, time-boxed period (typically 2–4 weeks) during which the Scrum team works to complete a defined set of work. Sprints shift QA from a traditional waterfall "test at the end" approach to continuous, iterative testing throughout the cycle.

```
┌─────────────────────────────────────────────────────────────────┐
│                        SPRINT LIFECYCLE                         │
├──────────────┬───────────────┬──────────────┬───────────────────┤
│    Sprint    │  During the   │    Sprint    │     Sprint        │
│   Planning   │    Sprint     │    Review    │  Retrospective    │
├──────────────┼───────────────┼──────────────┼───────────────────┤
│ QA reviews   │ QA tests as   │ QA demos     │ QA reflects on    │
│ user stories │ features are  │ completed    │ process and       │
│ & acceptance │ developed;    │ features to  │ suggests          │
│ criteria     │ runs CI tests │ stakeholders │ improvements      │
└──────────────┴───────────────┴──────────────┴───────────────────┘
```

---

## QA in Each Sprint Phase

### 1. Sprint Planning

QA actively participates to understand the Sprint Goal, user stories, and acceptance criteria — not just listen passively.

**QA contributions:**
- Identify potential testing challenges before development begins
- Estimate testing effort for the sprint
- Ensure user stories are clearly defined and testable

**✅ Good Example:** For a "guest checkout" feature, QA asks:
- "What payment methods will be supported?"
- "What error messages should appear for invalid input?"

**❌ Counterexample:** QA passively attends without asking questions — leading to misunderstandings and delays during testing.

---

### 2. During the Sprint

QA tests features as they are developed — not after the sprint ends.

**QA activities:**
- Unit testing of individual components as they are completed
- Integration testing as components are connected
- System testing of end-to-end user flows
- Exploratory testing for unexpected edge cases
- Running automated CI tests continuously on every commit

**✅ Good Example:** As developers complete guest checkout components, QA runs unit and integration tests immediately, and performs exploratory testing to find unexpected edge cases.

**❌ Counterexample:** QA waits until the sprint ends to begin testing — creating a bottleneck, delaying the sprint, and making bugs more expensive to fix.

---

### 3. Sprint Review

QA participates in demonstrating completed features to stakeholders and gathering feedback.

**QA contributions:**
- Demonstrates the tested functionality clearly
- Shows error handling and edge case behavior
- Answers questions about quality, coverage, and known issues

**✅ Good Example:** QA demos the guest checkout feature to the product owner, highlighting successful flows, error handling, and any known limitations. Stakeholders provide feedback on usability.

**❌ Counterexample:** QA doesn't attend — stakeholders have no quality context and cannot provide informed feedback.

---

### 4. Sprint Retrospective

QA reflects on the sprint and contributes to continuous process improvement.

**QA contributions:**
- Shares testing challenges encountered during the sprint
- Proposes improvements (e.g., better communication with devs, more automation)
- Helps the team avoid repeating the same issues

**✅ Good Example:** QA suggests automating a time-consuming manual test from this sprint to free up capacity in the next one.

**❌ Counterexample:** QA doesn't participate — missing the opportunity to improve the testing process for future sprints.

---

## QA Activities Within a Sprint

### Test Case Creation and Execution

Based on user stories and acceptance criteria, QA creates and runs test cases throughout the sprint.

**Example (guest checkout):**
- Verify a user can complete a purchase as a guest
- Verify all required fields are validated
- Verify correct error messages appear for invalid input

---

### Test Automation

Automated tests provide continuous regression feedback on every code commit.

**Example:** Automated tests verify that items can be added to the cart, shipping info can be entered, and orders can be submitted. These run automatically on every commit.

---

### Exploratory Testing

QA goes beyond scripted test cases to discover unexpected issues through open-ended investigation.

**Example:** QA explores the guest checkout feature by trying unusual input combinations, simulating stress conditions, and investigating potential security issues like cross-site scripting.

---

### Bug Reporting and Tracking

Bugs are logged in a tracking system (Jira, Bugzilla) with full context for developers.

**A complete bug report includes:**
- Clear description of the bug
- Step-by-step reproduction steps
- Expected vs. actual result
- Environment and build version

**Example:** QA finds that guest checkout incorrectly calculates sales tax. They create a Jira ticket with reproduction steps, expected tax amount, and actual result. The ticket is tracked until fixed and verified.

---

## Daily Stand-ups: Transparency and Collaboration

The **Daily Stand-up** (Daily Scrum) is a 15-minute time-boxed meeting where the team synchronizes activities and identifies blockers. It is a collaborative event — not a status report to management.

### The Three Questions

| Question | QA Example |
|---|---|
| **What did I do yesterday?** | "I completed testing the user registration form and found two bugs related to password validation." |
| **What will I do today?** | "I'll test the payment gateway integration and create automated tests for the checkout process." |
| **Any impediments?** | "I'm blocked from testing the API integration because the staging environment is currently down." |

---

### Benefits of QA Participation in Stand-ups

| Benefit | Impact |
|---|---|
| **Improved Communication** | Everyone stays aligned on testing progress and risks |
| **Increased Transparency** | Team can track testing status and spot roadblocks early |
| **Early Bug Detection** | Critical bugs are surfaced quickly before they compound |
| **Better Collaboration** | Developers know what QA needs; QA knows what developers are building |

---

## Stand-up Example: Online Banking App

> **QA Engineer says:**
> "Yesterday, I finished testing the fund transfer functionality and found a bug where transfers exceeding $10,000 are not flagged for review. Today, I'll be working on the bill payment feature. I'm currently blocked — I need the latest build with the fund transfer fix."

**What this communicates to the team:**
- ✅ Fund transfer testing is complete
- 🐛 Critical bug identified (regulatory concern)
- 🚧 QA is blocked — developer needs to prioritize the fix

The team can immediately act: the developer prioritizes the fix, and the Scrum Master helps remove obstacles.

---

## Quick Reference: QA in Scrum

```
SPRINT PLANNING        → Review stories, clarify acceptance criteria, estimate effort
DURING SPRINT          → Test continuously as features are built; run CI/automated tests
SPRINT REVIEW          → Demo tested features; gather stakeholder feedback
SPRINT RETROSPECTIVE   → Reflect on what worked; propose process improvements
DAILY STAND-UP         → Share progress, plans, and blockers in 15 minutes
```

---

## Summary

- Sprints are 2–4 week cycles; QA participates actively in all four sprint phases — not just during testing
- Testing starts early (Sprint Planning) and continues throughout; waiting until the end creates bottlenecks and late-stage bugs
- Daily Stand-ups keep the team aligned on testing progress, blockers, and quality risks
- Exploratory testing, automation, and thorough bug reporting are all sprint-level QA responsibilities

---

## Next Lesson

➡️ [Lesson 3 – Continuous Integration and Continuous Delivery (CI/CD)](./continuous-integration-and-continuous-delivery.md)

## Previous Lesson

⬅️ [Lesson 1 – Agile Development Principles and QA's Role](./agile-development-principles-and-qas-role.md)
