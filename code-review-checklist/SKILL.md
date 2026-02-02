---name: code-review-checklist
description: "A comprehensive checklist for conducting effective code reviews, ensuring code quality, and adhering to best practices."
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Code Review Checklist

## Overview
This skill provides a comprehensive and structured checklist for conducting thorough code reviews. It is designed to help developers and teams ensure that new code contributions are of high quality, maintainable, secure, and aligned with project standards. By following this checklist, reviewers can systematically assess code changes, provide constructive feedback, and improve the overall health of the codebase. This skill is particularly useful for establishing a consistent review process, onboarding new team members, and fostering a culture of quality engineering.

## When to Use This Skill
This skill is valuable in a variety of scenarios, including:

- **Daily Code Reviews:** Use it as a day-to-day guide for reviewing pull requests or merge requests.
- **Onboarding New Developers:** Help new team members understand the team's coding standards and review process.
- **Establishing Coding Standards:** Use the checklist as a foundation for creating or refining your team's official coding standards.
- **Pre-Release Quality Checks:** Perform a final, in-depth review of critical features before a major release.
- **Refactoring Legacy Code:** Guide the review process when refactoring old or complex parts of the application.
- **Self-Review:** Encourage developers to use the checklist to review their own code before submitting it for review.
- **Training and Mentorship:** Use it as a tool for training junior developers on code quality and best practices.

## Core Capabilities
This skill is organized into several core areas of focus, each with a detailed checklist. These capabilities ensure a 360-degree review of the code.

### 1. Functionality and Logic
This section focuses on verifying that the code works as intended and is logically sound.

- **[ ] Correctness:** Does the code accomplish its stated goal? Does it solve the problem it was intended to solve?
- **[ ] Requirements:** Does the code meet all the requirements specified in the ticket, user story, or task?
- **[ ] Edge Cases:** Are edge cases and corner cases handled correctly? (e.g., null inputs, empty lists, zero values, invalid data)
- **[ ] Error Handling:** Is error handling robust? Does the code gracefully handle potential failures (e.g., network errors, file not found, invalid user input)? Are the error messages clear and helpful?
- **[ ] Logic Complexity:** Is the logic unnecessarily complex? Can it be simplified? (e.g., reducing nested loops, simplifying conditional statements).
- **[ ] No Side Effects:** Does the code have any unintended side effects? Does it modify state unexpectedly?
- **[ ] Concurrency:** If the code is concurrent or asynchronous, are there any race conditions, deadlocks, or other concurrency issues?

### 2. Readability and Maintainability
This section ensures the code is easy to understand, modify, and maintain in the future.

- **[ ] Naming Conventions:** Are variables, functions, classes, and methods named clearly and consistently? Do the names accurately describe their purpose?
- **[ ] Code Formatting:** Does the code adhere to the project's established style guide (e.g., PEP 8 for Python, Prettier for JavaScript)? Is the formatting consistent?
- **[ ] Comments and Documentation:** Is the code well-commented where necessary? Are complex algorithms or business logic explained? Is the public API documented (e.g., using JSDoc, DocStrings)?
- **[ ] Code Structure:** Is the code well-organized? Are files and directories structured logically? Are functions and classes small and focused on a single responsibility (Single Responsibility Principle)?
- **[ ] Don't Repeat Yourself (DRY):** Is there duplicated code that could be refactored into a shared function or class?
- **[ ] Magic Numbers/Strings:** Are magic numbers and strings avoided? Are they defined as constants with meaningful names?
- **[ ] Readability:** Is the code easy to read and follow for someone unfamiliar with it?

### 3. Performance
This section focuses on identifying potential performance bottlenecks.

- **[ ] Algorithmic Complexity:** Is the algorithm efficient? What is its Big O notation? Could a more efficient algorithm be used?
- **[ ] Database Queries:** Are database queries optimized? Are there any N+1 query problems? Are appropriate indexes used?
- **[ ] Memory Usage:** Is the code mindful of memory usage? Are there any potential memory leaks? Are large objects held in memory unnecessarily?
- **[ ] Network Requests:** Are network requests minimized? Is data being fetched efficiently?
- **[ ] Resource Management:** Are resources like file handles, database connections, and network connections properly opened and closed?

