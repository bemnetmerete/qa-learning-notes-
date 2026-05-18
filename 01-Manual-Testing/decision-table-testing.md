# Decision Table Testing
> Source: QA Learn the Fundamentals — Module 2, Lesson 3 | roadmap.sh
> Last updated: 2026

---

## What is Decision Table Testing?

Decision Table Testing is a technique for testing systems where **multiple conditions combine to produce different outcomes**. Also called **cause-effect tables**, decision tables map every possible combination of inputs to its expected output.

> Use this technique when you have complex business rules where multiple things must be true or false simultaneously to determine what happens.

---

## The Four Components of a Decision Table

| Component | Description |
|---|---|
| **Condition Stubs** | The list of conditions that affect the outcome |
| **Action Stubs** | The list of possible actions/outcomes |
| **Condition Entries** | The values for each condition per rule (T/F, Y/N) |
| **Action Entries** | Which actions apply for each combination (marked with X) |

---

## Basic Structure

```
                    Rule 1   Rule 2   Rule 3   Rule 4
CONDITION STUBS
Condition 1           T        T        F        F
Condition 2           T        F        T        F

ACTION STUBS
Action 1              X
Action 2                       X        X
Action 3                                         X

T = True | F = False | X = This action applies
```

---

## How Many Rules?

For **n conditions**, there are **2ⁿ possible rules** (combinations):

| Conditions | Rules |
|---|---|
| 1 | 2 |
| 2 | 4 |
| 3 | 8 |
| 4 | 16 |

---

## Examples

### Example 1 — Online Shopping Discount

**Business Rule:** Apply 10% discount only if customer is a registered member AND order total is over $100.

**Conditions:**
- Registered member? (T/F)
- Order total > $100? (T/F)

**Decision Table:**

| | Rule 1 | Rule 2 | Rule 3 | Rule 4 |
|---|---|---|---|---|
| Registered Member | T | T | F | F |
| Order Total > $100 | T | F | T | F |
| **Apply 10% Discount** | **X** | | | |
| **No Discount** | | **X** | **X** | **X** |

**Reading the rules:**
- Rule 1: Member + over $100 → 10% discount ✅
- Rule 2: Member + under $100 → no discount
- Rule 3: Not member + over $100 → no discount
- Rule 4: Not member + under $100 → no discount

---

### Example 2 — Loan Approval System

**Conditions:**
- Credit score > 700?
- Income > $50,000?
- Debt-to-income ratio < 30%?

**Decision Table (8 rules for 3 conditions):**

| | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 |
|---|---|---|---|---|---|---|---|---|
| Credit Score > 700 | T | T | T | T | F | F | F | F |
| Income > $50,000 | T | T | F | F | T | T | F | F |
| Debt Ratio < 30% | T | F | T | F | T | F | T | F |
| **Approve Loan** | **X** | | | | | | | |
| **Reject Loan** | | | | **X** | | | | **X** |
| **Refer to Officer** | | **X** | **X** | | **X** | **X** | **X** | |

**Key rules:**
- Rule 1: All conditions true → Approve loan
- Rule 4: Low income + bad debt ratio (regardless of credit) → Reject
- Rule 8: All conditions false → Reject
- Everything else → Refer to loan officer for manual review

---

### Example 3 — ATM Withdrawal

**Conditions:**
- Valid ATM card?
- Sufficient balance?
- Within daily withdrawal limit?

**Decision Table:**

| | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 |
|---|---|---|---|---|---|---|---|---|
| Valid ATM Card | T | T | T | T | F | F | F | F |
| Sufficient Balance | T | T | F | F | T | T | F | F |
| Within Daily Limit | T | F | T | F | T | F | T | F |
| **Dispense Cash** | **X** | | | | | | | |
| **Insufficient Balance** | | | **X** | **X** | | | | |
| **Limit Exceeded** | | **X** | | | | **X** | | |
| **Eject Card (Invalid)** | | | | | **X** | **X** | **X** | **X** |

---

### Example 4 — E-commerce Shipping Cost

**Conditions:**
- Order total > $50?
- Premium member?
- Same state shipping?

**Decision Table:**

| | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 |
|---|---|---|---|---|---|---|---|---|
| Order Total > $50 | T | T | T | T | F | F | F | F |
| Premium Member | T | T | F | F | T | T | F | F |
| Same State | T | F | T | F | T | F | T | F |
| **Free Shipping** | **X** | **X** | **X** | **X** | | | | |
| **Standard ($5)** | | | | | **X** | **X** | **X** | |
| **Express ($10)** | | | | | | | | **X** |

---

## Step by Step — How to Create a Decision Table

```
Step 1: Identify all CONDITIONS that affect the outcome
Step 2: Identify all possible ACTIONS / outcomes
Step 3: Calculate number of rules = 2ⁿ (n = number of conditions)
Step 4: Fill in every combination of T and F for each condition
Step 5: For each combination, determine which action applies
Step 6: Mark actions with X
Step 7: (Optional) Simplify — merge rules with identical actions
```

---

## Advantages

- **Systematic** — ensures every possible condition combination is considered
- **Complete coverage** — no scenario is accidentally missed
- **Reduces redundancy** — duplicate scenarios become obvious
- **Clear communication** — easy for developers, testers, and business analysts to read together

## Limitations

- **Combinatorial explosion** — 4 conditions = 16 rules, 5 conditions = 32 rules
- **Not for UI testing** — best suited for logic and business rules, not visual elements
- **Can get complex** — large tables become hard to manage

---

## When to Use Decision Table Testing

Use it when you see:
- "If X AND Y then do Z"
- "When A is true but B is false, then..."
- Complex discount, pricing, or approval rules
- Permission and access control logic
- Any feature where multiple conditions combine

---

## Quick Memory Aid

```
Decision Table = A truth table for business rules

Columns = Rules (each combination of T/F)
Rows    = Conditions + Actions
X       = "This action applies for this rule"

2 conditions = 4 rules
3 conditions = 8 rules
4 conditions = 16 rules
```

---

*Previous topic: boundary-value-analysis.md*
*Next topic: writing-effective-test-cases.md*
