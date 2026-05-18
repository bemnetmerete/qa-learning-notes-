# Test Data and Test Environments
> Source: QA Learn the Fundamentals — Module 2, Lesson 5 | roadmap.sh
> Last updated: 2026

---

## Overview

Two things every QA engineer needs before testing can begin:

1. **Test Data** — the inputs you feed into the system during testing
2. **Test Environment** — the setup (hardware, software, network) where testing runs

> Without good test data and a stable environment, even the best test cases produce unreliable results.

---

# PART 1 — Test Data

## What is Test Data?

Test data is any information used as input when executing a test case. It directly determines whether your testing is effective or full of gaps.

> Poor test data = missed bugs. Good test data = comprehensive coverage.

---

## Types of Test Data

| Type | Description | Example |
|---|---|---|
| **Valid Data** | Correct format, within accepted range | Email: `user@example.com` |
| **Invalid Data** | Wrong format or out of range | Email: `user@@example` |
| **Boundary Value Data** | At the edges of valid range | Age: 17, 18, 65, 66 |
| **Equivalence Partition Data** | Representative of each input group | Age under 18, 18-65, over 65 |
| **Performance Data** | Large volumes to test load handling | 10,000 customer records |
| **Security Data** | Malicious inputs to test vulnerabilities | `' OR '1'='1` (SQL injection) |

---

## Real Example — E-commerce Test Data Set

**Valid Data:**
```
Customer Name:  John Doe
Email:          john.doe@example.com
Address:        123 Main Street, Anytown
Product ID:     ABC123
Quantity:       1
Payment:        Credit Card
```

**Invalid Data:**
```
Customer Name:  (empty)
Email:          invalid-email
Address:        123!@# Main Street (invalid characters)
Product ID:     XYZ999 (non-existent product)
Quantity:       -1 (negative number)
Payment:        Invalid Payment Method
```

**Boundary Data:**
```
Quantity: 0 (below minimum)
Quantity: 1 (minimum valid)
Quantity: 99 (maximum valid)
Quantity: 100 (above maximum)
```

**Performance Data:**
```
10,000 customer records
100,000 product records
1,000,000 order records
```

**Security Data:**
```
Search field: ' OR '1'='1     (SQL injection attempt)
Review field: <script>alert('XSS')</script>   (XSS attempt)
```

---

## Test Data Creation Techniques

### 1. Manual Creation
Create test data by hand based on requirements.
- ✅ Highly specific and targeted
- ✅ Good for exploratory testing
- ❌ Time-consuming
- ❌ Hard to generate large volumes

### 2. Data Generation Tools
Use automated tools to generate large volumes of test data.
- ✅ Fast — generates thousands of records in seconds
- ✅ Consistent and reproducible
- ❌ Generated data may not always feel realistic
- **Tools:** Mockaroo, Faker, GenerateData.com

### 3. Data Cloning
Copy real data from production to the test environment.
- ✅ Most realistic data possible
- ❌ Must be anonymized to protect real users' private information
- **Important:** Never use real customer credit cards, passwords, or personal data without anonymization

### 4. Data Mining
Extract and modify data from existing databases.
- ✅ Uses real patterns and distributions
- ❌ Requires database access and SQL knowledge

### 5. Hybrid Approach (Recommended)
Combine multiple techniques — generate a base dataset with tools, then manually add specific edge cases and boundary values.

---

## Test Data Management

Once you have test data, managing it properly is just as important as creating it.

| Practice | Description |
|---|---|
| **Data Storage** | Store in a centralized repo — database, shared folder, or test data tool |
| **Data Versioning** | Keep different versions for different test cycles |
| **Data Refreshing** | Regularly update to keep data current and relevant |
| **Data Anonymization** | Mask real names, emails, card numbers from cloned production data |
| **Data Subsetting** | Use smaller representative subsets to reduce storage and complexity |

---

# PART 2 — Test Environments

