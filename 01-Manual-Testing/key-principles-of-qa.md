# Key Principles of Quality Assurance
> Source: QA Learn the Fundamentals — Lesson 3 | roadmap.sh
> Last updated: 2026

---

## Overview

QA is built on 7 core principles. These are not abstract theories — they are practical guidelines that shape every decision a QA professional makes daily.

---

## The 7 Key Principles

---

### 1. Prevention Over Detection

**The idea:** Stop defects from happening rather than finding them after the fact.

**Why it matters:** Fixing a bug found in requirements costs 10x less than fixing it after release.

**In practice:**
- Review design documents before coding begins
- Participate in code reviews with developers
- Use static analysis tools to catch issues early
- Encourage developers to write unit tests

**Example:** A QA engineer reviews a new feature's design document and notices the password reset flow doesn't account for expired tokens — caught before a single line of code was written.

**Counterexample:** A team that only tests after development finds 40 bugs the week before release — all requiring expensive, rushed fixes.

---

### 2. Whole Team Responsibility

**The idea:** Quality is everyone's job — not just the QA team's.

**Why it matters:** If developers think "QA will catch my bugs," they write sloppier code.

**In practice:**
- Developers write unit tests for their own code
- Designers create clear, testable UI specifications
- Product managers write clear, unambiguous requirements
- Everyone participates in quality conversations

**Example:** A developer who writes clean, well-documented code is contributing to quality just as much as a QA tester running test cases.

**Counterexample:** A developer who pushes untested code thinking "that's QA's problem" introduces avoidable bugs that slow the entire team.

---

### 3. Early Testing

**The idea:** Start testing as early as possible in the development cycle.

**Why it matters:** The later a bug is found, the more expensive it is to fix.

**Cost of fixing bugs by phase:**
| Phase Found | Relative Cost |
|---|---|
| Requirements | 1x |
| Design | 5x |
| Development | 10x |
| Testing | 20x |
| Production | 100x |

**In practice:**
- Review requirements for testability from day one
- Write test cases before development is complete
- Use continuous integration to run automated tests on every code change
- Apply Test-Driven Development (TDD) where possible

**Counterexample:** A team that only tests in the final week before release discovers critical bugs that delay the launch by a month.

---

### 4. Testing is Context Dependent

**The idea:** There is no one-size-fits-all approach to testing. Every project is different.

**Why it matters:** Applying the wrong testing approach wastes resources or misses critical risks.

**Factors that determine your approach:**
- Project size and complexity
- Risk level
- Available budget and time
- Team skills and tools
- Regulatory requirements

**Examples:**
- A simple landing page → basic functional testing is enough
- A fintech payment system → needs functional + security + performance + compliance testing
- A medical device → needs exhaustive testing with full documentation for regulatory approval

**In practice:** Always write a **test plan** that tailors your approach to the specific project context before you start testing.

---

### 5. The Pesticide Paradox

**The idea:** If you run the same tests over and over, they eventually stop finding new bugs.

**Why it matters:** A stale test suite gives a false sense of security — bugs hide in untested areas.

**The analogy:** Just like crop pests build resistance to the same pesticide, software bugs "resist" tests that never evolve.

**In practice:**
- Regularly add new test cases as features change
- Use exploratory testing to find bugs outside scripted test cases
- Rotate which areas you focus on each sprint
- Review and retire outdated test cases that no longer add value

**Counterexample:** A team runs the same 50 automated regression tests for 6 months and finds no bugs — then a critical bug hits production because a new feature was never added to the test suite.

---

### 6. Absence of Errors is a Fallacy

**The idea:** A bug-free product is not automatically a good product.

**Why it matters:** Software can pass all tests and still fail users if it doesn't meet their needs.

**The real goal:** Deliver a product that users actually want and can use — not just one that technically works.

**In practice:**
- Include usability testing — real users testing the software
- Validate against business requirements, not just technical specs
- Involve actual users in testing where possible
- Ask "does this solve the user's problem?" not just "does this pass the test?"

**Example:** A perfectly bug-free e-commerce checkout process that takes 12 steps will still lose customers to a competitor with a 3-step checkout.

---

### 7. Risk-Based Testing

**The idea:** Not everything needs to be tested equally. Focus your effort where it matters most.

**Why it matters:** Time and resources are always limited — spend them where bugs would cause the most damage.

**How to prioritize:**
1. Identify the most critical features (what would break if this failed?)
2. Identify historically buggy areas of the codebase
3. Identify areas with recent significant changes
4. Identify features used by the most users

**Example risk levels:**

| Feature | Risk Level | Testing Priority |
|---|---|---|
| Payment processing | Critical | Test exhaustively |
| User login | High | Test thoroughly |
| Product search | Medium | Test standard cases |
| Footer links | Low | Basic check only |

**In practice:** Document your risk assessment in your test plan and use it to decide how much testing each area gets.

---

## Summary — All 7 Principles at a Glance

| # | Principle | One-line Summary |
|---|---|---|
| 1 | Prevention Over Detection | Stop bugs before they happen |
| 2 | Whole Team Responsibility | Quality belongs to everyone |
| 3 | Early Testing | Find bugs when they are cheapest to fix |
| 4 | Context Dependent | Tailor your approach to each project |
| 5 | Pesticide Paradox | Evolve your tests or they stop working |
| 6 | Absence of Errors is a Fallacy | Bug-free ≠ good product |
| 7 | Risk-Based Testing | Test the most important things most |

---

## Real-World Application — Tesla Autopilot

Tesla's Autopilot system is a perfect real-world example of all 7 principles applied together:

- **Prevention:** Simulation testing before any real-world deployment
- **Whole Team:** Software, hardware, and safety engineers all own quality
- **Early Testing:** Hardware-in-the-loop testing during development
- **Context Dependent:** Lane keeping tests differ from emergency braking tests
- **Pesticide Paradox:** Continuously adds new driving scenarios to test suite
- **Absence of Errors Fallacy:** Monitors real-world performance even after release
- **Risk-Based:** Emergency braking and collision avoidance are tested most rigorously

---

*Previous topic: introduction-to-qa.md*
*Next topic: sdlc-and-stlc.md*
