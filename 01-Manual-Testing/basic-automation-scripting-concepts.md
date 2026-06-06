# Basic Automation Scripting Concepts

> **Course:** QA: Learn the Fundamentals | **Module 6 – Test Automation** | **Lesson 3 of 35**

---

## Overview

Basic automation scripting concepts allow you to translate manual test cases into automated scripts, making testing faster, more efficient, and more reliable. Every automation script — regardless of tool or language — shares the same core structure.

---

## Core Elements of an Automation Script

```
┌─────────────────────────────────────────────┐
│           Automation Script Structure        │
├─────────────────────────────────────────────┤
│  1. TEST SETUP     → Prepare environment     │
│  2. TEST STEPS     → Simulate user actions   │
│  3. ASSERTIONS     → Verify expected results │
│  4. TEST TEARDOWN  → Clean up environment    │
└─────────────────────────────────────────────┘
```

---

## 1. Test Setup — Preparing the Environment

Test setup configures the application to a **known state** before the test runs. Without it, tests produce inconsistent or unreliable results.

Setup tasks typically include:
- Launching the application (browser, mobile app, desktop)
- Navigating to the correct starting page or screen
- Creating test data (accounts, database records, config files)
- Setting environment variables or installing dependencies

**Example (e-commerce):**
```
1. Launch Chrome browser
2. Navigate to homepage
3. Log in with test account
4. Add a product to the cart
```

---

## 2. Test Steps — Simulating User Actions

Test steps are the heart of the script. They replicate what a real user would do when interacting with the application.

Common actions:
- Clicking buttons and links
- Entering text into fields
- Selecting options from dropdowns
- Submitting forms
- Scrolling and navigating

**Considerations for effective test steps:**

| Principle | Description |
|---|---|
| **Clarity** | Each step should be clearly defined and easy to understand |
| **Granularity** | Steps should be specific enough to isolate failures |
| **Maintainability** | Steps should be easy to update as the application evolves |

---

## 3. Assertions — Validating Expected Behavior

Assertions are **checks that determine pass or fail**. They verify that the application behaves as expected after each action.

### What assertions can verify:
- Presence of elements on the page
- Text content of elements
- Attribute values (e.g., `disabled`, `checked`)
- Application state (e.g., correct URL after redirect)
- Error messages displayed to the user

### Types of Assertions

| Type | Purpose | Example |
|---|---|---|
| **Equality** | Two values are equal | `assertEqual(actual, expected)` |
| **Inequality** | Two values are not equal | `assertNotEqual(a, b)` |
| **Boolean** | Value is true or false | `assertTrue(is_logged_in)` |
| **Null** | Value is null or not null | `assertNotNull(element)` |
| **Contains** | String contains a substring | `assertContains("Welcome", page_text)` |

---

## 4. Test Teardown — Cleaning Up

Teardown runs after the test to reset the environment for the next test. Without it, tests can interfere with each other.

Teardown tasks typically include:
- Logging out of the application
- Deleting test data (accounts, orders, records)
- Closing the browser or application
- Restoring database to its original state
- Releasing system resources (memory, network connections)

---

## Common Scripting Elements

### Variables — Storing Data

Variables hold values used throughout the script, making scripts easier to read and update.

```python
# Define variables
username = "testuser"
password = "password123"
url = "https://www.example.com"

# Use variables
driver.get(url)
driver.find_element("id", "username").send_keys(username)
```

**Data types commonly used:**

| Type | Example |
|---|---|
| String | `"testuser"` |
| Integer | `42` |
| Float | `9.99` |
| Boolean | `True` / `False` |

---

### Control Flow — Directing Script Execution

#### If-Else Statements
```python
if login_successful:
    print("Proceed to dashboard")
else:
    print("Show error message")
```

#### For Loop — Repeat a fixed number of times
```python
for i in range(5):
    print(i)  # Output: 0, 1, 2, 3, 4
```

#### While Loop — Repeat while condition is true
```python
count = 0
while count < 5:
    print(count)
    count += 1
```

---

### Functions — Reusable Code Blocks

Functions break complex scripts into smaller, manageable pieces that can be reused.

```python
def login(driver, username, password):
    driver.find_element("id", "username").send_keys(username)
    driver.find_element("id", "password").send_keys(password)
    driver.find_element("id", "loginBtn").click()

# Call the function in any test
login(driver, "testuser", "password123")
```

**Benefits of using functions:**

| Benefit | Description |
|---|---|
| **Reusability** | Call the same function from multiple tests |
| **Modularity** | Break complex scripts into smaller pieces |
| **Readability** | Scripts are easier to follow |
| **Maintainability** | Update logic in one place, applied everywhere |

---

### Comments — Explaining the Code

```python
# This function handles the login process
def login(driver, username, password):
    driver.find_element("id", "username").send_keys(username)  # Enter username
    driver.find_element("id", "password").send_keys(password)

'''
Multi-line comment:
This test verifies that a valid user
can successfully log in to the system.
'''
```

**Best practices:**
- Explain *why*, not just *what*
- Keep comments up to date when code changes
- Avoid commenting the obvious

---

## Full Script Structure (Pseudocode)

```
# TEST SETUP
Launch Browser
Navigate to Login Page

# TEST STEPS
Enter Username "testuser" into Username Field
Enter Password "password123" into Password Field
Click Login Button

# ASSERTIONS
Verify user is redirected to the Home Page
Verify Welcome Message contains "testuser"

# TEST TEARDOWN
Logout from the application
Close Browser
```

---

## Error Handling

Automation scripts must anticipate and handle errors gracefully to avoid crashes and unreliable results.

### Types of Errors

| Type | Description |
|---|---|
| **Syntax Error** | Typo or incorrect code structure |
| **Runtime Error** | Occurs during execution (e.g., element not found) |
| **Logical Error** | Incorrect logic producing wrong results |
| **Exception** | Unexpected event (e.g., network timeout, file not found) |

### Try-Except Block (Python)

```python
try:
    element = driver.find_element("id", "submitBtn")
    element.click()
except Exception as e:
    print(f"Error: Element not found — {e}")
```

---

## Best Practices for Automation Scripting

| Practice | Description |
|---|---|
| **Modular design** | Break scripts into small, reusable functions |
| **Descriptive names** | Use clear names for variables, functions, and classes |
| **Clear code** | Write code that is easy to read and understand |
| **Add comments** | Explain purpose and complex logic |
| **Handle errors** | Anticipate and catch exceptions gracefully |
| **Use version control** | Track all script changes with Git |
| **Follow coding standards** | Follow style guides for your language (e.g., PEP8 for Python) |

---

## Summary

- Every automation script follows four core phases: **Setup → Steps → Assertions → Teardown**
- **Variables** store data; **control flow** directs execution; **functions** enable reuse; **comments** improve readability
- **Assertions** are the mechanism that determines pass or fail
- **Error handling** prevents scripts from crashing unexpectedly
- Good scripting practices make tests easier to maintain as the application grows

---

## Next Lesson

➡️ [Lesson 4 – Understanding Test Automation Frameworks](./understanding-test-automation-frameworks.md)

## Previous Lesson

⬅️ [Lesson 2 – Introduction to Automation Tools](./introduction-to-automation-tools.md)
