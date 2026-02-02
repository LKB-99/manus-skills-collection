---
name: kanban-board
description: Create and manage Kanban boards for visual task management.
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Kanban Board Management

## Overview
This skill empowers Manus to create, manage, and interact with Kanban boards directly within the chat interface. It provides a powerful way to visually organize tasks, track progress, and manage workflows for various projects. By leveraging simple text commands, users can build complex boards, move cards between columns, and get a clear overview of their work, enhancing productivity and project clarity.

## When to Use This Skill
This skill is particularly useful in the following scenarios:

- **Project Management:** Tracking the progress of a software development project, a marketing campaign, or any other multi-step project.
- **Personal Task Management:** Organizing personal to-do lists, daily chores, or long-term goals.
- **Content Creation Pipeline:** Managing the flow of content from idea to publication (e.g., blog posts, videos, social media updates).
- **Agile Development:** Implementing a simple Scrum or Kanban workflow for a development team.
- **Sales Pipeline:** Visualizing the stages of a sales process, from lead generation to closing a deal.
- **Event Planning:** Coordinating the various tasks and deadlines involved in organizing an event.
- **Academic Research:** Structuring the phases of a research project, from literature review to final paper submission.

## Core Capabilities

### 1. Board Creation
Quickly generate a new Kanban board from a template or a custom structure. Boards are stored as Markdown files for easy editing and version control.

**Features:**
- Create boards with default columns (e.g., To Do, In Progress, Done).
- Define custom column names during creation.
- Initialize a board with a set of predefined tasks.

### 2. Card Management
Add, remove, and edit cards on the board. Each card represents a task and can hold details, assignees, and due dates.

**Features:**
- Add a new card to a specific column.
- Edit the description of an existing card.
- Assign users or tags to a card.
- Set a due date for a card.

### 3. Column Operations
Move cards between columns to reflect their current status. This is the core mechanic of the Kanban methodology.

**Features:**
- Move a card from one column to another.
- Drag-and-drop functionality (simulated via commands).
- Archive or remove cards from the board.

### 4. Board Visualization
Display the Kanban board in a clean, readable format within the chat. The skill renders the Markdown file into a visually appealing table structure.

**Features:**
- Show the entire board.
- Filter the view to show only specific columns or cards (e.g., cards assigned to a user).
- Provide a summary of the board (e.g., number of cards per column).

## Step-by-Step Workflow

1.  **Initialization:** Start by creating a new Kanban board.
    - **Command:** `manus kanban create --name "My Project Board" --columns "Backlog,To Do,In Progress,Done"`
    - **Action:** This creates a new file named `my_project_board.md` with the specified columns.

2.  **Adding Tasks:** Populate the board with tasks (cards).
    - **Command:** `manus kanban add --board "My Project Board" --column "To Do" --card "Setup the project repository"`
    - **Action:** Adds a new card to the "To Do" column of the specified board.

3.  **Viewing the Board:** Check the current state of your project.
    - **Command:** `manus kanban show --board "My Project Board"`
    - **Action:** Displays the entire Kanban board in the chat.

4.  **Updating Task Status:** Move cards across columns as work progresses.
    - **Command:** `manus kanban move --board "My Project Board" --card "Setup the project repository" --to "In Progress"`
    - **Action:** Moves the specified card to the "In Progress" column.

5.  **Editing Card Details:** Add more information to a card.
    - **Command:** `manus kanban edit --board "My Project Board" --card "Setup the project repository" --description "Initialize git, create README, and push to remote."`
    - **Action:** Updates the description of the card.

6.  **Completing Tasks:** Move finished tasks to the "Done" column.
    - **Command:** `manus kanban move --board "My Project Board" --card "Setup the project repository" --to "Done"`
    - **Action:** Marks the task as completed.

## Best Practices

- **Keep It Simple:** Don't overcomplicate your board with too many columns. Start with a basic "To Do, In Progress, Done" and add more only when necessary.
- **Limit Work in Progress (WIP):** To improve flow and focus, set a limit on the number of cards that can be in the "In Progress" column at any given time.
- **Be Specific with Card Titles:** A card title should clearly define a single, actionable task.
- **Regularly Review the Board:** Hold regular (e.g., daily or weekly) stand-up meetings to review the board with your team.
- **Use Markdown for Details:** Leverage Markdown formatting within card descriptions to add checklists, links, and other rich details.
- **Automate Repetitive Tasks:** Use Manus to script the creation of recurring tasks or to automatically move cards based on external triggers (e.g., a git commit).
- **Version Control Your Boards:** Since boards are just Markdown files, you can use `git` to track changes, revert to previous states, and collaborate with others.

## Examples

### Example 1: Simple Personal To-Do List

