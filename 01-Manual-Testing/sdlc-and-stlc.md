# SDLC and QA's Role
> Source: QA Learn the Fundamentals — Lesson 2 | roadmap.sh
> Last updated: 2026

---

## What is the SDLC?

The **Software Development Life Cycle (SDLC)** is a structured framework that outlines every stage involved in building and maintaining software. It helps teams deliver software on time, within budget, and at the required quality level.

> Think of SDLC as the master blueprint for how software gets built from idea to live product.

---

## Common SDLC Models

### 1. Waterfall Model
Linear and sequential — each phase must finish before the next begins.

```
Requirements → Design → Development → Testing → Deployment → Maintenance
```

- **Best for:** Small projects with fixed, well-defined requirements
- **Weakness:** Inflexible — changes mid-project are expensive
- **QA role:** Concentrated in the Testing phase, but also reviews requirements and design

---

### 2. Iterative Model
Software is built in small cycles called **iterations**. Each iteration delivers a working piece of the product.

```
Plan → Design → Build → Test → Evaluate → (repeat)
```

- **Best for:** Projects where requirements may evolve
- **Strength:** Early feedback, flexible to change
- **QA role:** Integrated into every iteration — tests each cycle's output

**Example:** Building a mobile banking app — first iteration delivers account balance view, second adds transfers, third adds bill pay.

---

### 3. Spiral Model
Combines Waterfall and Iterative, with strong emphasis on **risk analysis** at every cycle.

```
Plan → Risk Analysis → Build & Test → Evaluate → (spiral outward)
```

- **Best for:** Large, complex, high-risk projects (e.g., medical device software)
- **Strength:** Risk mitigation is built into every phase
- **QA role:** Participates in risk assessment and plans testing to mitigate identified risks

---

### 4. Agile Model
The most widely used modern approach. Iterative, collaborative, and customer-focused. Work is done in short cycles called **sprints** (usually 2 weeks).

**Key principles:**
- Customer satisfaction through frequent delivery
- Embrace changing requirements
- Measure progress by working software
- Close developer-stakeholder collaboration
- Continuous improvement

**Common Agile frameworks:**
- **Scrum** — sprints, daily standups, sprint reviews, retrospectives
- **Kanban** — visual workflow boards, continuous delivery

- **Best for:** Most modern software projects
- **QA role:** Fully embedded in the team — tests during sprints, attends standups, participates in reviews

---

### 5. V-Model
Each development phase has a **directly corresponding testing phase**. Testing is planned from day one.

```
Requirements Analysis  ←→  Acceptance Testing
System Design          ←→  System Testing
Architectural Design   ←→  Integration Testing
Module Design          ←→  Unit Testing
         [Coding at the base of the V]
```

- **Best for:** Projects requiring strict quality standards
- **Strength:** Testing is never an afterthought — it mirrors development
- **QA role:** Plans each testing phase alongside its corresponding development phase

---

## SDLC Model Comparison

| Model | Flexibility | Risk Handling | QA Integration | Best For |
|---|---|---|---|---|
| Waterfall | Low | Low | End phase | Fixed scope projects |
| Iterative | Medium | Medium | Each cycle | Evolving requirements |
| Spiral | Medium | High | Every cycle | High-risk projects |
| Agile | High | Medium | Continuous | Most modern projects |
| V-Model | Low | Medium | Parallel phases | Quality-critical projects |

---

## QA's Role in Each SDLC Phase

Regardless of which model is used, QA contributes to every phase:

| SDLC Phase | QA Activity |
|---|---|
| **Requirements Gathering** | Review requirements for clarity, completeness, and testability |
| **Design** | Review architecture for potential quality issues |
| **Development** | Monitor coding standards, review code, write early tests |
| **Testing** | Execute test cases, report bugs, verify fixes |
| **Deployment** | Verify software deploys correctly and works in production |
| **Maintenance** | Test bug fixes and updates, monitor for regressions |

> **Key insight:** QA is not just the "testing phase" — it is involved from the very first conversation about what to build.

---

## Real-World Example — Agile QA in Action

**Scenario:** Adding a "Schedule Ride" feature to a ride-sharing app using Scrum.

**QA Activities per Sprint:**

1. **Sprint Planning** — QA asks clarifying questions about requirements
   - *"What is the maximum time in advance a ride can be scheduled?"*
   - *"How are cancellations handled?"*

2. **Test Case Design** — QA writes test cases covering:
   - Scheduling for tomorrow
   - Scheduling a week in advance
   - Canceling a scheduled ride
   - Modifying a scheduled ride
   - Scheduling during peak hours

3. **Test Execution** — QA runs manual and automated tests as developers build the feature

4. **Defect Reporting** — QA logs bugs in JIRA with full reproduction steps

5. **Regression Testing** — After fixes, QA re-tests to ensure nothing else broke

6. **Sprint Review** — QA demonstrates the feature to stakeholders and collects feedback

---

## Choosing the Right SDLC Model

Ask these questions:

| Question | Answer → Model |
|---|---|
| Are requirements fixed and clear? | Waterfall or V-Model |
| Will requirements change? | Agile or Iterative |
| Is the project high-risk? | Spiral |
| Does the project need frequent delivery? | Agile |
| Is strict testing documentation required? | V-Model |

---

## Key Takeaway

> The SDLC defines *when* and *how* QA does its work. Understanding the model your team uses tells you exactly where to plug in your testing activities for maximum impact.

---

*Previous topic: What is QA and Why is it Important*
*Next topic: testing-types.md*
