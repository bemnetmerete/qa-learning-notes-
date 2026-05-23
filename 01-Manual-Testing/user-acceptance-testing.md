# User Acceptance Testing (UAT) — The Customer Perspective
> Source: QA Learn the Fundamentals — Module 3, Lesson 4 | roadmap.sh
> Last updated: 2026

---

## What is UAT?

User Acceptance Testing (UAT) is the **final phase of testing** before software is released to production. Unlike other testing phases run by QA engineers, UAT involves **real end-users** performing tasks they would normally do in their daily work.

> UAT = validating the entire solution from the user's perspective — not just finding bugs, but confirming the system is usable, understandable, and fit for purpose.

---

## Key Objectives of UAT

| Objective | Description |
|---|---|
| **Validation of Business Requirements** | Confirm the software meets functional specs from the user's viewpoint |
| **Usability Testing** | Verify the software is easy to use, understand, and navigate |
| **Real-World Scenario Testing** | Test under real conditions using real data |
| **End-to-End Testing** | Validate the entire workflow across all integrated components |
| **Confidence Building** | Give stakeholders assurance the software is ready for release |

---

## UAT vs. Other Testing Types

| Testing Type | Focus | Performed By | Goal |
|---|---|---|---|
| **Unit Testing** | Individual components | Developers | Verify each unit of code works as expected |
| **Integration Testing** | Interaction between components | Testers / Developers | Ensure different parts work together |
| **System Testing** | Entire system as a whole | QA Engineers | Validate system meets specified requirements |
| **UAT** | System from the user's perspective | End-Users / Customers | Confirm system meets business needs and is release-ready |

---

## The UAT Process — Step by Step

```
Step 1 — PLANNING         Define scope, objectives, and criteria. Identify testers and environment.
Step 2 — TEST CASE DEV    Write test cases from user stories, business requirements, real scenarios.
Step 3 — ENV SETUP        Configure test environment to closely mirror production.
Step 4 — TEST EXECUTION   End-users run test cases and record results.
Step 5 — DEFECT REPORTING Report bugs with steps to reproduce, expected vs. actual results.
Step 6 — DEFECT RESOLUTION Dev team investigates and fixes reported issues.
Step 7 — RETESTING        End-users verify fixes and check for regressions.
Step 8 — SIGN-OFF         Formal approval from end-users that software is ready to release.
```

---

## Developing Effective UAT Test Cases

Each test case should include:

| Field | Description |
|---|---|
| **Test Case ID** | Unique identifier |
| **Description** | Brief summary of what is being tested |
| **Steps** | Detailed list of actions to perform |
| **Expected Result** | The anticipated outcome |
| **Actual Result** | What actually happened |
| **Status** | Passed / Failed / Blocked |

### Example — E-Commerce Website

**Scenario: Placing an order as a guest user**
1. Browse the website and add items to the cart
2. Proceed to checkout
3. Enter shipping and billing information
4. Select a payment method and complete the payment
5. Verify the order is placed and a confirmation email is received

**Scenario: Canceling an order**
1. Log in with valid credentials
2. Navigate to order history
3. Select an order to cancel and confirm
4. Verify the order is canceled and a confirmation email is received

**Scenario: Returning an item**
1. Log in with valid credentials
2. Navigate to order history and select an order
3. Initiate the return process and ship the item back
4. Verify the return is processed and a refund is issued

---

## Best Practices for UAT

- **Involve end-users early** — Gather feedback before assumptions solidify
- **Use real-world data** — Simulate actual usage conditions
- **Provide adequate training** — Users should know how to execute test cases
- **Establish clear communication channels** — Between users, devs, and stakeholders
- **Document everything** — Test plan, cases, results, and defects
- **Prioritize defects** — By severity and business impact
- **Track progress** — Report regularly to stakeholders

---

## Roles and Responsibilities

| Role | Responsibility |
|---|---|
| **UAT Testers (End-Users)** | Execute test cases, report defects, provide usability feedback |
| **UAT Lead** | Plans, coordinates, and manages the entire UAT process |
| **Business Analyst** | Provides domain expertise; defines business requirements and scenarios |
| **Project Manager** | Ensures UAT is completed on time and within budget |
| **Developers** | Resolve reported defects and support end-users |
| **QA Engineers** | Provide guidance and ensure testing follows defined standards |

---

## Entry and Exit Criteria

### Entry Criteria (UAT can begin when...)
- System testing is complete and the software is stable
- Test environment is set up and mirrors production
- Necessary test data is available
- UAT test plan is approved by stakeholders
- End-users are trained and ready

### Exit Criteria (UAT is complete when...)
- All planned test cases have been executed
- All critical and high-priority defects are resolved
- End-users have provided formal sign-off
- UAT report is completed and distributed

---

## Tools Used in UAT

| Category | Tools |
|---|---|
| **Test Management** | TestRail, Zephyr, Xray |
| **Defect Tracking** | Jira, Bugzilla, Azure DevOps |
| **Screen Recording** | Camtasia, OBS Studio |
| **Feedback / Surveys** | SurveyMonkey, Google Forms |
| **Collaboration** | Microsoft Teams, Slack |

---

## Real-World Examples

### Online Banking Platform
A bank runs UAT with representative customers before launch. Users test:
- Checking account balances
- Transferring funds
- Paying bills
- Viewing transaction history

UAT reveals: confusing navigation, unclear error messages, browser incompatibilities, slow load times — all fixed before go-live.

### Hospital EHR System
Doctors, nurses, and admin staff test a new Electronic Health Record system:
- Creating patient records
- Ordering tests and prescribing medications
- Scheduling appointments

UAT uncovers: difficult UI, missing data fields, integration issues, security vulnerabilities — resolved before deployment.

### Project Management Startup
A startup enlists real project managers to test their product before public release:
- Creating projects and assigning tasks
- Tracking progress and generating reports
- Collaborating with team members

UAT feedback reveals: no customization options, poor tool integrations, unintuitive interface — all addressed before launch.

---

## Key Takeaway

> UAT is the last line of defense before release. It shifts the perspective from *"does the code work?"* to *"does this actually serve the user?"* — and that distinction is what determines whether software succeeds in the real world.

---

## Quick Reference

```
UAT Process:
PLAN → TEST CASES → ENV SETUP → EXECUTE → REPORT → RESOLVE → RETEST → SIGN-OFF

Entry Criteria:              Exit Criteria:
✔ System testing done        ✔ All test cases executed
✔ Env mirrors production     ✔ Critical defects resolved
✔ Test data ready            ✔ User sign-off received
✔ Test plan approved         ✔ UAT report completed
✔ Users trained
```

---

*Module 3 — Testing Types*
*Previous: integration-testing.md | Next: regression-testing.md*
