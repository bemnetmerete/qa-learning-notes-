# Continuous Integration and Continuous Delivery (CI/CD)

> **Course:** QA: Learn the Fundamentals | **Module 7 – Agile & DevOps** | **Lesson 3 of 35**

---

## Overview

CI/CD streamlines the software development lifecycle by ensuring code changes are frequently integrated, automatically tested, and kept ready for deployment. It directly enables the Agile principles of iterative development and continuous feedback.

---

## Continuous Integration (CI)

**Continuous Integration** is the practice of developers frequently merging code changes into a central shared repository — ideally multiple times per day. Each merge triggers an automated build and test run to detect integration errors early.

### Core Principles of CI

| Principle | Description |
|---|---|
| **Frequent Commits** | Developers commit small changes multiple times per day, reducing merge complexity |
| **Automated Builds** | Every commit triggers a build — compiles code, links libraries, packages the application |
| **Automated Testing** | Unit, integration, and basic system tests run automatically after each build |
| **Immediate Feedback** | If build or tests fail, the team is notified immediately to fix issues while fresh |
| **Single Source Repository** | All code, build scripts, and test scripts live in one version-controlled repo (e.g., Git) |

---

### CI Workflow

```
Developer commits code
        │
        ▼
CI Server detects new commit (Jenkins / GitLab CI / GitHub Actions)
        │
        ▼
Pull latest code → Compile → Build
        │
        ▼
Run automated tests (Unit → Integration → Smoke)
        │
        ├── PASS ──→ Build artifact stored ──→ Team notified ✅
        │
        └── FAIL ──→ Developer notified immediately 🚨
                            │
                            ▼
                   Fix issue → Commit again → Restart CI
```

---

### CI in Practice: E-Commerce Example

1. Developer commits "add to cart" feature code to the main Git branch
2. CI server (e.g., GitHub Actions) detects the commit
3. Server compiles backend and builds frontend assets
4. Automated unit tests run for backend logic; integration tests verify cart interacts correctly with product catalog and user session
5. If all tests pass → build artifact is stored; team gets a success notification
6. If any test fails → developer is notified immediately and fixes before more code is built on top

---

## Continuous Delivery (CD)

**Continuous Delivery** extends CI by automatically deploying successfully built and tested code to staging/pre-production environments. The software is always in a deployable state; the final push to production remains a **manual decision**.

### Key Aspects of CD

| Aspect | Description |
|---|---|
| **Auto-Deploy to Staging** | Passed builds are automatically deployed to an environment mirroring production |
| **Further Automated Testing** | End-to-end, system, and performance tests run in staging |
| **Manual Exploratory Testing** | QA performs targeted manual testing on staging before release |
| **UAT** | Product owners or business stakeholders validate the release candidate |
| **Always Deployable** | At any point, the team can confidently push the "deploy to production" button |

---

### CD Workflow

```
CI Pipeline passes ✅
        │
        ▼
CD Pipeline: Auto-deploy to Staging
        │
        ▼
Automated end-to-end tests run in staging
        │
        ▼
QA performs manual exploratory testing
Product Owner conducts UAT
        │
        ▼
All checks pass → Application is READY FOR PRODUCTION
        │
        ▼
Team manually triggers production deployment (automated process)
```

---

### CD in Practice: Financial Institution Example

A bank deploys a new "simplified fund transfers" feature:
1. CI verifies the code changes with automated tests
2. CD pipeline auto-deploys to a UAT environment
3. Dedicated QA team + compliance officers run security scans and regulatory compliance checks
4. Only after all checks pass is the app scheduled for production
5. The production deployment itself is also automated — removing human error from the release process

---

## CI vs CD — Quick Comparison

| Aspect | Continuous Integration (CI) | Continuous Delivery (CD) |
|---|---|---|
| **Focus** | Code integration and automated testing | Deployment readiness and staging validation |
| **Trigger** | Every code commit | Successful CI build |
| **Testing** | Unit, integration, smoke tests | End-to-end, performance, UAT |
| **Environment** | CI server / build environment | Staging / pre-production |
| **Production deploy** | Not involved | Manual trigger after all checks pass |
| **Goal** | Catch integration bugs early | Keep software always deployable |

---

## The Role of QA in CI/CD

QA shifts from being a **gatekeeper at the end** to an **embedded quality enabler throughout the pipeline**.

| QA Responsibility | Description |
|---|---|
| **Early Test Strategy** | QA defines which tests run at each pipeline stage from the very start |
| **Writing Automated Tests** | QA designs and maintains unit, integration, and E2E tests that run in CI/CD |
| **Monitoring Pipeline Health** | QA watches build/test results, analyzes failures, and distinguishes code bugs from test issues |
| **Manual Exploratory Testing** | QA tests deployed staging builds for usability and complex workflows automation might miss |
| **Risk Assessment** | QA evaluates whether automated test coverage is sufficient before a release |
| **Continuous Feedback** | QA informs developers and product owners about quality status at every pipeline stage |

---

## CI/CD Stage Classification

| Step | CI or CD? |
|---|---|
| Developer pushes code to Git | CI begins |
| Server compiles app and runs unit tests | CI |
| App deployed to QA/staging environment | CD begins |
| Automated end-to-end tests run in staging | CD |
| QA engineers perform manual testing in staging | CD |
| Product owner approves release | CD (gate) |
| App deployed to production (automated process) | CD |

---

## Summary

- **CI** integrates code frequently, verifying each change with automated builds and tests to catch issues early
- **CD** extends CI by automatically deploying validated builds to staging, keeping software always ready for production
- The key difference: CI focuses on integration correctness; CD focuses on deployment readiness
- QA is critical at every stage — designing tests, monitoring pipelines, performing exploratory testing in staging, and assessing release readiness

---

## Next Lesson

➡️ [Lesson 4 – Collaboration and Communication in Agile Teams](./collaboration-and-communication-in-agile-teams.md)

## Previous Lesson

⬅️ [Lesson 2 – Testing in Scrum: Sprints and Daily Stand-ups](./testing-in-scrum-sprints-and-daily-standups.md)