### 4. Security
This section is critical for identifying and mitigating security vulnerabilities.

- **[ ] Input Validation:** Is all user-provided input validated and sanitized to prevent injection attacks (e.g., SQL injection, Cross-Site Scripting (XSS))?
- **[ ] Authentication and Authorization:** Is authentication and authorization handled correctly? Does the code check if the user has the necessary permissions to perform an action?
- **[ ] Sensitive Data:** Is sensitive data (e.g., passwords, API keys, personal information) handled securely? Is it encrypted in transit and at rest? Are secrets hard-coded in the source code?
- **[ ] Dependency Security:** Are the third-party libraries and dependencies up-to-date and free from known vulnerabilities?
- **[ ] Secure Defaults:** Does the code use secure defaults?

### 5. Testing
This section ensures that the code is well-tested and that the tests are effective.

- **[ ] Test Coverage:** Is there adequate test coverage for the new code? Are there unit tests, integration tests, and/or end-to-end tests?
- **[ ] Test Quality:** Are the tests well-written? Are they easy to understand? Do they test the right things?
- **[ ] Test Cases:** Do the tests cover both the happy path and failure scenarios/edge cases?
- **[ ] Testability:** Is the code easy to test? If not, could it be refactored to be more testable (e.g., using dependency injection)?

### 6. Best Practices and Design Patterns
This section focuses on adherence to general software engineering best practices and design principles.

- **[ ] SOLID Principles:** Does the code adhere to the SOLID principles of object-oriented design?
- **[ ] Design Patterns:** Are appropriate design patterns used? Are they implemented correctly?
- **[ ] Configuration Management:** Is configuration separated from the code? Is it handled through environment variables or configuration files?
- **[ ] Immutability:** Is immutability used where appropriate to prevent side effects?

## Step-by-Step Workflow
Here is a suggested workflow for using this skill to conduct a code review:

1.  **Understand the Context:** Before diving into the code, understand the purpose of the change. Read the ticket, user story, or bug report associated with the pull request. What problem is this change trying to solve?
2.  **High-Level Review:** Do a quick, high-level scan of the changes. Look at the file names, the overall structure, and the amount of code changed. Does the change seem reasonable in scope?
3.  **Detailed Checklist Review:** Go through the core capability checklists systematically:
    *   Start with **Functionality and Logic**. Does the code seem to work on a conceptual level?
    *   Move to **Readability and Maintainability**. Is the code clean and easy to understand?
    *   Assess **Performance**, **Security**, and **Testing**.
    *   Finally, consider **Best Practices and Design Patterns**.
4.  **Run the Code (If Possible):** If it's a significant or risky change, check out the branch and run the code locally. Test the functionality yourself.
5.  **Provide Constructive Feedback:** Write clear, concise, and respectful feedback. 
    *   Be specific. Instead of saying "this is confusing," say "this function name `handleData` is a bit vague. Could we rename it to `fetchAndProcessUserData` to be more descriptive?"
    *   Explain your reasoning. Link to best practices, documentation, or articles to support your suggestions.
    *   Frame feedback as suggestions or questions (e.g., "What do you think about...?", "Have you considered...?").
    *   Balance constructive criticism with positive reinforcement. Acknowledge what was done well.
6.  **Submit the Review:** Submit your comments. Be available to discuss your feedback with the author.
7.  **Follow-Up:** After the author has addressed the feedback, do a follow-up review to ensure the changes were implemented correctly.

## Best Practices
To make your code reviews as effective as possible, follow these best practices:

- **Be Kind and Respectful:** Remember that you are reviewing the code, not the person. Maintain a positive and collaborative tone.
- **Automate What You Can:** Use linters, static analysis tools, and automated tests to catch common issues automatically. This allows reviewers to focus on the more nuanced aspects of the review.
- **Keep Pull Requests Small:** Small, focused pull requests are easier and faster to review. Encourage developers to break down large features into smaller, incremental changes.
- **Review in a Timely Manner:** Don't let pull requests linger. A timely review process keeps the development workflow moving.
- **Don't Expect Perfection:** The goal of a code review is to improve the code, not to make it perfect. It's a collaborative process of incremental improvement.
- **Ask Questions:** If you don't understand something, ask for clarification. It's better to ask than to make assumptions.
- **Provide Examples:** When suggesting a change, providing a code snippet can be very helpful.

## Examples

### Example 1: Improving Readability

**Original Code:**
```javascript
// Bad: Vague function name and magic numbers
function process(data) {
  if (data.length > 10) {
    return data.slice(0, 10);
  }
  return data;
}
```

**Review Feedback:**
"This function is a bit hard to understand at a glance. Could we improve the naming and get rid of the magic number? For example, what if we renamed `process` to `truncateData` and defined `10` as a constant like `MAX_ITEMS`?"

**Improved Code:**
```javascript
// Good: Clear function name and constant
const MAX_ITEMS = 10;

function truncateData(data) {
  if (data.length > MAX_ITEMS) {
    return data.slice(0, MAX_ITEMS);
  }
  return data;
}
```

### Example 2: Handling Edge Cases

**Original Code:**
```python
# Bad: Assumes user and profile always exist
def get_user_city(user):
    return user.profile.address.city
```

**Review Feedback:**
"This could raise an `AttributeError` if `user`, `user.profile`, or `user.profile.address` is `None`. Have you considered adding some checks to handle these cases gracefully? Maybe return a default value or raise a more specific exception."

**Improved Code:**
```python
# Good: Handles potential null values
def get_user_city(user):
    if user and user.profile and user.profile.address:
        return user.profile.address.city
    return "City not available"
```

### Example 3: Security - SQL Injection

**Original Code:**
```php
// Bad: Vulnerable to SQL Injection
$userId = $_POST['userId'];
$query = "SELECT * FROM users WHERE id = " . $userId;
$result = mysqli_query($conn, $query);
```

**Review Feedback:**
"This query is vulnerable to SQL injection. We should use prepared statements to safely handle user input. This is a critical security issue that needs to be fixed."

**Improved Code:**
```php
// Good: Uses prepared statements
$userId = $_POST['userId'];
$stmt = $conn->prepare("SELECT * FROM users WHERE id = ?");
$stmt->bind_param("i", $userId);
$stmt->execute();
$result = $stmt->get_result();
```

## Code Review Templates

Here are some templates you can use for your code reviews.

### General Checklist Template (Markdown)

```markdown
## Code Review Checklist

### Functionality
- [ ] Does the code work as expected?
- [ ] Are edge cases handled?

### Readability
- [ ] Is the code easy to understand?
- [ ] Are naming conventions followed?

### Performance
- [ ] Are there any performance concerns?

### Security
- [ ] Are there any security vulnerabilities?

### Testing
- [ ] Is the code well-tested?

### Comments

[Your detailed comments here]
```

### Pull Request Description Template

Encourage developers to use a good pull request template to provide context for the reviewer.

```markdown
## Description

[Provide a detailed description of the changes.]

## Related Ticket

[Link to the Jira ticket, Trello card, etc.]

## Type of Change

- [ ] Bug fix
- [ ] New feature
- [ ] Refactoring
- [ ] Documentation update

## How to Test

[Provide step-by-step instructions on how to test these changes.]

## Screenshots

[If applicable, add screenshots to demonstrate the changes.]
```

## References

- [Google's Engineering Practices Documentation](https://google.github.io/eng-practices/)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [OWASP Top Ten](https://owasp.org/www-project-top-ten/)
- [SOLID Principles for C# Developers](https.www.codeproject.com/Articles/536905/SOLID-Principles-for-Csharp-Developers)
- [How to Make Your Code Reviewer Fall in Love with You](https://mtlynch.io/code-review-love/)
