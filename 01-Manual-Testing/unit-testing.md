# Unit Testing — Concepts and Benefits
> Source: QA Learn the Fundamentals — Module 3, Lesson 1 | roadmap.sh
> Last updated: 2026

---

## What is Unit Testing?

Unit testing is the practice of testing **individual, isolated pieces of code** — called units — to verify they work correctly on their own.

A "unit" is typically a single function, method, or class. Unit testing is the **first and lowest level** of testing in the testing pyramid, done by developers during or immediately after writing code.

> Unit testing = testing the smallest possible piece of code in complete isolation from everything else.

---

## Where Unit Testing Fits in the Testing Pyramid

```
        /\
       /  \
      / E2E\          ← System / End-to-End Testing (slowest, fewest)
     /------\
    /Integrat\        ← Integration Testing
   /----------\
  /    Unit    \      ← Unit Testing (fastest, most tests)
 /--------------\
```

Unit tests form the **wide base** of the pyramid — there should be more unit tests than any other type because they are fast, cheap, and catch bugs earliest.

---

## Core Concepts

---

### 1. Unit Isolation

A unit test must test **one thing only** — completely isolated from databases, files, APIs, or other modules.

**Why isolation matters:**
- If a test depends on a database and the database goes down, the test fails — but the bug isn't in your code
- Isolation ensures a failing test means the code itself is broken — not some external dependency

**How to isolate:**
- Use **mocks** — fake objects that simulate dependencies
- Use **stubs** — simplified replacements that return controlled responses

**Example:**
```
Function: calculateShippingCost(location, weight)
Problem:  Function queries a database for shipping rates
Solution: Mock the database call to return a fixed rate
Result:   Test only verifies the calculation logic — nothing else
```

---

### 2. Test-Driven Development (TDD)

TDD is a development approach where you **write the test before writing the code**.

**The TDD Cycle — Red, Green, Refactor:**

```
Step 1 — RED:     Write a test that fails (code doesn't exist yet)
Step 2 — GREEN:   Write the minimum code to make the test pass
Step 3 — REFACTOR: Clean up the code while keeping the test passing
Step 4 — REPEAT:  Move to the next unit of functionality
```

**Simple TDD Example — add() function:**

```javascript
// Step 1: Write failing test first
test_add_two_numbers() {
    assert add(2, 3) == 5   // FAILS — function doesn't exist yet
}

// Step 2: Write minimum code to pass
function add(a, b) {
    return a + b;
}

// Step 3: Test now passes ✅ — refactor if needed
```

**Benefits of TDD:**
- Forces you to think about requirements before coding
- Ensures every piece of code has a test from day one
- Results in cleaner, more modular code design

---

### 3. Assertions

Assertions are the **heart of every unit test** — they verify that actual output matches expected output.

| Assertion | What it checks |
|---|---|
| `assertEquals(expected, actual)` | Two values are equal |
| `assertTrue(condition)` | A condition is true |
| `assertFalse(condition)` | A condition is false |
| `assertNull(object)` | An object is null |
| `assertNotNull(object)` | An object is not null |
| `assertThrows(exceptionType, code)` | A specific exception is thrown |

**Example — Rectangle Area Function:**
```javascript
function calculateRectangleArea(length, width) {
    return length * width;
}

test_calculateRectangleArea() {
    assertEquals(10, calculateRectangleArea(2, 5));   // 2 × 5 = 10 ✅
    assertEquals(25, calculateRectangleArea(5, 5));   // 5 × 5 = 25 ✅
    assertEquals(0,  calculateRectangleArea(0, 10));  // 0 × 10 = 0  ✅
}
```

If any assertion fails — the entire test is marked as FAILED.

---

### 4. The FIRST Principles

Good unit tests follow the FIRST principles:

| Letter | Principle | Meaning |
|---|---|---|
| **F** | Fast | Tests run in milliseconds — run them constantly |
| **I** | Isolated | No dependencies on databases, files, or other tests |
| **R** | Repeatable | Same result every time, on any machine |
| **S** | Self-Verifying | Automatically pass or fail — no manual checking |
| **T** | Timely | Written early — ideally before the code (TDD) |

---

