---
name: accessibility-checker
description: A skill to check web accessibility following the Web Content Accessibility Guidelines (WCAG).
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Web Accessibility Checker (WCAG)

## Overview
This skill provides a comprehensive framework for evaluating web accessibility based on the Web Content Accessibility Guidelines (WCAG) 2.1. It is designed to assist developers, designers, and content creators in identifying and fixing accessibility barriers on their websites and web applications. By using a combination of automated checks and guided manual inspections, this skill helps ensure that digital products are usable by everyone, including people with disabilities. The ultimate goal is to foster a more inclusive and accessible web for all.

## When to Use This Skill
This skill is valuable in a variety of scenarios throughout the product development lifecycle:

*   **During Development:** Integrate accessibility checks directly into your development workflow to catch and fix issues early.
*   **Before a Launch:** Perform a full accessibility audit before deploying a new website, application, or feature.
*   **Auditing Existing Sites:** Regularly assess your existing web properties to ensure they remain compliant and accessible.
*   **Content Creation:** Guide content authors to create accessible content from the start.
*   **Quality Assurance:** As part of the QA process to formalize accessibility testing.
*   **Learning and Training:** As an educational tool to learn more about WCAG and web accessibility best practices.

## Core Capabilities

### 1. Automated Accessibility Scanning
This skill can leverage browser-based tools to run initial automated scans. While automated tools can only detect a subset of WCAG issues (typically around 30-40%), they are excellent for quickly finding common problems.

**How it works:**
The skill will use the browser's developer tools (like Lighthouse in Chrome) to generate an initial accessibility report. It will then parse this report to identify immediate action items.

**Example Command (Conceptual):**
```bash
# This is a conceptual representation of how the skill might trigger a scan.
run-accessibility-scan --url https://example.com --output report.json
```

### 2. Guided Manual Checks (The POUR Principles)
This is the core of the skill. It provides a structured checklist for manual testing, organized by the four principles of WCAG: Perceivable, Operable, Understandable, and Robust.

#### **Principle 1: Perceivable**
Information and user interface components must be presentable to users in ways they can perceive.

*   **1.1 Text Alternatives:**
    *   Check that all non-text content (images, icons) has a text alternative (`alt` attribute).
    *   `alt` text should be descriptive for informative images, and empty (`alt=""`) for decorative images.
    *   Complex images (charts, graphs) should have a long description.
*   **1.2 Time-based Media:**
    *   Check for captions for all prerecorded audio content.
    *   Check for audio descriptions for all prerecorded video content.
*   **1.3 Adaptable:**
    *   Ensure content can be presented in different ways (e.g., simpler layout) without losing information or structure.
    *   Check that the reading and navigation order is logical and intuitive.
    *   Verify that the page is responsive and usable when zoomed up to 400%.
*   **1.4 Distinguishable:**
    *   Check color contrast ratios for text and graphical objects. Use a color contrast checker tool.
    *   Ensure that color is not the only means of conveying information.
    *   Verify that users can control any moving, blinking, or scrolling content.

#### **Principle 2: Operable**
User interface components and navigation must be operable.

*   **2.1 Keyboard Accessible:**
    *   Verify that all functionality is available from a keyboard.
    *   Check for a visible keyboard focus indicator.
    *   Ensure there are no "keyboard traps" where a user can't navigate away from an element.
*   **2.2 Enough Time:**
    *   If there are time limits, ensure the user can pause, stop, or extend them.
*   **2.3 Seizures and Physical Reactions:**
    *   Ensure no content flashes more than three times in any one second period.
*   **2.4 Navigable:**
    *   Check for a "Skip to Main Content" link.
    *   Verify that page titles are descriptive and helpful.
    *   Ensure the purpose of each link can be determined from the link text alone.

#### **Principle 3: Understandable**
Information and the operation of user interface must be understandable.

*   **3.1 Readable:**
    *   The default human language of each page should be declared (e.g., `<html lang="en">`).
