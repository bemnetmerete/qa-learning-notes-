# The Bug Lifecycle — From Discovery to Resolution
> Source: QA Learn the Fundamentals — Module 4, Lesson 4 | roadmap.sh
> Last updated: 2026

---

## What is the Bug Lifecycle?

The bug lifecycle is the **structured sequence of states a bug passes through** from the moment it is discovered until it is fully resolved and closed. It provides a clear framework for managing defects, ensuring accountability, and facilitating communication between testers and developers.

> Bug lifecycle = the complete journey of a bug, from "found" to "fixed and verified."

---

## Core Bug States

| State | Description | Who Acts |
|---|---|---|
| **New / Open** | Bug has been reported but no action taken yet | QA Tester |
| **Assigned** | Bug reviewed and assigned to a developer | QA Lead / Project Manager |
| **In Progress** | Developer is actively investigating and fixing the bug | Developer |
| **Resolved / Fixed** | Developer has applied a fix and it's ready for QA retest | Developer |
| **To Be Verified** | Fix is deployed to QA environment, awaiting verification | QA Tester |
| **Closed** | QA verified the fix — bug is gone | QA Tester |
| **Reopened** | Fix failed or introduced a new issue — back to development | QA Tester |

---

## Additional States

| State | When It Applies |
|---|---|
| **Deferred / Postponed** | Bug acknowledged but scheduled for a later release due to time or priority constraints |
| **Rejected / Not a Bug** | Reported behavior is intentional, cannot be reproduced, or is not a defect |
| **Duplicate** | Identical to an already-logged bug — linked to the original and closed |

---

## The Bug Lifecycle — Visual Flow

```
                    ┌─────────────────────────────────────────────┐
                    │                                             │
[Tester] NEW ──► ASSIGNED ──► IN PROGRESS ──► RESOLVED ──► TO BE VERIFIED ──► CLOSED
                                   ▲                                  │
                                   │                                  │ (fix failed)
                                   └──────── REOPENED ◄───────────────┘

Alternative paths from NEW:
  NEW ──► REJECTED     (not a bug / cannot reproduce)
  NEW ──► DUPLICATE    (same as existing bug)
  NEW ──► DEFERRED     (postponed to future release)
```

---

## State-by-State Breakdown

---

### 1. New / Open
Bug has been submitted. No action taken yet by the development team.

**Real-world example:**
A user can't log in to an online banking app after changing their password. QA verifies the issue and logs it as "New" with full steps, expected/actual results, and screenshots.

**Hypothetical example:**
During system testing, a QA engineer finds that the "Add New Item" button is unresponsive. They create a detailed report, attach console logs, and set status to "New."

---

### 2. Assigned
Bug reviewed and handed to the appropriate developer based on severity, priority, and code ownership.

**Real-world example:**
The login bug is reviewed. Given its Critical severity and High priority, it is immediately assigned to Sarah, the senior backend developer responsible for authentication.

**Hypothetical example:**
The "Add New Item" button bug is assigned to David (frontend developer) since the issue appears UI-related.

---

### 3. In Progress
Developer is actively debugging and implementing a fix.

**Real-world example:**
Sarah investigates and finds a misconfiguration in the password hashing algorithm that triggers specifically after a password change. She begins writing a patch.

**Hypothetical example:**
David identifies a JavaScript error preventing the button's event listener from firing. He begins fixing the script.

---

### 4. Resolved / Fixed
Developer believes the fix is complete. Status updated with comments explaining what was changed and which build contains the fix.

**Real-world example:**
Sarah tests her fix locally, updates the status to "Resolved," and adds a comment: *"Fixed in build v2.3.1_hotfix."*

**Hypothetical example:**
David confirms the button works on his local machine and marks the bug "Resolved," noting it's in the dev-branch for the next QA build.

---

### 5. To Be Verified / Ready for Test
Fix is deployed to the QA environment. Clear handover from development back to QA.

**Real-world example:**
The v2.3.1_hotfix build is deployed to QA. The bug transitions to "To Be Verified" — either automatically or manually.

**Hypothetical example:**
David's changes are merged and a new inventory system build is deployed to QA. The button bug is now "To Be Verified."

---

### 6. Closed
QA verified the fix — bug is confirmed resolved and archived.

**Real-world example:**
QA tests the login fix across multiple scenarios in v2.3.1_hotfix. Everything works. Bug is marked "Closed."

---

### 7. Reopened
Fix failed verification or introduced a new regression. QA documents exactly what went wrong and sends it back to the developer.

**Real-world example:**
QA tests the login fix. The original issue is resolved, but users can no longer change their password at all. QA reopens the bug with a new screenshot documenting the regression.

