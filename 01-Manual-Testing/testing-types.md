# Testing Methodologies — Black Box, White Box, and Gray Box
> Source: QA Learn the Fundamentals — Lesson 4 | roadmap.sh
> Last updated: 2026

---

## Overview

Testing methodologies provide different perspectives for verifying software quality. There are three fundamental approaches every QA engineer must understand:

| Methodology | Knowledge of Code | Who Uses It | Focus |
|---|---|---|---|
| Black Box | None | Manual testers | Inputs and outputs |
| White Box | Full | Developers, SDETs | Internal logic and code |
| Gray Box | Partial | QA engineers | Integration and data flow |

---

## 1. Black Box Testing

The tester has **no knowledge** of the internal code or architecture. The system is treated as a "black box" — you put something in and verify what comes out.

### Key Principles
- **Focus on functionality** — validates what the software does, not how
- **Input-output driven** — tests based on specifications and expected behavior
- **No internal knowledge needed** — tester does not need to know the code
- **User perspective** — simulates how a real user interacts with the software

### Techniques
- **Equivalence Partitioning** — divide inputs into groups where all values behave the same; test one value per group
- **Boundary Value Analysis** — test the exact edges of valid and invalid ranges where bugs are most common
- **Decision Table Testing** — map different input combinations to expected outputs
- **State Transition Testing** — test system behavior as it moves between different states
- **Use Case Testing** — create tests based on how users interact with the system to achieve goals

### Real Example — E-commerce Search
```
Input:  Search for "red shoes"
Output: Relevant results displayed in correct order
Knowledge used: None — no need to know how the search algorithm works
```

### Real Example — Online Banking Login
```
Input:  Valid username + wrong password
Output: Error message shown, account locked after 6 failed attempts
Knowledge used: None — no need to know how authentication works internally
```

### Advantages
- Easy to understand and implement
- User-centric — focuses on real user experience
- Testers do not need programming knowledge
- Can catch requirement and functionality bugs early

### Disadvantages
- May not cover all internal code paths
- Can lead to redundant tests
- Hard to identify root cause of bugs without code knowledge

---

## 2. White Box Testing

Also called **clear box** or **glass box** testing. The tester has **full knowledge** of the internal code, architecture, and implementation.

### Key Principles
- **Knowledge of internals** — tester understands the code structure
- **Code coverage** — tests are designed to cover as much code as possible
- **Focus on internal logic** — verifies control flow and logic correctness
- **Requires technical skills** — tester needs programming knowledge

### Techniques
- **Statement Coverage** — every line of code is executed at least once
- **Branch Coverage** — every if/else branch is executed at least once
- **Path Coverage** — every possible execution path is tested
- **Condition Coverage** — every condition evaluates to both true and false
- **Data Flow Testing** — tracks how data moves through the system

### Real Example — Testing a Sorting Algorithm (Python)
```python
def sort_list(data):
    n = len(data)
    for i in range(n):
        for j in range(0, n-i-1):
            if data[j] > data[j+1]:
                data[j], data[j+1] = data[j+1], data[j]
    return data
```
White box tests would cover:
- Already sorted list
- Reverse sorted list
- List with duplicate values
- Empty list

### Real Example — Input Validation Function
```python
def validate_input(username, password):
    if not username:
        return "Username cannot be empty"
    if len(password) < 8:
        return "Password must be at least 8 characters"
    if not any(char.isdigit() for char in password):
        return "Password must contain at least one digit"
    return "Valid input"
```
White box tests ensure every return statement is reached at least once.

### Advantages
- Thorough — can find hidden logic errors
- Helps identify code that can be optimized
- Easier to pinpoint exact location of a bug

### Disadvantages
- Complex — requires deep technical knowledge
- Time-consuming and costly
- Cannot identify usability or requirement issues
- Hard to scale on large systems

---

## 3. Gray Box Testing

Combines elements of both black box and white box. The tester has **partial knowledge** of the system internals — such as data structures, APIs, or architecture — but not the full source code.

### Key Principles
- **Partial knowledge** — knows some internals but not all
- **Focus on integration** — tests how different components interact
- **Bridges the gap** — balanced approach between black and white box
- **Protocol and standard compliance** — useful for systems following specific protocols

### Techniques
- **Database Testing** — validate data integrity and consistency
- **Security Testing** — identify vulnerabilities using architectural knowledge
- **Integration Testing** — test how different modules work together
- **Pattern Testing** — analyze logs and historical data to spot issues

### Real Example — API Testing
```
Knowledge: API endpoints, JSON request/response format, authentication mechanism
Tests:     Send requests with different parameters, validate response schema
Focus:     Ensure API adheres to its contract and handles edge cases correctly
```

### Real Example — Web App with Database
```
Knowledge: Database tables, relationships, and SQL queries used
Tests:     Validate data is stored correctly, test query performance
Focus:     Ensure data consistency between UI and database
```

### Advantages
- Balanced — combines benefits of both methodologies
- Targeted — focus on specific risk areas using internal knowledge
- Better bug detection than pure black box

### Disadvantages
- Requires some technical knowledge
- More complex than black box testing
- Partial knowledge can be incomplete or outdated

---

## Choosing the Right Methodology

| Factor | Black Box | White Box | Gray Box |
|---|---|---|---|
| You have full code access | ❌ | ✅ | ❌ |
| Testing user-facing features | ✅ | ❌ | ⚠️ |
| Testing critical algorithms | ❌ | ✅ | ❌ |
| Testing APIs or integrations | ❌ | ❌ | ✅ |
| No programming knowledge | ✅ | ❌ | ⚠️ |
| Need maximum code coverage | ❌ | ✅ | ❌ |

> **Best practice:** Most professional QA teams use a **combination** of all three methodologies for complete coverage.

---

## Quick Memory Aid

```
Black Box  = You're a USER    — you see only inputs and outputs
White Box  = You're a DEVELOPER — you see all the code inside
Gray Box   = You're a QA ENGINEER — you see some internals + outputs
```

---

*Next topic: test-case-design.md*
