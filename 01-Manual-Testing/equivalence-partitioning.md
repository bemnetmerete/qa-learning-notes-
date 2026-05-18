# Equivalence Partitioning
> Source: QA Learn the Fundamentals — Module 2, Lesson 1 | roadmap.sh
> Last updated: 2026

---

## What is Equivalence Partitioning?

Equivalence Partitioning (EP) is a **black-box test case design technique** that divides all possible input values into groups called **equivalence classes** or **partitions**.

The core idea is simple:

> If one value in a partition works correctly, all other values in that partition will also work correctly. If one fails, all others in that partition will likely fail too.

This means you only need to test **one value per partition** — dramatically reducing the number of test cases while still achieving good coverage.

---

## Valid vs Invalid Partitions

Every input field has at least two types of partitions:

| Partition Type | Description | Purpose |
|---|---|---|
| **Valid Partition** | Values the system should accept | Verify correct behavior |
| **Invalid Partition** | Values the system should reject | Verify error handling |

---

## How to Identify Equivalence Partitions

Ask these questions about every input field:

1. **What is the input domain?** — What data type, format, or range is expected?
2. **What values are valid?** — What should the system accept?
3. **What values are invalid?** — What should the system reject?

---

## Examples

### Example 1 — Age Input Field (accepts 18–65)

```
Valid Partition:    18 ≤ age ≤ 65     → test with: 35
Invalid Partition 1: age < 18         → test with: 10
Invalid Partition 2: age > 65         → test with: 70
```

**Test Case Table:**

| Test Case ID | Input | Expected Result | Partition |
|---|---|---|---|
| TC_001 | 35 | Accepted | Valid |
| TC_002 | 17 | Rejected — "Age must be 18 or older" | Invalid |
| TC_003 | 66 | Rejected — "Age must be 65 or younger" | Invalid |

---

### Example 2 — Password Field

Requirements: 8–16 characters, must have uppercase, lowercase, digit, special character.

```
Valid Partition:      Meets ALL criteria          → test with: "Test@123"
Invalid Partition 1:  Less than 8 characters      → test with: "Te@1"
Invalid Partition 2:  More than 16 characters     → test with: "TestPassword@12345"
Invalid Partition 3:  No uppercase letter         → test with: "test@1234"
Invalid Partition 4:  No lowercase letter         → test with: "TEST@1234"
Invalid Partition 5:  No digit                    → test with: "Test@abcd"
Invalid Partition 6:  No special character        → test with: "TestPass1"
```

---

### Example 3 — Discount Code

Rules: "SAVE10" = 10% discount, "SAVE20" = 20% discount, anything else = invalid.

| Test Case ID | Input | Expected Result | Partition |
|---|---|---|---|
| TC_001 | SAVE10 | 10% discount applied | Valid |
| TC_002 | SAVE20 | 20% discount applied | Valid |
| TC_003 | INVALID | Error message shown | Invalid |

---

### Example 4 — File Upload (max 5MB)

```
Valid Partition:   File size ≤ 5MB   → test with: 3MB file
Invalid Partition: File size > 5MB   → test with: 6MB file
```

---

## Step by Step Process

```
1. Read the requirements for the input field
2. Identify the valid range or accepted values
3. Define valid partition(s)
4. Define invalid partition(s) — think about what's too small, too large,
   wrong format, empty, special characters, etc.
5. Select ONE representative value from each partition
6. Write a test case for each representative value
```

---

## Advantages

- **Reduces test cases** significantly without losing coverage
- **Improves coverage** by ensuring all input categories are tested
- **Easy to apply** — accessible for testers at all experience levels
- **Finds defects early** — before the software reaches production

## Limitations

- **Doesn't test combinations** — if two fields interact, use Decision Table Testing instead
- **Requires clear requirements** — vague specs lead to poorly defined partitions
- **Assumes uniform treatment** — if the system treats values in a partition differently, bugs may be missed

---

## Quick Memory Aid

```
Think of equivalence partitioning like sorting people into queues:
- Under 18 queue     → all treated the same (invalid)
- 18 to 65 queue     → all treated the same (valid)
- Over 65 queue      → all treated the same (invalid)

You only need to test ONE person from each queue.
You don't need to test every single age.
```

---

## Combined with Boundary Value Analysis

EP tells you **which partitions** to test.
BVA tells you **which specific values** within those partitions to focus on.

Always use both together for maximum coverage.

| Technique | Focus | Use When |
|---|---|---|
| Equivalence Partitioning | Groups of inputs | Reducing test cases |
| Boundary Value Analysis | Edges of partitions | Catching boundary bugs |

---

*Previous topic: requirements-and-specifications.md*
*Next topic: boundary-value-analysis.md*