*   **3.2 Predictable:**
    *   Ensure that components that have the same functionality are identified consistently.
    *   Navigation mechanisms should be consistent across the site.
*   **3.3 Input Assistance:**
    *   Labels or instructions should be provided for all user input fields.
    *   Error messages should be specific and help the user to correct the error.

#### **Principle 4: Robust**
Content must be robust enough that it can be interpreted reliably by a wide variety of user agents, including assistive technologies.

*   **4.1 Compatible:**
    *   Check for valid HTML to avoid parsing errors.
    *   Ensure that custom controls have appropriate ARIA roles, states, and properties.

### 3. Report Generation
After completing the checks, the skill will help you compile a detailed accessibility report. The report will list all identified issues, their severity, the relevant WCAG success criterion, and recommendations for fixing them.

**Sample Report Snippet:**
```markdown
## Accessibility Audit Report for example.com

### Issue 1: Missing `alt` text for logo

*   **Severity:** High
*   **WCAG Guideline:** 1.1.1 Non-text Content
*   **Description:** The main logo in the header is missing a text alternative. Screen reader users will not know what the image is.
*   **Recommendation:** Add a descriptive `alt` attribute to the `<img>` tag, e.g., `alt="Example Inc. Homepage"`.
```

## Step-by-Step Workflow

1.  **Initiate the Skill:** Start the skill and provide the URL of the web page you want to check.
    *   `> accessibility-checker --url https://example.com`
2.  **Run Automated Scan:** The skill will first perform an automated scan using browser tools and present a summary of potential issues.
3.  **Begin Guided Manual Check:** The skill will then guide you through the manual checklist, organized by the POUR principles.
4.  **Identify and Document Issues:** For each item in the checklist, you will inspect the page and report your findings to the skill. The skill will prompt you for details like the element, the issue, and the relevant WCAG criterion.
5.  **Review and Complete:** Once you have gone through all the checks, the skill will show you a summary of all the issues you have documented.
6.  **Generate Report:** The skill will then generate a complete report in Markdown format, which you can save and share with your team.

## Best Practices

*   **Go Beyond the Checklist:** This skill provides a baseline. Always consider the user experience and context.
*   **Test with Real Users:** Whenever possible, involve people with disabilities in your testing process. Their feedback is invaluable.
*   **Embrace "Shift Left":** Integrate accessibility into your design and development process from the very beginning, rather than treating it as an afterthought.
*   **Document Everything:** Keep detailed notes of your findings and the steps you took to fix them.
*   **Stay Informed:** The world of web accessibility is always evolving. Stay up-to-date with the latest WCAG versions and best practices.

## Examples

### Example 1: Fixing a Missing Text Alternative

**Bad Code (Inaccessible):**
```html
<img src="/images/logo.png">
```

**Good Code (Accessible):**
```html
<img src="/images/logo.png" alt="Example Corporation Logo">
```

### Example 2: Improving Form Accessibility

**Bad Code (Inaccessible):**
```html
<input type="text" placeholder="Your Name">
```

**Good Code (Accessible):**
```html
<label for="name">Your Name</label>
<input type="text" id="name">
```

### Example 3: Ensuring Sufficient Color Contrast

**Bad CSS (Inaccessible):**
```css
.button {
    background-color: #DDDDDD; /* Light Gray */
    color: #EEEEEE; /* Lighter Gray */
}
```

**Good CSS (Accessible):**
```css
.button {
    background-color: #333333; /* Dark Gray */
    color: #FFFFFF; /* White */
}
```

## References

*   [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG21/)
*   [Understanding WCAG 2.1](https://www.w3.org/WAI/WCAG21/Understanding/)
*   [WAI-ARIA Authoring Practices](https://www.w3.org/TR/wai-aria-practices-1.1/)
*   [The A11Y Project](https://www.a11yproject.com/)
*   [WebAIM: Web Accessibility in Mind](https://webaim.org/)
*   [MDN Web Docs: Accessibility](https://developer.mozilla.org/en-US/docs/Web/Accessibility)
