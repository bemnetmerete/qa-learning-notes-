# Writing Clear and Concise Bug Reports
> Source: QA Learn the Fundamentals — Module 4, Lesson 2 | roadmap.sh
> Last updated: 2026

---

## Why Clear Bug Reports Matter

A well-written bug report is the cornerstone of communication between testers and developers. It's not just about pointing out a problem — it's about giving developers everything they need to understand, reproduce, and fix the bug efficiently.

| Benefit | Why It Matters |
|---|---|
| **Reduces Misinterpretation** | Clear language prevents developers from misreading the issue |
| **Saves Time** | Concise reports let developers grasp the problem quickly |
| **Improves Reproducibility** | Precise steps make it easier to recreate and verify the fix |
| **Enhances Collaboration** | Well-written reports foster better tester-developer communication |
| **Facilitates Tracking** | Consistent reports make it easier to analyze bug trends over time |

### Clarity in Practice

```
❌ Unclear:  "The thing doesn't work."
✅ Clear:    "The 'Submit' button on the registration page does not respond
             when clicked after entering a password longer than 20 characters."

❌ Verbose:  "When I was using the application, I was trying to register a new
             account. I entered my name, email, and then I tried to enter a really
             long password... and then when I clicked submit, nothing happened..."
✅ Concise:  "The 'Submit' button on the registration page is unresponsive
             after entering a password exceeding 20 characters."
```

---

## Key Components of a Bug Report

A complete bug report includes these 9 components:

| # | Component | Description |
|---|---|---|
| 1 | **Title / Summary** | Brief, descriptive summary of the bug |
| 2 | **Description** | Detailed explanation of symptoms and impact |
| 3 | **Steps to Reproduce** | Numbered steps that consistently trigger the bug |
| 4 | **Expected Result** | What should happen if the bug weren't present |
| 5 | **Actual Result** | What actually happens when the bug occurs |
| 6 | **Severity** | Impact of the bug on the application's functionality |
| 7 | **Priority** | Urgency with which the bug needs to be fixed |
| 8 | **Environment** | Hardware and software configuration where the bug was observed |
| 9 | **Attachments** | Screenshots, videos, or log files supporting the report |

---

## Component Breakdown

---

### 1. Title / Summary

The title is the first thing a developer sees. It must be specific and informative.

```
✅ Do:    "Incorrect Calculation of Total Price in Shopping Cart"
❌ Don't: "Bug in Shopping Cart"

✅ Do:    "Application Crash on Startup After Latest Update"
❌ Don't: "App is not working"
```

---

### 2. Description

Provide a comprehensive overview of the bug — what it is, where it occurs, and how it impacts users.

**Include:**
- The specific page or feature where the bug occurs
- Any error messages or unusual behavior
- How frequently the bug occurs (always, sometimes, rarely)

**Example:**
> "When adding multiple items to the shopping cart and proceeding to checkout, the total price displayed is higher than the sum of the individual item prices. This issue occurs consistently and may lead to customer dissatisfaction and abandoned purchases."

---

### 3. Steps to Reproduce

The most critical section. Developers must be able to follow these steps and see the bug themselves.

**Rules:**
- Use a **numbered list** — order matters
- Be **specific** — avoid "click here" or "enter data"
- Keep it **minimal** — only include steps necessary to trigger the bug

**Example:**
1. Navigate to the product page for "Product X"
2. Click the "Add to Cart" button
3. Navigate to the shopping cart page
4. Increase the quantity of "Product X" to 3
5. Click the "Checkout" button
6. Observe the total price displayed on the checkout page

---

### 4. Expected Result

What should happen if the bug were not present. Be precise and directly tied to the steps above.

**Example:**
> "The total price displayed on the checkout page should be the sum of the individual item prices, including applicable taxes and shipping fees."

---

### 5. Actual Result

A factual, objective account of what actually happens. No speculation.

**Rules:**
- Be objective — state facts only
- Include exact text of any error messages

**Example:**
> "The total price displayed is $150.00, while the correct sum of individual item prices (including tax and shipping) is $120.00."

---

### 6. Severity

| Level | Description |
|---|---|
| **Critical** | Complete system failure or data loss |
| **Major** | Major feature is unusable |
| **Minor** | Minor inconvenience or cosmetic issue |
| **Trivial** | Very minor issue with no functional impact |

---

### 7. Priority

| Level | Description |
|---|---|
| **Immediate** | Fix now — prevents further damage or disruption |
| **High** | Fix as soon as possible |
| **Medium** | Fix in the next sprint or release |
| **Low** | Fix at a later date when resources allow |

---

### 8. Environment

