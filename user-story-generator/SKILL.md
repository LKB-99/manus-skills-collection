---
name: user-story-generator
description: A skill to generate comprehensive user stories and acceptance criteria for agile development.
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# User Story Generator

## Overview
This skill is designed to assist software developers, product managers, and agile teams in generating well-structured and detailed user stories. A user story is a concise, plain-language description of a feature told from the perspective of the person who desires the new capability, usually a user or customer of the system. This skill helps in defining the "who," "what," and "why" of a requirement in a simple, yet powerful way. By providing a structured template, it ensures that all essential components of a user story, including acceptance criteria, are captured, leading to clearer requirements and smoother development cycles. This skill is not just a simple template filler; it leverages AI to understand the context of the feature and suggest relevant details, potential edge cases, and comprehensive acceptance criteria. It aims to be a collaborative partner in the requirement definition process, reducing the cognitive load on the product owner and the development team.

## When to Use This Skill
This skill is particularly useful in the following scenarios:

- **Initial Requirement Gathering:** When you need to translate high-level stakeholder needs and ideas into actionable and well-defined development items. The skill can take a vague feature request and help structure it into a formal user story.
- **Backlog Grooming and Refinement:** To add detail, clarity, and precision to existing user stories in the product backlog. It can help break down large, epic-level stories into smaller, more manageable ones.
- **Sprint Planning Meetings:** To ensure that the entire team has a clear and shared understanding of what needs to be built during an upcoming sprint. Using this skill during planning can help uncover hidden assumptions and dependencies.
- **Agile Coaching and Training:** To teach and enforce best practices for writing effective user stories. New team members or those new to agile can use this skill as a learning tool.
- **Solo Development Projects:** To maintain a structured and disciplined approach to building features even when working alone. It helps in thinking through the requirements from a user's perspective.
- **Product Discovery and Prototyping:** To quickly explore and define new product features and capabilities. The skill can generate multiple story variations to help in brainstorming and validating ideas.
- **API and Backend Development:** While user stories are often associated with UI features, this skill can be adapted to define requirements for backend services, APIs, and system-level functionalities by focusing on the "user" as another system or a developer.

## Core Capabilities

### 1. Structured User Story Generation
The primary capability of this skill is to generate a complete user story based on a simple prompt or a set of keywords. The skill will guide you to define the user role, the desired action, and the ultimate benefit.

**Standard Template (As a... I want to... so that...):**
```
As a [user role],
I want to [perform an action or achieve a goal],
so that I can [realize a benefit or value].
```

### 2. Comprehensive Acceptance Criteria Formulation
A user story is incomplete without clear, testable acceptance criteria. This skill excels at generating detailed acceptance criteria using the Gherkin syntax (Given/When/Then), which is widely used in Behavior-Driven Development (BDD).

**Gherkin-based Template:**
```markdown
**Acceptance Criteria:**

*   **Scenario 1:** [Clear and concise description of the scenario]
    *   **Given** [a specific precondition or context]
    *   **And** [another precondition, if necessary]
    *   **When** [a specific action is performed by the user or system]
    *   **Then** [an expected and observable outcome occurs]
    *   **And** [another expected outcome, if necessary]

*   **Scenario 2: (Edge Case)** [Description of an alternative or error scenario]
    *   **Given** [a different precondition]
    *   **When** [a different action is performed]
    *   **Then** [a different expected outcome is observed, e.g., an error message]
```

### 3. Adherence to Agile Principles
The skill is built upon industry best practices for writing effective user stories, most notably the **INVEST** principle. It encourages the creation of high-quality user stories that are:
- **I**ndependent: Can be developed and delivered separately.
- **N**egotiable: Not a strict contract, but a starting point for discussion.
- **V**aluable: Delivers clear value to the end-user or stakeholder.
- **E**stimable: Can be reasonably estimated by the development team.
- **S**mall: Sized appropriately to be completed within a single sprint.
- **T**estable: Has clear acceptance criteria that can be verified.

### 4. Template Customization and Expansion
The skill is not limited to a single template. It can adapt and provide additional sections to a user story as needed, such as:
- **Notes & Assumptions:** To capture important context or constraints.
- **Out of Scope:** To explicitly define what is not being built.
- **UI/UX Considerations:** To provide guidance on design and user experience.
- **Technical Notes:** For implementation details or dependencies.

## Step-by-Step Workflow

