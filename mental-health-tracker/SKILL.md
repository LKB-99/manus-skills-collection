---
name: mental-health-tracker
description: A skill for tracking mental health through daily journaling, mood logging, and guided reflections to identify patterns and promote well-being.
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Mental Health Tracker

## Overview
The Mental Health Tracker skill is designed to help you proactively manage your mental well-being. By leveraging daily journaling, mood tracking, and guided reflection prompts, this skill provides a structured yet flexible system to monitor your emotional state, identify triggers, and recognize patterns in your thoughts and feelings over time. Consistent use of this skill can lead to greater self-awareness, improved emotional regulation, and a more mindful approach to daily life. It serves as a private, personal space for introspection, helping you build a comprehensive record of your mental health journey.

## When to Use This Skill
This skill is particularly useful in the following situations:

- **Daily Self-Reflection:** When you want to establish a routine of checking in with yourself to understand your emotional state.
- **Managing Stress and Anxiety:** When you are experiencing periods of high stress or anxiety and need a tool to externalize and process your thoughts.
- **Identifying Emotional Patterns:** When you want to understand the connections between your daily activities, thoughts, and moods.
- **Preparing for Therapy:** When you want to collect detailed information about your experiences to share with a mental health professional.
- **Tracking Progress:** When you are working on specific mental health goals (e.g., reducing negative self-talk, practicing gratitude) and want to monitor your progress.
- **Promoting Mindfulness:** When you aim to be more present and aware of your inner world on a day-to-day basis.

## Core Capabilities

### 1. Daily Journaling
This capability allows you to create and manage a private journal. You can write free-form entries about your day, thoughts, feelings, and experiences. The skill helps organize these entries by date for easy retrieval and review.

- **Create New Entry:** Prompts you to write about your day.
- **Review Past Entries:** Allows you to look back at entries from a specific date or period.
- **Search Journal:** Provides the ability to search for keywords or themes within your journal entries.

### 2. Mood Logging
Log your mood at any time of the day. This feature helps you build a visual and data-driven overview of your emotional fluctuations. You can add context to each mood entry, such as activities you were engaged in or people you were with.

- **Log Current Mood:** Asks you to rate your mood on a scale (e.g., 1-10) and select descriptive tags (e.g., happy, anxious, productive, tired).
- **Add Context:** Prompts for optional notes about what is influencing your current mood.
- **Visualize Mood Patterns:** (Future capability) Generates simple charts or summaries of your mood trends over a week or month.

### 3. Guided Reflection
For days when you're unsure what to write, the skill provides a set of structured reflection templates and prompts. These are designed to encourage deeper introspection on specific topics like gratitude, challenges, and personal growth.

- **Gratitude Journal:** Prompts you to list things you are thankful for.
- **Challenge & Growth:** Guides you to reflect on a recent challenge and what you learned from it.
- **Future Self:** Encourages you to write about your goals and aspirations.

## Step-by-Step Workflow

Here is a typical workflow for using the Mental Health Tracker skill.

### Step 1: Initialization
To begin, you need to set up the directory structure for your journal. The skill will guide you through this.

1.  **Invoke the skill:** Start by asking Manus to use the `mental-health-tracker` skill.
2.  **Create Project Directory:** The skill will prompt you to create a main directory for your mental health data (e.g., `~/mental-health-journal`).
3.  **Set up Subdirectories:** Inside the main directory, it will create `journal/` and `logs/` folders.
    - `journal/` will store your daily entries.
    - `logs/` will store your mood data in a structured format (e.g., CSV).

```bash
# Example of the setup process guided by the skill
mkdir -p ~/mental-health-journal/journal
mkdir ~/mental-health-journal/logs
touch ~/mental-health-journal/logs/mood_log.csv
echo "timestamp,mood_rating,mood_tags,context" > ~/mental-health-journal/logs/mood_log.csv
```

### Step 2: Making a Daily Journal Entry

1.  **State Your Intent:** Tell Manus, "I want to write in my journal."
2.  **Open the Editor:** The skill will create a new Markdown file for the day's entry, named with the current date (e.g., `~/mental-health-journal/journal/YYYY-MM-DD.md`).
3.  **Write Your Entry:** You can write freely. Alternatively, you can ask for a guided reflection prompt.
    - **Example Request:** "Give me a prompt for my journal entry today."
    - **Skill Response:** "Today's prompt: *Describe a small victory you had today and how it made you feel.*"
4.  **Save the File:** Once you are done writing, the skill saves the content to the daily file.

### Step 3: Logging Your Mood