## Benefits of Unit Testing

---

### 1. Early Bug Detection
Catching a bug during unit testing costs a fraction of catching it in production.

```
Cost of fixing a bug:
Unit testing phase:       1x
Integration testing:      5x
System testing:           10x
Production (live users):  100x
```

---

### 2. Improved Code Design
If a function is hard to unit test, it is usually poorly designed. Writing unit tests forces better, more modular code.

**Signal:** If you need to mock 10 dependencies to test one function — that function does too much and needs to be split up.

---

### 3. Safe Refactoring
Unit tests act as a safety net. Change the implementation of a function freely — if all tests still pass, nothing broke.

Without tests → changing code is risky and stressful.
With tests → changing code is safe and confident.

---

### 4. Living Documentation
Unit tests show exactly how a function is meant to be used — what inputs it accepts, what it returns, and what edge cases it handles. Better than comments that go stale.

---

### 5. Faster Debugging
When a bug is reported, run the unit tests for the affected area first. If a test fails — you immediately know which unit is broken. No guesswork.

---

## Practical Examples

---

### Example 1 — Email Validation

```javascript
function isValidEmail(email) {
    return email.includes('@') && email.includes('.');
}

test_isValidEmail() {
    assertTrue(isValidEmail("test@example.com"));   // ✅ Valid
    assertFalse(isValidEmail("testexample.com"));   // ❌ Missing @
    assertFalse(isValidEmail("test@example"));      // ❌ Missing .com
    assertFalse(isValidEmail("@example.com"));      // ❌ Missing username
    assertFalse(isValidEmail("test@.com"));         // ❌ Missing domain
}
```

---

### Example 2 — Discount Calculator

```javascript
function calculateDiscount(price, loyaltyLevel) {
    if (loyaltyLevel === "Gold")   return price * 0.2;  // 20% off
    if (loyaltyLevel === "Silver") return price * 0.1;  // 10% off
    return 0;                                            // No discount
}

test_calculateDiscount() {
    assertEquals(20, calculateDiscount(100, "Gold"));    // ✅ 20% of 100
    assertEquals(10, calculateDiscount(100, "Silver"));  // ✅ 10% of 100
    assertEquals(0,  calculateDiscount(100, "Bronze"));  // ✅ No discount
    assertEquals(0,  calculateDiscount(100, ""));        // ✅ Empty level
    assertEquals(0,  calculateDiscount(100, null));      // ✅ Null level
}
```

---

### Example 3 — String Reversal

```javascript
function reverseString(str) {
    return str.split("").reverse().join("");
}

test_reverseString() {
    assertEquals("olleh",       reverseString("hello"));        // ✅ Simple word
    assertEquals("dlrow olleh", reverseString("hello world"));  // ✅ With spaces
    assertEquals("",            reverseString(""));             // ✅ Empty string
    assertEquals("a",           reverseString("a"));            // ✅ Single char
    assertEquals("madam",       reverseString("madam"));        // ✅ Palindrome
}
```

---

## Unit Testing vs Other Testing Types

| | Unit Testing | Integration Testing | System Testing |
|---|---|---|---|
| **What is tested** | Single function/method | Multiple components together | Entire application |
| **Who writes it** | Developers | Developers + QA | QA Engineers |
| **Speed** | Very fast | Medium | Slow |
| **Isolation** | Complete | Partial | None |
| **When** | During development | After units are built | Before release |
| **Cost to fix bugs** | Lowest | Medium | Highest |

---

## Key Takeaway

> Unit testing is the developer's responsibility — but as a QA engineer you need to understand it deeply because:
> - You review unit test coverage as part of your quality assessment
> - You write automated tests using the same assertion concepts
> - Understanding unit tests helps you focus your manual testing on areas not covered by unit tests

---

## Quick Memory Aid

```
FIRST principles:
F — Fast          (runs in milliseconds)
I — Isolated      (no external dependencies)
R — Repeatable    (same result every time)
S — Self-Verifying (pass/fail automatically)
T — Timely        (written early — before or with the code)

TDD cycle:
RED → GREEN → REFACTOR → REPEAT
```

---

*Module 3 — Testing Types*
*Next topic: integration-testing.md*