1.  **Initiate the Skill:** Start by calling the `user-story-generator` skill.
2.  **Provide a Feature Prompt:** Give the skill a high-level description of the feature you want to build. For example: `"I need a login page for my e-commerce website."`
3.  **Define the User Role:** The skill will ask you to specify the user role. For the login page example, the role would be `"registered customer"`.
4.  **Specify the Action and Benefit:** The skill will then help you articulate the action and the benefit. For instance, `"I want to log in with my email and password so that I can access my account and purchase history."`
5.  **Generate the Core User Story:** The skill will combine this information into a well-formatted user story.
6.  **Brainstorm Acceptance Criteria:** The skill will then prompt you to think about different scenarios. It might ask questions like:
    *   `"What should happen if the user enters the correct credentials?"`
    *   `"What should happen if the password is incorrect?"`
    *   `"What about if the user's account is locked?"`
    *   `"Is there a 'Forgot Password' link?"`
7.  **Formulate and Refine Criteria:** Based on your answers, the skill will generate detailed acceptance criteria in the Given/When/Then format for each scenario.
8.  **Add Supplementary Details:** The skill will ask if you want to add any other sections like 'Notes', 'UI/UX Considerations', or 'Technical Notes'.
9.  **Review and Finalize:** The skill will present the complete user story with all its components. You can then review, edit, and finalize it.
10. **Export or Copy:** The final output is a clean, well-formatted Markdown text that you can directly copy into your project management tool or save as a document.

## Best Practices

- **Be Specific in Your Prompts:** The more context you provide to the skill, the better and more relevant the generated story and criteria will be. Instead of `"user profile"`, try `"As a user, I want to be able to edit my profile information, including my name, email, and profile picture."`
- **Collaborate with the Skill:** Treat the skill as a brainstorming partner. Use its questions and suggestions to think through the feature from all angles.
- **Focus on Value:** Always keep the `"so that..."` part of the story in mind. It represents the value proposition of the feature and should guide the development effort.
- **Keep Stories Small:** If the generated story seems too large or complex, use the skill to help you break it down into smaller, more manageable stories.
- **Review with the Team:** The generated user story is a starting point for a conversation. Always review it with the entire development and product team to ensure a shared understanding.
- **Don't Forget Non-Functional Requirements:** Use the 'Notes' or 'Technical Notes' sections to capture important non-functional requirements (NFRs) such as performance, security, or accessibility.

## Examples

### Example 1: E-commerce Search Functionality

**User Prompt:** `"Generate a user story for a product search feature on an e-commerce site."`

**Generated SKILL.md Output:**

```markdown
**User Story**

**As a** shopper,
**I want to** search for products using keywords,
**so that I can** quickly find the items I am interested in purchasing.

---

**Acceptance Criteria:**

*   **Scenario 1: Successful Search with Multiple Results**
    *   **Given** I am on the homepage.
    *   **When** I enter the keyword `"laptop"` into the search bar and press Enter.
    *   **Then** I should be redirected to a search results page.
    *   **And** the page should display a list of products related to `"laptop"`.
    *   **And** the search term `"laptop"` should be visible in the search bar on the results page.

*   **Scenario 2: Search with No Results**
    *   **Given** I am on the homepage.
    *   **When** I enter a non-existent product keyword like `"xyzabc"` into the search bar and press Enter.
    *   **Then** the search results page should display a message indicating `"No products found for 'xyzabc'"`.
    *   **And** the page might suggest alternative search terms or categories.

*   **Scenario 3: Search with a Single Result**
    *   **Given** I am on the homepage.
    *   **When** I enter a unique product SKU like `"MBP-M3-2024"` into the search bar.
    *   **Then** the search results page should display the single product matching that SKU.

---

**UI/UX Considerations:**
- The search bar should be prominently displayed on all main pages.
- An autocomplete or search suggestion feature should be considered to help users.
- Search results should include a product image, name, price, and a short description.

**Technical Notes:**
- The search functionality should be case-insensitive.
- The search algorithm should handle partial matches and typos gracefully.
- The performance of the search should be optimized to return results in under 500ms.
```

### Example 2: API Endpoint for User Data

**User Prompt:** `"Create a story for a backend API that provides user details."`

**Generated SKILL.md Output:**