1.  **Create the board:**
    ```bash
    manus kanban create --name "Daily Chores"
    ```
    *(This will use the default columns: To Do, In Progress, Done)*

2.  **Add tasks:**
    ```bash
    manus kanban add --board "Daily Chores" --column "To Do" --card "Buy groceries"
    manus kanban add --board "Daily Chores" --column "To Do" --card "Go to the gym"
    manus kanban add --board "Daily Chores" --column "To Do" --card "Read a chapter of a book"
    ```

3.  **Start a task:**
    ```bash
    manus kanban move --board "Daily Chores" --card "Buy groceries" --to "In Progress"
    ```

4.  **Show the board:**
    ```bash
    manus kanban show --board "Daily Chores"
    ```

    **Output:**
    ```
    | To Do                      | In Progress     | Done |
    |----------------------------|-----------------|------|
    | - Go to the gym            | - Buy groceries |      |
    | - Read a chapter of a book |                 |      |
    ```

### Example 2: Software Development Sprint

1.  **Create a board with custom columns:**
    ```bash
    manus kanban create --name "Sprint-24" --columns "Backlog,Ready for Dev,In Dev,In Review,Done"
    ```

2.  **Add user stories to the backlog:**
    ```bash
    manus kanban add --board "Sprint-24" --column "Backlog" --card "As a user, I want to log in with my email."
    manus kanban add --board "Sprint-24" --column "Backlog" --card "As a user, I want to reset my password."
    ```

3.  **Move a story to development:**
    ```bash
    manus kanban move --board "Sprint-24" --card "As a user, I want to log in with my email." --to "In Dev"
    ```

4.  **Add details to the card:**
    ```bash
    manus kanban edit --board "Sprint-24" --card "As a user, I want to log in with my email." --description "### Acceptance Criteria
- [ ] User can enter email and password.
- [ ] Form validation for email format.
- [ ] Redirect to dashboard on successful login."
    ```

## Templates

### Basic To-Do Board Template

**File:** `basic_todo_template.md`
```markdown
# Kanban Board

| To Do | In Progress | Done |
|---|---|---|
| | | |
```

**Usage:**
```bash
manus file write --path "My_New_Board.md" --text "$(cat basic_todo_template.md)"
```

### Content Creation Pipeline Template

**File:** `content_pipeline_template.md`
```markdown
# Content Pipeline

| Ideas | Writing | Editing | Published |
|---|---|---|---|
| | | | |
```

### Agile Development Template

**File:** `agile_dev_template.md`
```markdown
# Agile Sprint Board

| Product Backlog | Sprint Backlog | In Progress | Code Review | Testing | Done |
|---|---|---|---|---|---|
| | | | | | |
```

## Implementation Details (for Manus Developers)

The skill can be implemented as a set of shell scripts or a Python application that manipulates Markdown files. Here is a conceptual example using shell commands.

**`create` command:**
```bash
#!/bin/bash
BOARD_NAME=$1
COLUMNS=${2:-"To Do,In Progress,Done"}
FILENAME="${BOARD_NAME// /-}.md"

HEADER="| ${COLUMNS//,/" | "} |"
SEPARATOR="|$(printf '---',%.0s $(seq 1 $(echo $COLUMNS | awk -F, '{print NF}')) | sed 's/,/ | /g')|"

echo -e "# $BOARD_NAME\n" > $FILENAME
echo "$HEADER" >> $FILENAME
echo "$SEPARATOR" >> $FILENAME
echo "File $FILENAME created."
```

**`add` command:**
```bash
#!/bin/bash
# This is a simplified example. A robust implementation would use
# more advanced text processing tools like awk or sed.
BOARD_FILE=$1
COLUMN_NAME=$2
CARD_TEXT=$3

# Logic to find the correct column and add the card text
# For example, using awk to insert text into a specific column
awk -v col="$COLUMN_NAME" -v card="$CARD_TEXT" 'BEGIN{FS=OFS="|"}
{
    if(NR==1){for(i=1;i<=NF;i++){if($i ~ col){c=i;break}}}
    if(NR==3){$c = $c " - " card " <br> "}
    print
}' $BOARD_FILE > tmp && mv tmp $BOARD_FILE
```

## References

- [1] [Atlassian Kanban Guide](https://www.atlassian.com/agile/kanban)
- [2] [Kanban Explained in 10 Minutes](https://www.youtube.com/watch?v=iVaFqQ2R4o4)
- [3] [Personal Kanban: Mapping Work | Navigating Life](https://www.amazon.com/Personal-Kanban-Mapping-Navigating-Life/dp/0982866309)
- [4] [Markdown Tables Generator](https://www.tablesgenerator.com/markdown_tables)

This skill provides a flexible and developer-friendly way to bring the power of Kanban into any workflow, directly from the command line.













































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																															'
