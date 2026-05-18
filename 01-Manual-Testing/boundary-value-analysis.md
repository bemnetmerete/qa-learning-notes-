# Boundary Value Analysis (BVA)
> Source: QA Learn the Fundamentals — Module 2, Lesson 2 | roadmap.sh
> Last updated: 2026

---

## What is Boundary Value Analysis?

Boundary Value Analysis (BVA) is a test case design technique that focuses on testing the **edges** of input ranges rather than the middle.

> Bugs love boundaries. Most input errors occur at the minimum, maximum, and values just outside those limits — not somewhere in the middle.

BVA complements Equivalence Partitioning — EP tells you which groups to test, BVA tells you exactly which values at the edges of those groups to focus on.

---

## Core Concepts

| Term | Definition |
|---|---|
| **Input Domain** | All possible input values for a field |
| **Boundary** | The minimum and maximum values of the valid range |
| **Boundary Values** | Values at, just above, and just below the boundary |

---

## The Six Boundary Values Formula

For any range with a minimum and maximum, always test these 6 values:

```
Min - 1   ← just below minimum  (should FAIL)
Min       ← exact minimum       (should PASS)
Min + 1   ← just above minimum  (should PASS)

Max - 1   ← just below maximum  (should PASS)
Max       ← exact maximum       (should PASS)
Max + 1   ← just above maximum  (should FAIL)
```

---

## Examples

### Example 1 — Age Field (accepts 18–65)

```
Boundary values: 17, 18, 19, 64, 65, 66
```

| Test Case ID | Input (Age) | Expected Result |
|---|---|---|
| TC_Age_001 | 17 | ❌ Error — "Age must be between 18 and 65" |
| TC_Age_002 | 18 | ✅ Valid input |
| TC_Age_003 | 19 | ✅ Valid input |
| TC_Age_004 | 64 | ✅ Valid input |
| TC_Age_005 | 65 | ✅ Valid input |
| TC_Age_006 | 66 | ❌ Error — "Age must be between 18 and 65" |

---

### Example 2 — Password Length (8–12 characters)

```
Boundary values: 7, 8, 9, 11, 12, 13
```

| Test Case ID | Input Length | Expected Result |
|---|---|---|
| TC_Pass_001 | 7 chars | ❌ Rejected |
| TC_Pass_002 | 8 chars | ✅ Accepted |
| TC_Pass_003 | 9 chars | ✅ Accepted |
| TC_Pass_004 | 11 chars | ✅ Accepted |
| TC_Pass_005 | 12 chars | ✅ Accepted |
| TC_Pass_006 | 13 chars | ❌ Rejected |

---

### Example 3 — Bank Transfer Amount ($1–$1000)

```
Boundary values: 0, 1, 2, 999, 1000, 1001
```

| Test Case ID | Transfer Amount | Expected Result |
|---|---|---|
| TC_Bank_001 | $0 | ❌ Error — below minimum |
| TC_Bank_002 | $1 | ✅ Valid transfer |
| TC_Bank_003 | $2 | ✅ Valid transfer |
| TC_Bank_004 | $999 | ✅ Valid transfer |
| TC_Bank_005 | $1000 | ✅ Valid transfer |
| TC_Bank_006 | $1001 | ❌ Error — above maximum |

---

### Example 4 — E-commerce Free Shipping (orders over $50, max $5000)

```
Boundary values: -0.01, 0, 0.01, 49.99, 50.00, 50.01, 4999.99, 5000.00, 5000.01
```

| Test Case ID | Order Value | Expected Result |
|---|---|---|
| TC_Shop_001 | -$0.01 | ❌ Invalid order value |
| TC_Shop_002 | $0.00 | ✅ Valid — no free shipping |
| TC_Shop_003 | $49.99 | ✅ Valid — no free shipping |
| TC_Shop_004 | $50.00 | ✅ Valid — free shipping applied |
| TC_Shop_005 | $50.01 | ✅ Valid — free shipping applied |
| TC_Shop_006 | $5000.00 | ✅ Valid — free shipping applied |
| TC_Shop_007 | $5000.01 | ❌ Invalid order value |

---

### Example 5 — Library Books (borrow 0–5 books max)

```
Boundary values: -1, 0, 1, 4, 5, 6
```

| Test Case ID | Books Borrowed | Expected Result |
|---|---|---|
| TC_Lib_001 | -1 | ❌ Invalid number |
| TC_Lib_002 | 0 | ✅ Valid — no books borrowed |
| TC_Lib_003 | 1 | ✅ Valid |
| TC_Lib_004 | 4 | ✅ Valid |
| TC_Lib_005 | 5 | ✅ Valid — maximum reached |
| TC_Lib_006 | 6 | ❌ Error — maximum is 5 |

---

## Multiple Input Variables

When testing fields that depend on each other, apply BVA to each variable independently while keeping the other at a safe nominal value.

### Example — Shipping Cost (Weight: 1–10 lbs, Distance: 10–100 miles)

**Test weight boundaries (hold distance at 50 miles):**

| Test Case ID | Weight (lbs) | Distance (miles) | Expected Result |
|---|---|---|---|
| TC_Ship_001 | 0 | 50 | ❌ Weight invalid |
| TC_Ship_002 | 1 | 50 | ✅ Valid |
| TC_Ship_003 | 2 | 50 | ✅ Valid |
| TC_Ship_004 | 9 | 50 | ✅ Valid |
| TC_Ship_005 | 10 | 50 | ✅ Valid |
| TC_Ship_006 | 11 | 50 | ❌ Weight invalid |

**Test distance boundaries (hold weight at 5 lbs):**

| Test Case ID | Weight (lbs) | Distance (miles) | Expected Result |
|---|---|---|---|
| TC_Ship_007 | 5 | 9 | ❌ Distance invalid |
| TC_Ship_008 | 5 | 10 | ✅ Valid |
| TC_Ship_009 | 5 | 11 | ✅ Valid |
| TC_Ship_010 | 5 | 99 | ✅ Valid |
| TC_Ship_011 | 5 | 100 | ✅ Valid |
| TC_Ship_012 | 5 | 101 | ❌ Distance invalid |

---

## Advantages

- **Finds boundary bugs** — most common source of input errors
- **Easy to apply** — straightforward once you know the valid range
- **Reduces test cases** — 6 values cover the full boundary risk instead of hundreds
- **Works with EP** — together they form a complete test strategy

## Limitations

- **Doesn't test input combinations** — use Decision Table Testing for that
- **Best for numeric inputs** — less effective for booleans or complex data types
- **Assumes variable independence** — if fields depend on each other, test interactions separately

---

## BVA + EP Together — The Complete Picture

```
Step 1 — Use Equivalence Partitioning to identify your partitions:
         Invalid Low | Valid Range | Invalid High

Step 2 — Use Boundary Value Analysis to pick your test values:
         Min-1, Min, Min+1 ... Max-1, Max, Max+1

Together they cover every meaningful input scenario efficiently.
```

---

## Quick Memory Aid

```
"Test the edges, not the middle."

For any range [Min, Max]:
✅ Min - 1  →  should fail
✅ Min      →  should pass
✅ Min + 1  →  should pass
✅ Max - 1  →  should pass
✅ Max      →  should pass
✅ Max + 1  →  should fail
```

---

*Previous topic: equivalence-partitioning.md*
*Next topic: decision-table-testing.md*