```markdown
**User Story**

**As a** client application developer,
**I want to** make a GET request to a `/api/users/{id}` endpoint,
**so that I can** retrieve the profile information for a specific user.

---

**Acceptance Criteria:**

*   **Scenario 1: Successfully Retrieve a User**
    *   **Given** a user with ID `"12345"` exists in the database.
    *   **When** I send a GET request to `/api/users/12345` with a valid authentication token.
    *   **Then** the API should return a `200 OK` status code.
    *   **And** the response body should be a JSON object containing the user's id, name, email, and join_date.
    *   **And** the response body should NOT contain sensitive information like the user's password hash.

*   **Scenario 2: User Not Found**
    *   **Given** a user with ID `"99999"` does not exist in the database.
    *   **When** I send a GET request to `/api/users/99999`.
    *   **Then** the API should return a `404 Not Found` status code.

*   **Scenario 3: Unauthorized Access**
    *   **Given** a user with ID `"12345"` exists.
    *   **When** I send a GET request to `/api/users/12345` without a valid authentication token.
    *   **Then** the API should return a `401 Unauthorized` status code.

---

**Technical Notes:**
- The endpoint must be protected and require authentication.
- The JSON response structure should be documented in the API documentation.
- Consider implementing rate limiting to prevent abuse.
- The endpoint should be versioned (e.g., `/api/v1/users/{id}`).
```

## References