**Hypothetical example:**
The "Add New Item" button now clicks, but sometimes adds two items instead of one. Bug reopened with the partial fix noted and new behavior described.

---

## Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| **QA Tester** | Logs New bugs, verifies To Be Verified bugs, marks Closed or Reopened |
| **Developer** | Takes Assigned bugs, moves to In Progress, then Resolved. Can also Reject or mark Duplicate |
| **Team Lead / PM / Product Owner** | Reviews New bugs, assigns them, decides on Deferred or Rejected based on project priorities |

---

## Practical Walkthroughs

---

### Scenario 1 — Critical Payment Gateway Bug (Happy Path)

**App:** FashionForward e-commerce website

```
1. NEW         QA tester finds payment gateway fails on credit card checkout.
               Logs bug: "Critical: Payment Gateway Fails on Credit Card Transaction."
               Attaches screenshots and logs.

2. ASSIGNED    QA Lead assigns to Alex (senior backend, payment integrations).

3. IN PROGRESS Alex investigates. Finds a recent API change from the payment provider
               was not accounted for in the integration. Begins writing the fix.

4. RESOLVED    Alex completes and locally tests the fix.
               Comment: "Updated API calls to match provider's v3.1 spec. Fixed in build 1.5.0."

5. TO BE       Build 1.5.0 deployed to QA environment.
   VERIFIED

6. CLOSED      QA retests multiple payment transactions with different card types.
               All pass. Bug closed.
```

---

### Scenario 2 — Minor UI Typo Bug (Unhappy Path with Reopen)

**App:** Internal customer support dashboard

```
1. NEW         QA finds typo: "Custumer Details" instead of "Customer Details."
               Logged as Minor severity, Low priority.

2. DEFERRED    Product Owner defers to next sprint — current sprint focused on
               critical data integrity features.

3. ASSIGNED    Next sprint: bug assigned to Maria (frontend developer).

4. IN PROGRESS Maria fixes the "Custumer Details" typo. Tests locally.

5. RESOLVED    Fix noted in build 2.1.0.

6. TO BE       Build 2.1.0 deployed to QA.
   VERIFIED

7. REOPENED    QA finds the original typo is fixed, but a new one was introduced:
               "Acccount Summary" instead of "Account Summary."
               Bug reopened with screenshot of new typo.

8. IN PROGRESS Maria reviews the screenshot and fixes the second typo.

9. RESOLVED    Fix noted in build 2.1.1.

10. TO BE      Build 2.1.1 deployed to QA.
    VERIFIED

11. CLOSED     QA verifies both typos are corrected. Bug closed.
```

---

## Exercises

### Exercise 1 — Critical Security Bug
A penetration test reveals a vulnerability in a financial app's authentication module that allows bypassing multi-factor authentication.
1. Trace the likely states from discovery to resolution (assuming smooth process)
2. Who is responsible for each transition?
3. What action triggers each state change?

### Exercise 2 — Non-Standard Paths
Bug: "The shopping cart icon disappears when adding more than 10 items."
1. Give two plausible reasons this bug might be **Rejected**
2. If marked **Duplicate**, what information would accompany that status?
3. If **Resolved** then **Reopened**, describe a likely reason and the next steps

### Exercise 3 — Role-Play the Lifecycle
**Your role:** QA Tester
**The bug:** A user's profile picture doesn't display correctly after uploading a new one.
1. Write a brief summary with expected/actual result
2. Trace the lifecycle from New to Closed (fix works on first attempt)
3. Identify who acts at each transition
4. Now imagine: on verification, the picture displays but is heavily distorted. What happens next?

---

## Key Takeaway

> The bug lifecycle is not always linear. A bug can be deferred, rejected, reopened, or closed — and each state shift has a responsible party and a clear trigger. Understanding this flow makes you a more effective QA engineer and a better collaborator with your development team.

---

## Quick Reference

```
Core States:
NEW → ASSIGNED → IN PROGRESS → RESOLVED → TO BE VERIFIED → CLOSED
                                                    │
                                                REOPENED (if fix fails)
                                                    │
                                             → IN PROGRESS again

Alternative exits from NEW:
  → REJECTED   (not a bug)
  → DUPLICATE  (already logged)
  → DEFERRED   (postponed)

Who does what:
  QA Tester    → NEW, TO BE VERIFIED, CLOSED, REOPENED
  Developer    → IN PROGRESS, RESOLVED, REJECTED, DUPLICATE
  Lead / PM    → ASSIGNED, DEFERRED, REJECTED
```

---

*Module 4 — Bug Reporting and Tracking*
*Previous: bug-tracking-systems.md | Next: effective-communication-with-developers.md*
