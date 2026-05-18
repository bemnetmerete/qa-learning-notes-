# Writing Effective Test Cases — Structure and Components
> Source: QA Learn the Fundamentals — Module 2, Lesson 4 | roadmap.sh
> Last updated: 2026

---

## Why Test Cases Matter

A well-written test case is a precise, repeatable instruction set that any tester can follow and get the same result. A poorly written test case leads to inconsistent testing, missed bugs, and confusion.

> A test case is only useful if someone other than the person who wrote it can follow it perfectly and get the exact same result every time.

---

## The 10 Core Components of a Test Case

---

### 1. Test Case ID
A unique identifier for every test case.

- **Format:** `TC_[Module]_[Feature]_[Number]`
- **Examples:** `TC_LOGIN_001`, `TC_CART_005`, `TC_CHECKOUT_012`
- **Why:** Allows easy tracking, referencing in bug reports, and sorting in JIRA

---

### 2. Test Case Name / Title
A short, clear description of exactly what is being tested.

- **Examples:**
  - ✅ "Verify successful login with valid credentials"
  - ✅ "Verify error message when password is incorrect"
  - ❌ "Login test" — too vague
- **Rule:** Keep it specific and action-oriented

---

### 3. Test Objective / Purpose
One sentence stating the goal of this test case.

- **Example:** "To verify that a registered user can log in with correct credentials and is redirected to the homepage."
- **Why:** Clarifies intent and ensures the test aligns with the requirement being tested

---

### 4. Pre-Conditions
Everything that must be true BEFORE the test can run.

- **Examples:**
  - User account exists with username `valid_user` and password `ValidPass123`
  - Browser is open and pointed to the login page
  - Shopping cart is empty
- **Why:** If preconditions aren't met the test result is meaningless
- **Rule:** Be specific — list every single required condition

---

### 5. Test Steps
Numbered, step-by-step actions the tester must perform.

- **Rules:**
  - Each step = one single action
  - Use clear, simple language
  - Number every step
  - Never combine two actions into one step

- **Good example:**
  ```
  1. Open Chrome browser
  2. Navigate to www.example.com/login
  3. Enter "valid_user" in the Username field
  4. Enter "ValidPass123" in the Password field
  5. Click the "Login" button
  ```
- **Bad example:**
  ```
  1. Go to the site and log in with valid credentials
  ```

---

### 6. Test Data
The exact input values used in the test.

| Field | Value |
|---|---|
| Username | valid_user |
| Password | ValidPass123 |
| Product ID | ABC123 |

- **Why:** Without specific data, two testers may use different values and get different results
- **Rule:** Use realistic data — cover valid, invalid, and boundary values across your test suite

---

### 7. Expected Result
The exact outcome that should happen if the software is working correctly.

- **Examples:**
  - ✅ "User is redirected to homepage at www.example.com/home and their name appears in the top right corner"
  - ❌ "Login works" — too vague, not measurable
- **Rule:** Be precise and specific — this is the pass/fail criterion

---

### 8. Actual Result
What actually happened when the tester ran the test. Filled in during execution.

- **Examples:**
  - ✅ "User was redirected to homepage. Name displayed correctly."
  - ❌ "User saw error: 'Invalid credentials' despite entering correct details."
- **Rule:** Record exactly what happened — never guess or assume

---

### 9. Pass / Fail Status
The final verdict based on comparing expected vs actual result.

| Status | Meaning |
|---|---|
| ✅ Pass | Actual result matches expected result exactly |
| ❌ Fail | Actual result does not match expected result |
| ⏸️ Blocked | Test cannot run — precondition not met or environment issue |
| ⏭️ Skipped | Test deliberately not run this cycle |

---

### 10. Post-Conditions
The state the system should be in AFTER the test completes.

- **Examples:**
  - "Log out the user account"
  - "Remove test item from shopping cart"
  - "Delete test user account created during test"
- **Why:** Prevents one test from interfering with the next test

---

## Complete Test Case Example

**Scenario:** Testing login on an e-commerce website.

---

**Test Case ID:** `TC_LOGIN_001`

**Test Case Name:** Verify successful login with valid credentials

**Test Objective:** To verify that a registered user can log in with correct credentials and is redirected to the homepage.

**Pre-Conditions:**
- User account exists: username `valid_user`, password `ValidPass123`
- Browser is open
- User is on the login page: `www.example.com/login`

**Test Steps:**
1. Open Chrome browser
2. Navigate to `www.example.com/login`
3. Enter `valid_user` in the Username field
4. Enter `ValidPass123` in the Password field
5. Click the "Login" button

**Test Data:**
| Field | Value |
|---|---|
| Username | valid_user |
| Password | ValidPass123 |

**Expected Result:**
- User is redirected to `www.example.com/home`
- User's name "Valid User" is displayed in the top right corner of the page

**Actual Result:** *(filled in during execution)*

**Pass/Fail:** *(filled in during execution)*

**Post-Conditions:**
- Log out the user account after test completion

---

## Best Practices Summary

| Practice | Why It Matters |
|---|---|
| Be clear and concise | Any tester should understand it immediately |
| Be specific | Vague tests produce unreliable results |
| One action per step | Easier to pinpoint exactly where a failure occurs |
| Cover all scenarios | Positive, negative, and boundary value tests |
| Include realistic test data | Catches real-world bugs that fake data misses |
| Review with another tester | Fresh eyes catch gaps and ambiguities |
| Prioritize critical features | Test what matters most first |
| Keep test cases maintainable | Easy to update when the feature changes |

---

## Test Case Types — What to Cover

For every feature, write test cases across these categories:

| Type | What It Tests | Example |
|---|---|---|
| **Positive / Functional** | Happy path — things that should work | Valid login with correct credentials |
| **Negative** | Error handling — things that should fail gracefully | Login with wrong password |
| **Boundary** | Edge of valid range | Password exactly 8 characters |
| **UI / Usability** | Visual and layout correctness | Error message displayed in red |
| **Security** | Unauthorized access attempts | SQL injection in login field |

---

## Naming Convention Reference

```
TC_[MODULE]_[FEATURE]_[NUMBER]

Examples:
TC_LOGIN_001         → Login module, test 001
TC_CART_ADD_005      → Cart module, add item feature, test 005
TC_CHECKOUT_PAY_012  → Checkout module, payment feature, test 012
TC_REG_EMAIL_003     → Registration module, email field, test 003
```

---

*Previous topic: decision-table-testing.md*
*Next topic: test-data-and-environments.md*