- [User Stories - Atlassian Agile Coach](https://www.atlassian.com/agile/project-management/user-stories)
- [INVEST in Good Stories, and SMART Tasks - Agile For All](https://www.agileforall.com/2010/09/invest-in-good-stories-and-smart-tasks/)
- [The Gherkin Language - Cucumber Documentation](https://cucumber.io/docs/gherkin/reference/)
- [Mike Cohn's User Story Blog](https://www.mountaingoatsoftware.com/blog)

## Advanced Usage

### 1. Generating Epics and Breaking Them Down

While this skill is primarily for user stories, it can be used to define larger pieces of functionality, known as epics. An epic is a large body of work that can be broken down into a number of smaller stories. You can start by defining the epic and then use the skill iteratively to break it down.

**User Prompt for an Epic:** `"Generate an epic for a new user profile management feature."`

**Generated Epic:**

```markdown
**Epic:** User Profile Management

**Description:** Provide users with the ability to view, edit, and manage their profile information, as well as control their account settings and preferences.

**Child Stories (to be generated):**
- Story 1: View Profile Information
- Story 2: Edit Basic Profile Information (Name, Bio)
- Story 3: Change Profile Picture
- Story 4: Update Email Address
- Story 5: Change Password
- Story 6: Manage Notification Preferences
- Story 7: View Order History
- Story 8: Delete Account
```

You can then take each of these child story titles and use the skill to generate a full user story with acceptance criteria for each one.

### 2. Handling Different User Roles (Personas)

In many applications, you have different types of users with different needs and permissions. This skill can help you tailor user stories for each specific persona.

**Example with Multiple Personas:**

**User Prompt:** `"Generate a user story for a content publishing feature on a blog platform, considering both an 'Author' and an 'Editor' role."`

**Generated Story for 'Author':**

```markdown
**User Story**

**As an** Author,
**I want to** write and submit a blog post for review,
**so that I can** share my content with the world.

**Acceptance Criteria:**
*   **Scenario 1: Successful Draft Submission**
    *   **Given** I am logged in as an Author.
    *   **When** I create a new post, fill in the title and content, and click "Submit for Review".
    *   **Then** the post status should change to "Pending Review".
    *   **And** an Editor should be notified.
```

**Generated Story for 'Editor':**

```markdown
**User Story**

**As an** Editor,
**I want to** review, approve, and publish submitted blog posts,
**so that I can** ensure the quality and consistency of the content on our platform.

**Acceptance Criteria:**
*   **Scenario 1: Approve and Publish a Post**
    *   **Given** I am logged in as an Editor and there is a post with "Pending Review" status.
    *   **When** I review the post, make any necessary edits, and click "Approve and Publish".
    *   **Then** the post should become publicly visible on the blog.
    *   **And** the post status should change to "Published".
    *   **And** the original Author should be notified.
```

### 3. Incorporating Non-Functional Requirements (NFRs)

User stories often focus on functionality, but non-functional requirements (like performance, security, and usability) are equally important. The skill can help you explicitly capture these as part of the story or its acceptance criteria.

**Example with NFRs:**

**User Prompt:** `"Generate a user story for an image upload feature, and make sure it's secure and performs well."`

**Generated Story with NFRs:**

```markdown
**User Story**

**As a** user,
**I want to** upload a profile picture,
**so that I can** personalize my account.

**Acceptance Criteria:**
*   **Scenario 1: Successful Image Upload**
    *   **Given** I am on my profile settings page.
    *   **When** I select a valid image file (JPG, PNG) under 5MB and click "Upload".
    *   **Then** my new profile picture should be displayed on my profile.
    *   **And** the upload process should complete in under 3 seconds on a standard internet connection.

*   **Scenario 2: Invalid File Type**
    *   **Given** I am on my profile settings page.
    *   **When** I try to upload a file that is not a JPG or PNG (e.g., a PDF).
    *   **Then** I should see an error message: "Invalid file type. Please upload a JPG or PNG."

**Technical Notes (NFRs):**
- **Security:** All uploaded files must be scanned for malware. The upload endpoint must be protected against Cross-Site Scripting (XSS) and other vulnerabilities.
- **Performance:** Images should be automatically resized and compressed on the server to optimize loading times across the application.
- **Accessibility:** The upload button and any error messages must be accessible to screen readers.
```

## Common Pitfalls and How to Avoid Them

1.  **Making Stories Too Big (Epics in Disguise):**
    *   **Pitfall:** Writing a story that is too large to be completed in a single sprint. For example: `"As a user, I want to manage my entire account."`
    *   **How to Avoid:** Use the skill to break down large features into smaller, more focused stories. The `user-story-generator` can help you identify the individual components of a larger feature.

2.  **Forgetting the "So That" Clause:**
    *   **Pitfall:** Focusing only on the "what" and not the "why." This leads to a lack of clarity about the value of the feature.
    *   **How to Avoid:** The skill's template enforces the inclusion of the `"so that..."` clause. Always take the time to articulate the benefit to the user.

3.  **Writing Vague Acceptance Criteria:**
    *   **Pitfall:** Acceptance criteria that are not specific or testable. For example: `"The login page should work correctly."`
    *   **How to Avoid:** Use the Gherkin (Given/When/Then) format that the skill provides. This structure forces you to think about specific preconditions, actions, and observable outcomes.

4.  **Treating User Stories as Contracts:**
    *   **Pitfall:** Believing that a user story is a fixed requirement that cannot be changed. This stifles collaboration and adaptation.
    *   **How to Avoid:** Remember that user stories are "negotiable." Use the generated story as a starting point for a conversation with the development team. The story is a promise of a conversation, not a contract.

5.  **Ignoring Non-Functional Requirements:**
    *   **Pitfall:** Focusing solely on what the system does, and not on how well it does it.
    *   **How to Avoid:** Use the `Technical Notes` or `UI/UX Considerations` sections of the skill's template to explicitly capture NFRs like performance, security, and accessibility.

## Integrating with Project Management Tools

The output of the `user-story-generator` skill is in clean, standard Markdown. This makes it incredibly easy to integrate with most modern project management and development tools.

### Jira

1.  **Create a New Issue:** In your Jira project, click the "Create" button.
2.  **Select Issue Type:** Choose "Story" as the issue type.
3.  **Copy and Paste:** Copy the entire generated Markdown output from the skill.
4.  **Paste into Description:** Paste it directly into the "Description" field of the Jira issue. Jira's editor supports Markdown, so the formatting (headings, lists, code blocks) will be preserved.
5.  **Fill in Summary:** Use the user story's title (e.g., `"User Story: E-commerce Search Functionality"`) as the "Summary" of the Jira issue.

### Trello

1.  **Create a New Card:** In your Trello board, create a new card for the user story.
2.  **Use Title:** The title of the card can be the short user story itself (e.g., `"As a shopper, I want to search for products..."`).
3.  **Paste in Description:** Open the card and paste the full Markdown output into the "Description" field. Trello also renders Markdown beautifully.

### GitHub Issues

1.  **Create a New Issue:** In your GitHub repository, go to the "Issues" tab and click "New issue".
2.  **Title:** Use a descriptive title for the issue.
3.  **Paste in Comment:** Paste the full Markdown output into the main comment box. GitHub has excellent Markdown support.
4.  **Use Labels:** You can use labels like `user-story`, `feature`, or `epic` to categorize the issue.

## Glossary of Terms

- **User Story:** A short, simple description of a feature told from the perspective of the person who desires the new capability.
- **Epic:** A large body of work that can be broken down into a number of smaller stories.
- **Acceptance Criteria:** A set of predefined requirements that must be met for a user story to be considered "done."
- **Gherkin:** A business-readable, domain-specific language that lets you describe software's behavior without detailing how that behavior is implemented. It uses the `Given/When/Then` syntax.
- **INVEST:** An acronym that stands for the attributes of a good quality user story: Independent, Negotiable, Valuable, Estimable, Small, and Testable.
- **Persona:** A fictional character created to represent a user type that might use a site, brand, or product in a similar way.
- **Non-Functional Requirement (NFR):** A requirement that specifies criteria that can be used to judge the operation of a system, rather than specific behaviors (e.g., performance, security).
