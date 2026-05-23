# Regression Testing — Ensuring Stability After Changes
> Source: QA Learn the Fundamentals — Module 3, Lesson 5 | roadmap.sh
> Last updated: 2026

---

## What is Regression Testing?

Regression testing verifies that **recent code changes have not broken existing functionality**. Its goal is to confirm that previously tested software still performs as expected after any modification, update, or bug fix — and that no new bugs have been introduced in the process.

> Regression testing = re-validating that what worked before still works after a change.

---

## Core Principles

| Principle | Description |
|---|---|
| **Re-running Tests** | Re-execute a subset or the full test suite after every code change |
| **Verification of Existing Functionality** | Confirm previously working features remain intact |
| **Early Detection** | Catching regression bugs early reduces the cost and effort to fix them |
| **Automated Testing** | Due to its repetitive nature, automation is essential for efficiency and coverage |

---

## Why Regression Testing Matters

- **Stability** — Ensures changes don't break existing functionality
- **Quality Assurance** — Verifies the software continues to meet requirements
- **Risk Mitigation** — Reduces the chance of regressions reaching production
- **Customer Satisfaction** — Keeps the product reliable for end users

---

## When to Perform Regression Testing

Run regression tests whenever the software changes, including:

- New features are added
- Bugs are fixed (confirm the fix didn't introduce new issues)
- Existing code is modified or refactored
- Configuration settings are changed
- The software is integrated with another system
- The underlying OS, database, or environment is updated

---

## Types of Regression Testing

---

### 1. Corrective Regression Testing
**Purpose:** Retest the changed code and its immediate surroundings to confirm the fix is correct.
**Scope:** Narrow — only the directly modified code.

**Example:**
```
Bug fixed in: User Authentication module
Tests to rerun: Login, logout, password reset
```

---

### 2. Selective Regression Testing
**Purpose:** Run only the subset of test cases most likely affected by the change.
**Scope:** Moderate — areas most impacted.
**Benefit:** Saves time by focusing only on the most relevant tests.

---

### 3. Complete Regression Testing
**Purpose:** Re-run the entire test suite to ensure nothing is broken.
**Scope:** Comprehensive — all aspects of the software.
**When used:** After major releases or when risk of regression is high.
**Drawback:** Time-consuming and resource-intensive.

---

## Regression Test Suite Selection

A well-designed regression test suite should:
- Cover all **critical functionality**
- Reflect **real user scenarios**
- Be **kept up-to-date** as the software evolves
- Be **automated** wherever possible

### Strategies

| Strategy | Description | Example |
|---|---|---|
| **Prioritization** | Run high-risk, high-frequency tests first | Login, checkout, payment before minor features |
| **Test Case Optimization** | Remove redundant or obsolete tests | Keep only the most effective test per functionality |
| **Impact Analysis** | Identify tests affected by specific code changes | DB schema change → prioritize tests hitting affected tables |
| **Categorization** | Group tests by module or risk level | "User Management", "Order Processing", "Product Catalog" |

---

## Automation in Regression Testing

Because regression testing is repetitive by nature, automation is a key part of any effective strategy.

### Benefits of Test Automation

| Benefit | Description |
|---|---|
| **Increased Efficiency** | Frees up time and allows more frequent test cycles |
| **Improved Accuracy** | Less prone to human error |
| **Enhanced Coverage** | More tests run in less time |
| **Faster Feedback** | Developers get results quickly and fix issues sooner |

### Common Tools and Frameworks

| Tool | Use Case |
|---|---|
| **Selenium** | Browser automation for web apps |
| **Cypress** | Modern JavaScript end-to-end testing |
| **JUnit** | Unit testing for Java |
| **TestNG** | Java testing framework supporting unit, integration, and E2E |

### Example — Automating a Login Test with Selenium (Python)

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import unittest

class LoginTest(unittest.TestCase):

    def setUp(self):
        self.driver = webdriver.Chrome()
        self.driver.get("https://example.com/login")

    def test_login_success(self):
        self.driver.find_element(By.ID, "username").send_keys("testuser")
        self.driver.find_element(By.ID, "password").send_keys("password123")
        self.driver.find_element(By.ID, "login-button").click()

        WebDriverWait(self.driver, 10).until(
            EC.presence_of_element_located((By.ID, "success-message"))
        )

        success_message = self.driver.find_element(By.ID, "success-message")
        self.assertTrue(success_message.is_displayed())

    def tearDown(self):
        self.driver.quit()

if __name__ == "__main__":
    unittest.main()
```

**Key concepts in the example:**

| Method / Call | What it does |
|---|---|
| `setUp` | Runs before each test — launches the browser and navigates to the login page |
| `test_login_success` | The actual test — fills credentials, clicks login, asserts success |
| `tearDown` | Runs after each test — closes the browser |
| `find_element(By.ID, ...)` | Locates an HTML element by its ID attribute |
| `send_keys(...)` | Types text into an input field |
| `WebDriverWait(...).until(...)` | Explicit wait — pauses until a condition is met or timeout occurs |
| `assertTrue(...)` | Assertion — fails the test if the condition is false |

> Install Selenium: `pip install selenium` — ChromeDriver must also be installed and on your system PATH.

---

## Challenges in Regression Testing

- **Test Suite Maintenance** — Keeping tests current as the codebase evolves is ongoing work
- **Test Case Selection** — Choosing the right tests for each change requires judgment
- **Automation Costs** — Writing and maintaining automated tests takes time and resources
- **False Positives** — Automated tests can sometimes flag issues that don't actually exist

---

## Best Practices

- **Define a clear strategy** — Scope, frequency, and selection criteria upfront
- **Prioritize critical functionality** — Test the highest-risk areas first
- **Automate as much as possible** — Reduces effort over time and increases reliability
- **Use a test management tool** — Track cases, results, and reports systematically
- **Integrate with CI/CD** — Automatically run regression tests on every code change *(covered in Module 7)*
- **Version control your tests** — Store test scripts in Git alongside application code
- **Continuously improve** — Regularly review and refine the process

---

## Real-World Examples

### E-Commerce (Amazon)
Amazon adds a new product recommendation algorithm. Regression testing confirms existing features still work:
- Adding items to cart
- Checkout process
- User login/logout
- Product search
- Order history and reviews

Tests also check the new algorithm doesn't impact performance or introduce security vulnerabilities.

### Banking App
A bank releases international money transfers. Regression testing protects:
- Balance inquiry
- Bill payment
- Internal fund transfers
- Login and security
- Statement generation

The new feature is also validated for regulatory compliance and security standards.

### Startup — InnovateTech
A project management tool adds CSV export. Their regression process:
1. **Identify affected areas** — Data storage, permissions, reporting
2. **Select test cases** — Existing tests for affected areas + new export-specific tests
3. **Execute tests** — Run full selected suite
4. **Analyze results** — Spot any regressions or new bugs
5. **Fix and retest** — Resolve bugs, re-run regression suite to confirm

---

## Key Takeaway

> Regression testing is the safety net that lets teams move fast without breaking things. The more automated and well-maintained your regression suite is, the more confidently you can ship changes.

---

## Quick Reference

```
Types of Regression Testing:
Corrective  → Narrow scope, retest the fixed area only
Selective   → Moderate scope, most-impacted areas
Complete    → Full suite, used after major releases

When to run regression tests:
✔ New feature added          ✔ Code refactored
✔ Bug fixed                  ✔ Config changed
✔ New system integrated      ✔ Environment updated

Best Practices:
✔ Automate repetitive tests
✔ Integrate into CI/CD pipeline
✔ Version control your test scripts
✔ Prioritize high-risk, high-frequency tests
```

---

*Module 3 — Testing Types*
*Previous: user-acceptance-testing.md | Next: performance-testing.md*