1.  **State Your Intent:** Tell Manus, "I want to log my mood."
2.  **Provide Mood Data:** The skill will ask for your mood rating and relevant tags.
    - **Skill:** "On a scale of 1 (very negative) to 10 (very positive), how are you feeling?"
    - **You:** "7"
    - **Skill:** "Add some tags to describe your mood (e.g., calm, focused, tired)."
    - **You:** "calm, focused"
    - **Skill:** "Any specific context to add? (Optional)"
    - **You:** "Just finished a productive work session."
3.  **Log the Data:** The skill appends this information as a new row in `~/mental-health-journal/logs/mood_log.csv`.

```csv
# Example of mood_log.csv content
timestamp,mood_rating,mood_tags,context
"2026-02-02T10:00:00Z",7,"calm, focused","Just finished a productive work session."
"2026-02-02T19:00:00Z",4,"tired, anxious","Thinking about tomorrow's workload."
```

### Step 4: Reviewing Your Data

1.  **Request a Review:** Ask Manus to show you your journal entry from a specific day or your mood log from the past week.
    - **Example Request:** "Show me my journal entry from last Monday."
    - **Example Request:** "Summarize my mood logs from this week."
2.  **Retrieve Information:** The skill uses `Read` and `Bash` tools to find the requested files, extract the data, and present it to you in a readable format.

## Best Practices

- **Be Consistent:** Try to make journaling and mood logging a daily habit, even if it's just for a few minutes. Consistency is key to identifying meaningful patterns.
- **Be Honest:** This is your private space. Be as honest as possible with yourself about your feelings and experiences.
- **Use Tags Effectively:** Develop a consistent set of mood tags that make sense to you. This will make it easier to analyze your mood data later.
- **Combine Journaling and Mood Logging:** After logging a particularly strong mood, consider writing a journal entry to explore the reasons behind it in more detail.
- **Review Regularly:** Set aside time each week or month to review your entries and mood logs. This is where you'll gain the most insights.
- **Don't Strive for Perfection:** Some days you'll write a lot, other days just a little. The goal is not to write a masterpiece but to simply connect with yourself.

## Examples

Here are some practical examples of how you might interact with the Mental Health Tracker skill.

### Example 1: A Quick Morning Check-in

**You:** "Good morning. I want to start my day with a quick journal entry and mood log."

**Manus (using the skill):**
1.  Creates `~/mental-health-journal/journal/2026-02-03.md`.
2.  Asks for your mood: "How are you feeling this morning on a scale of 1-10?"
3.  You respond: "An 8."
4.  Asks for tags: "What tags describe this feeling?"
5.  You respond: "Hopeful, energized."
6.  Logs the mood in `mood_log.csv`.
7.  Opens the journal file and asks: "What's on your mind this morning? You can also ask for a gratitude prompt."
8.  You respond: "Give me a gratitude prompt."
9.  Manus provides the prompt and you write your entry.

### Example 2: Processing a Difficult Day

**You:** "I had a really stressful day. I need to write it down."

**Manus (using the skill):**
1.  Opens today's journal file (`.../2026-02-03.md`) or creates it if it doesn't exist.
2.  **Manus:** "I'm here to listen. Write as much as you need to. You can start by describing what happened."
3.  You write a long entry detailing the events and your feelings.
4.  After you finish, Manus asks: "Would you like to log your current mood to capture this feeling?"
5.  You agree and log your mood as a 3, with tags "stressed, overwhelmed, sad."

### Example 3: Using a Reflection Template

**You:** "I want to do a guided reflection on my goals."

**Manus (using the skill):**
1.  Opens today's journal file.
2.  Provides the "Future Self" template:

```markdown
### Future Self Reflection

**1. What is one major goal you want to accomplish in the next year?**

[Your answer here]

**2. What small, actionable step can you take *this week* to move toward that goal?**

[Your answer here]

**3. What potential obstacles might you face, and how can you prepare for them?**

[Your answer here]

**4. Describe how you will feel once you achieve this goal. What will change in your life?**

[Your answer here]
```

3.  You fill out the template, and the skill saves it as part of your daily entry.

## References

- **The Bullet Journal Method by Ryder Carroll:** While not exclusively about mental health, this book provides a powerful framework for intentional living and tracking, which is the foundation of this skill.
- **Atomic Habits by James Clear:** An excellent resource for building the consistent habits required to make this skill effective.
- **Mindful.org:** A great online resource for learning about mindfulness and meditation practices that can complement your journaling.
- **The Artist's Way by Julia Cameron:** Introduces the concept of "Morning Pages," a form of daily free-form writing that aligns well with the journaling capability of this skill.