## What is a Test Environment?

A test environment is the complete setup — hardware, software, network, and configuration — used to run tests. It should be as close as possible to the real production environment.

> If your test environment doesn't match production, bugs will hide in the gaps between them.

---

## Why Test Environments Matter

| Reason | Explanation |
|---|---|
| **Realistic testing** | Simulates real conditions users will experience |
| **Isolation** | Prevents test activity from affecting live production data |
| **Reproducibility** | Consistent setup means consistent, reliable results |
| **Early defect detection** | Representative environment catches environment-specific bugs early |

---

## Components of a Test Environment

| Component | Examples |
|---|---|
| **Hardware** | Servers, laptops, mobile phones, tablets |
| **Software** | OS, browser, database, application server |
| **Network** | Wi-Fi, cellular, VPN, firewall settings |
| **Data** | Test data loaded and ready for use |
| **Test Tools** | Selenium, Postman, JIRA, TestRail, Appium |
| **Configuration** | Specific settings, environment variables, feature flags |

---

## Types of Test Environments

```
Development Environment
    ↓ (used by developers — least stable)

Test / QA Environment
    ↓ (used by QA — should match production closely)

Staging Environment
    ↓ (final pre-release environment — mirrors production exactly)

Production Environment
    (live environment — real users)
```

| Environment | Used By | Stability | Purpose |
|---|---|---|---|
| **Development** | Developers | Low | Writing and unit testing code |
| **Test / QA** | QA Engineers | Medium | Formal functional testing |
| **Staging** | QA + Stakeholders | High | Final UAT before release |
| **Production** | End Users | Highest | Live software |

---

## Setting Up a Test Environment

```
Step 1: Requirements Gathering
        → Understand hardware, software, and network needs

Step 2: Environment Design
        → Plan the setup based on resources and requirements

Step 3: Environment Setup
        → Install OS, browsers, databases, application server

Step 4: Data Setup
        → Load test data into the environment

Step 5: Test Tool Setup
        → Install and configure Selenium, Postman, JIRA etc.

Step 6: Environment Validation
        → Verify everything works correctly before testing begins
```

---

## Maintaining a Test Environment

| Task | Description |
|---|---|
| **Regular Updates** | Keep OS, browsers, and tools patched and current |
| **Configuration Management** | Track every configuration change made |
| **Backup and Recovery** | Regularly back up so it can be restored after failures |
| **Performance Monitoring** | Watch for slowdowns that could affect test results |
| **Security Management** | Protect the environment from unauthorized access |

---

## Real Example — Mobile App Test Environment

**App:** "MyApp" available on iOS and Android.

```
Hardware:
- Multiple iPhones with different iOS versions
- Multiple Android phones with different Android versions
- iPads and Android tablets

Software:
- iOS 16, 17 and Android 12, 13, 14
- MyApp application (build under test)
- Appium (mobile automation tool)

Network:
- Wi-Fi connection
- 4G/5G cellular network

Data:
- Test accounts for registration, login, and all features

Test Tools:
- Appium → automation
- JIRA → bug tracking
- TestRail → test case management
```

---

## Key Takeaways

> **Test Data:** Garbage in = garbage out. Your tests are only as good as the data you feed them.

> **Test Environment:** A bug found in the wrong environment is a bug that misleads. Match your environment to production as closely as possible.

---

## Quick Reference

```
Test Data Types:
✅ Valid      → normal, accepted inputs
✅ Invalid    → rejected, error-triggering inputs
✅ Boundary   → at the edges of valid ranges
✅ Performance → large volumes for load testing
✅ Security   → malicious inputs for vulnerability testing

Test Environment Types:
🔵 Development → developer's sandbox
🟡 Test/QA     → formal QA testing
🟠 Staging     → pre-release validation
🔴 Production  → live users
```

---

*Previous topic: writing-effective-test-cases.md*
*Next topic: Continue with Module 3 topics*