Specify the exact configuration where the bug was observed.

**Include:**
- Operating system and version
- Browser and version
- Device type (desktop, laptop, tablet, phone)
- Screen resolution
- Any other relevant software or hardware

**Example:**
```
Operating System:  Windows 10
Browser:           Chrome 98.0.4758.102
Device:            Desktop Computer
Screen Resolution: 1920x1080
```

---

### 9. Attachments

Supporting evidence that helps developers understand the bug faster.

- **Screenshots** — capture the visual state of the bug
- **Videos** — demonstrate the steps to reproduce
- **Log files** — detailed application behavior
- **Error messages** — exact text of any errors shown

---

## Good vs. Bad Steps to Reproduce

| ❌ Bad Steps | ✅ Good Steps |
|---|---|
| 1. Click around | 1. Navigate to the "Settings" page by clicking the gear icon in the top right corner |
| 2. Do something with the form | 2. Enter "test@example.com" in the "Email Address" field |
| 3. It breaks | 3. Click the "Save Changes" button |
| 4. See the error | 4. Observe that the error message "Invalid Email Address" appears below the field, even though the email is valid |

---

## Full Bug Report Examples

### Example 1 — E-Commerce Product Search

```
Title:       Product Search Returns Incorrect Results for "Red Shirt"

Description: When searching for "Red Shirt," the results include unrelated items
             such as blue shirts and hats. This may cause customer frustration
             and difficulty finding desired products.

Steps to Reproduce:
  1. Navigate to the e-commerce website's homepage
  2. Enter "Red Shirt" in the search bar
  3. Click the "Search" button
  4. Observe the search results

Expected Result: Only red shirts should appear in the search results.
Actual Result:   Results include blue shirts, hats, and other unrelated items.

Severity:    Major
Priority:    High

Environment:
  OS:      Windows 10
  Browser: Chrome 98.0.4758.102
  Device:  Desktop Computer

Attachments: Screenshot of search results page
```

---

### Example 2 — Mobile App Crash on Image Upload

```
Title:       Application Crash When Uploading Image Larger Than 5MB

Description: The mobile app crashes when a user attempts to upload an image
             larger than 5MB, preventing users from sharing high-resolution photos.

Steps to Reproduce:
  1. Open the mobile application
  2. Navigate to the "Upload Photo" section
  3. Select an image file larger than 5MB from the device's photo library
  4. Click the "Upload" button
  5. Observe the application's behavior

Expected Result: The app should upload the image successfully, or display a
                 user-friendly message: "Images should be less than 5MB."
Actual Result:   The application crashes and closes unexpectedly.

Severity:    Major
Priority:    High

Environment:
  OS:     iOS 15.2
  Device: iPhone 13 Pro

Attachments: Video recording of the application crash
```

---

## Exercise — Improve This Bug Report

**Original (poor quality):**
```
Title:              Login doesn't work
Description:        I can't login
Steps to Reproduce: Try to login
Expected Result:    Login
Actual Result:      Doesn't login
```

**Improved version:**
```
Title:       Login fails with valid credentials on the web app

Description: Users are unable to log in despite entering correct username and
             password. The page refreshes without any error message shown.
             This issue occurs consistently and blocks all access to the application.

Steps to Reproduce:
  1. Navigate to https://example.com/login
  2. Enter a valid username in the "Email" field (e.g., user@test.com)
  3. Enter the correct password in the "Password" field
  4. Click the "Login" button
  5. Observe the result

Expected Result: User is redirected to the dashboard after successful login.
Actual Result:   The page refreshes and the user remains on the login page.
                 No error message is displayed.

Severity:    Critical
Priority:    Immediate

Environment:
  OS:      Windows 10
  Browser: Chrome 120.0
  Device:  Desktop
```

---

## Key Takeaway

> A bug report is only as useful as it is reproducible. If a developer can't recreate the bug from your report alone, the report has failed its purpose. Always ask: *"Could someone fix this bug using only what I've written?"*

---

## Quick Reference

```
9 Components of a Bug Report:
1. Title          — Specific and descriptive
2. Description    — What, where, how often
3. Steps          — Numbered, specific, minimal
4. Expected       — What should happen
5. Actual         — What actually happens (facts only)
6. Severity       — Critical / Major / Minor / Trivial
7. Priority       — Immediate / High / Medium / Low
8. Environment    — OS, browser, device, resolution
9. Attachments    — Screenshots, videos, logs

Golden Rule:
If a developer can't reproduce it from your report → rewrite it.
```

---

*Module 4 — Bug Reporting and Tracking*
*Previous: what-is-a-bug.md | Next: bug-tracking-systems.md*
