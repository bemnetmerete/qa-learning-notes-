# Understanding Requirements and Specifications
> Source: QA Learn the Fundamentals — Lesson 5 | roadmap.sh
> Last updated: 2026

---

## Why This Matters for QA

Requirements and specifications are the foundation of all testing. Without understanding what software is *supposed to do*, you cannot write meaningful test cases or know when something has failed.

> If requirements are unclear, QA either tests the wrong things or misses critical scenarios entirely.

---

## Requirements vs. Specifications

These two terms are related but different:

| | Requirements | Specifications |
|---|---|---|
| **Level** | High-level | Detailed |
| **Perspective** | User's needs | Technical implementation |
| **Written by** | Product managers, stakeholders | Developers, architects, QA |
| **Question answered** | What should it do? | How exactly will it do it? |

### Example
- **Requirement:** "As a user, I want to be able to search for products."
- **Specification:** "The system shall provide a search box on every page. It shall support keyword, category, and price range filtering. Results shall display product image, name, price, and rating."

---

## Types of Requirements

### Functional Requirements
Describe **what** the system should do — specific features and behaviors.

**Examples for an e-commerce website:**
- The system shall allow users to search for products by keyword, category, and price range
- The system shall allow users to add products to a shopping cart
- The system shall calculate total cost including taxes and shipping
- The system shall send an email confirmation after an order is placed

### Non-Functional Requirements
Describe **how** the system should perform — quality attributes.

**Examples:**
- **Performance:** Pages load within 3 seconds under 100 concurrent users
- **Security:** All sensitive data encrypted using AES-256
- **Usability:** A first-time user completes a purchase within 5 minutes
- **Reliability:** System uptime of 99.9% per month
- **Scalability:** System handles 500 concurrent users without degradation

---

## Turning Vague Requirements Into Testable Specifications

This is one of the most important skills a QA engineer develops. Vague requirements cannot be tested — they must be transformed into **SMART specifications** (Specific, Measurable, Achievable, Relevant, Time-bound).

---

### Example 1 — "The system should be user-friendly"

This is untestable as written. Here is how to break it down:

| Vague Requirement | Testable Specification |
|---|---|
| User-friendly navigation | User reaches any page within 3 clicks from homepage |
| Easy to complete tasks | First-time user completes a purchase within 5 minutes |
| Clear error messages | Invalid inputs display specific, helpful error messages |
| Accessible | Website conforms to WCAG 2.1 Level AA guidelines |

---

### Example 2 — "The system should be secure"

| Vague Requirement | Testable Specification |
|---|---|
| Strong passwords | Minimum 12 characters, 1 uppercase, 1 lowercase, 1 number, 1 special character |
| Data protection | Credit card data encrypted in transit (HTTPS) and at rest (AES-256) |
| Regular scanning | Vulnerability scans run quarterly, issues fixed within 30 days |
| Access control | Only admins can access user management — other roles are blocked |

---

### Example 3 — "The system should perform well"

| Vague Requirement | Testable Specification |
|---|---|
| Fast pages | All pages load within 3 seconds under 100 concurrent users |
| Fast transactions | Add to cart and checkout complete within 2 seconds |
| Handles traffic | Supports 500 concurrent users without significant degradation |
| Efficient resources | CPU stays below 80% and memory below 90% under normal load |

---

## The Importance of Traceability

**Traceability** is the ability to link every requirement to its corresponding test cases. This ensures:

- Every requirement has been tested — nothing is missed
- Changes to requirements automatically flag which tests need updating
- Compliance can be demonstrated — "show me which test covers this requirement"
- Communication is clearer across the whole team

### Traceability Matrix Example

| Requirement ID | Requirement | Test Case ID | Status |
|---|---|---|---|
| REQ-001 | User can search by keyword | TC_001, TC_002 | ✅ Passed |
| REQ-002 | User can filter by price range | TC_003 | ✅ Passed |
| REQ-003 | Cart calculates total correctly | TC_010, TC_011 | ❌ Failed |
| REQ-004 | Email sent after order placed | TC_015 | ⏳ Not tested |

---

## How QA Uses Requirements

As a QA engineer, requirements are your starting point for everything:

1. **Read requirements** — understand what the feature should do
2. **Ask questions** — clarify anything vague or ambiguous before testing begins
3. **Identify test scenarios** — what situations need to be tested based on requirements?
4. **Write test cases** — turn each requirement into one or more specific test cases
5. **Define pass/fail criteria** — what does success look like for each requirement?
6. **Track coverage** — use a traceability matrix to ensure all requirements are tested

---

## Common Problems With Requirements (And What QA Does About It)

| Problem | Example | QA Response |
|---|---|---|
| Vague | "Should be fast" | Ask for specific performance metrics |
| Incomplete | Missing error handling scenarios | Raise a question in JIRA or the sprint planning |
| Contradictory | Two requirements conflict with each other | Flag to product manager immediately |
| Untestable | "The system should be good" | Work with team to define measurable criteria |
| Missing | Feature has no documented requirements | Don't test blind — request requirements first |

---

## Key Takeaway

> Good requirements = good test cases = good software.
>
> QA's job begins the moment requirements are written — not when code is complete. The earlier you review requirements, the cheaper and easier it is to fix problems.

---

*Previous topic: key-principles-of-qa.md*
*Next topic: testing-types.md*
