---
name: habit-tracker
description: "A comprehensive skill for tracking habits, maintaining streaks, and using gamification to stay motivated. Use this skill when users want to track daily, weekly, or monthly habits, build routines, or monitor personal growth. Triggers: habit tracker, track habits, new habit, daily routine, weekly goal, build habit, streak, gamification, monitor progress, rastreador de hábitos, novo hábito, rotina diária, meta semanal, criar hábito."
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Habit Tracker: Gamified Habit Tracking System

## Overview
This skill provides a robust system for tracking daily, weekly, or monthly habits. It is designed to help users build and maintain positive routines by incorporating streaks and gamification elements. Users can define habits, log their progress, visualize their consistency, and receive motivational feedback. The skill leverages simple file-based storage, making it transparent and easily manageable. It is ideal for anyone looking to instill discipline, track personal growth, or simply organize their daily routines in a more engaging way.

## Automatic Triggers

**ALWAYS activate this skill when user mentions:**
- Keywords: habit tracker, track habits, new habit, daily routine, weekly goal, build habit, streak, gamification, monitor progress, rastreador de hábitos, novo hábito, rotina diária, meta semanal, criar hábito, acompanhar hábito
- Phrases: "create a new habit", "track my reading habit", "start a daily routine", "how's my habit streak?", "criar um novo hábito", "acompanhar meu hábito de leitura", "iniciar uma rotina diária"
- Context: Any discussion about creating, tracking, or maintaining personal habits, routines, or goals.

**Example user queries that trigger this skill:**
- "I want to start tracking my water intake."
- "Can you help me build a new habit for studying?"
- "Quero criar o hábito de meditar todos os dias."
- "Como está minha sequência no hábito de exercícios?"

## When to Use This Skill
This skill is particularly useful in the following scenarios:

- **Building New Habits:** When you want to start a new positive habit, such as exercising, reading, or meditating, and need a system to keep you accountable.
- **Breaking Bad Habits:** To track your progress in avoiding a bad habit, like smoking or excessive social media use.
- **Improving Consistency:** If you are already performing a habit but struggle with consistency, the streak and gamification features can provide extra motivation.
- **Personal Growth:** For individuals focused on self-improvement who want to quantify their efforts and see tangible proof of their progress over time.
- **Project Management:** To track recurring tasks or milestones within a larger project, ensuring that small, consistent steps are being taken.
- **Health and Wellness:** For tracking health-related goals, such as drinking enough water, taking vitamins, or following a specific diet plan.

## Core Capabilities

### 1. Habit Management
- **Create Habits:** Define new habits with a name, description, and frequency (daily, weekly, etc.).
- **List Habits:** View all the habits you are currently tracking.
- **Delete Habits:** Remove habits that are no longer relevant.

### 2. Progress Logging
- **Log Completion:** Mark a habit as completed for the current day or a specific date.
- **View History:** See the entire history of a specific habit, including all logged completions.

### 3. Streak Tracking
- **Current Streak:** The skill automatically calculates and displays the number of consecutive days (or periods) a habit has been completed.
- **Longest Streak:** It also keeps track of the longest streak ever achieved for each habit, serving as a personal record to beat.

### 4. Gamification and Motivation
- **Points System:** Earn points for completing habits and maintaining streaks.
- **Leveling System:** Accumulate points to level up, providing a sense of progression.
- **Achievements:** Unlock achievements for reaching milestones (e.g., "7-Day Streak," "Perfect Month").

### 5. Data and Visualization
- **Data Storage:** All habit data is stored in a simple, human-readable JSON file (`habits.json`), allowing for easy inspection and manual editing if needed.
- **Progress Summary:** Generate a summary report of your progress across all habits.
- **(Future) Visualization:** Future versions could include generating charts or graphs to visualize consistency over time.

## Step-by-Step Workflow

This workflow guides you through setting up and using the habit tracker skill.

### Step 1: Initialization
To get started, you need to create the main data file. The skill will automatically handle this if the file doesn't exist.

1.  **Action:** The first time you try to add a habit, the skill will create a `habits.json` file in your home directory.
2.  **File Structure:** The `habits.json` file will have the following structure:

    ```json
    {
        "user_level": 1,
        "user_points": 0,
        "habits": []
    }
    ```

### Step 2: Creating a New Habit

1.  **Command:** Use a clear command to express your intent.
    *   `"Create a new daily habit called 'Read for 30 minutes'"`
    *   `"Add a weekly habit: 'Go to the gym'"`

2.  **Execution:** The skill will add a new entry to the `habits` array in `habits.json`.

    ```json
    {
        "name": "Read for 30 minutes",
        "description": "Read a book for at least 30 minutes every day.",
        "frequency": "daily",
        "created_at": "2026-02-02T10:00:00Z",
        "history": [],
        "current_streak": 0,
        "longest_streak": 0
    }
    ```

### Step 3: Logging Habit Completion

1.  **Command:** Log your progress daily.
    *   `"I completed my habit 'Read for 30 minutes' today."`
    *   `"Log 'Go to the gym' for today."`

2.  **Execution:** The skill finds the specified habit and adds a new entry to its `history`.
    *   It checks the date to see if it continues a streak.
    *   If the streak is continued, `current_streak` is incremented.
    *   If `current_streak` surpasses `longest_streak`, the latter is updated.
    *   Points are awarded.

    ```json
    "history": [
        {
            "date": "2026-02-02T12:00:00Z",
            "points_earned": 10
        }
    ]
    ```

### Step 4: Viewing Your Progress

1.  **Command:** Check your status at any time.
    *   `"Show me my current habits."`
    *   `"What is my streak for 'Read for 30 minutes'?"`
    *   `"Give me a summary of my habit progress."`

2.  **Execution:** The skill reads the `habits.json` file and presents the information in a clear, readable format.

    **Example Output for "Show me my current habits":**

    ```
    Here are your current habits:

    1. Read for 30 minutes (Daily)
       - Current Streak: 1 day
       - Longest Streak: 1 day

    2. Go to the gym (Weekly)
       - Current Streak: 0 weeks
       - Longest Streak: 0 weeks
    ```

### Step 5: Handling Missed Days

The skill automatically detects a broken streak. If you log a habit after missing one or more days (based on its frequency), the `current_streak` will be reset to 1.

## Best Practices

- **Be Specific:** When creating a habit, be as specific as possible. Instead of "Exercise," use "30 minutes of cardio." This clarity removes ambiguity and makes it easier to know if you've completed the task.
- **Start Small:** Don't try to build ten new habits at once. Start with 1-3 core habits. Once they are well-established, you can add more.
- **Log Consistently:** Make it a part of your daily routine to log your habits. The best time is right after you've completed the habit or at the end of the day.
- **Don't Break the Chain:** The core motivational principle is to not break your streak. Visualize the chain of completions and focus on adding one more link each day.
- **Review Regularly:** Once a week, review your progress. See which habits you are sticking with and which ones you are struggling with. Adjust as necessary.
- **Manual Edits:** Since the data is in a simple JSON file, you can manually correct mistakes. For example, if you forgot to log a habit on a specific day, you can add the entry yourself. Be honest with yourself!

## Examples

Here are some practical examples of how to interact with the skill.

### Example 1: Setting Up and Tracking a Morning Routine

**User Goal:** Create a consistent morning routine.

1.  **Create Habits:**
    *   `"Create a daily habit: 'Meditate for 10 minutes'"`
    *   `"Add a daily habit: 'Drink a glass of water after waking up'"`
    *   `"New daily habit: 'Plan my day'"`

2.  **Log Completions (Next Morning):**
    *   `"I drank a glass of water."`
    *   `"I meditated for 10 minutes."`
    *   `"I just finished planning my day."`

3.  **Check Progress (End of the Week):**
    *   `"Show me a summary of my habits."`

    **Expected Output:**

    ```
    Habit Summary:

    - Meditate for 10 minutes (Daily)
      - Current Streak: 5 days
      - Longest Streak: 5 days
      - Completions this week: 5/7

    - Drink a glass of water after waking up (Daily)
      - Current Streak: 7 days
      - Longest Streak: 7 days
      - Completions this week: 7/7

    - Plan my day (Daily)
      - Current Streak: 2 days
      - Longest Streak: 3 days
      - Completions this week: 6/7

    Your current level is 2 (+150 points).
    Achievement Unlocked: 7-Day Streak (Drink a glass of water)!
    ```

### Example 2: Tracking a Fitness Goal

**User Goal:** Exercise three times a week.

1.  **Create Habit:**
    *   `"Add a new habit: 'Go to the gym'. Set the frequency to 3 times per week."`

2.  **Log Completions:**
    *   (Monday) `"I went to the gym today."`
    *   (Wednesday) `"Logged my gym session."`
    *   (Friday) `"Completed 'Go to the gym'."`

3.  **Check Progress:**
    *   `"How am I doing with my gym habit?"`

    **Expected Output:**
    ```
    Habit: Go to the gym (3 times per week)
    - Completions this week: 3/3
    - Weekly Goal Met!
    - Current Streak: 1 week
    ```

## Templates for Implementation

Below are some code templates and structures to help in the development of this skill.

### `habits.json` Template

This is the main data file. It should be stored at `/home/ubuntu/habits.json`.

```json
{
  "user_level": 1,
  "user_points": 0,
  "achievements": [],
  "habits": [
    {
      "name": "Read for 20 minutes",
      "description": "Read a non-fiction book.",
      "frequency": "daily",
      "created_at": "2026-01-15T09:00:00Z",
      "history": [
        {
          "date": "2026-01-15T20:00:00Z",
          "points_earned": 10
        },
        {
          "date": "2026-01-16T20:05:00Z",
          "points_earned": 15
        }
      ],
      "current_streak": 2,
      "longest_streak": 2
    },
    {
      "name": "Weekly Review",
      "description": "Review the past week and plan the next one.",
      "frequency": "weekly",
      "created_at": "2026-01-10T12:00:00Z",
      "history": [],
      "current_streak": 0,
      "longest_streak": 0
    }
  ]
}
```

### Python Logic for Streak Calculation (Pseudo-code)

This logic would be part of the "log completion" function.

```python
import json
from datetime import datetime, timedelta

def log_habit_completion(habit_name):
    with open('habits.json', 'r+') as f:
        data = json.load(f)

        habit = find_habit(data['habits'], habit_name)
        if not habit:
            print("Habit not found.")
            return

        today = datetime.now().date()

        # Avoid duplicate logs on the same day
        if habit['history'] and datetime.fromisoformat(habit['history'][-1]['date']).date() == today:
            print(f"Habit '{habit_name}' already logged for today.")
            return

        # Check for streak
        is_streak_continued = False
        if habit['history']:
            last_log_date = datetime.fromisoformat(habit['history'][-1]['date']).date()
            if today == last_log_date + timedelta(days=1):
                habit['current_streak'] += 1
                is_streak_continued = True
            else:
                habit['current_streak'] = 1 # Streak is broken
        else:
            habit['current_streak'] = 1 # First log

        # Update longest streak
        if habit['current_streak'] > habit['longest_streak']:
            habit['longest_streak'] = habit['current_streak']

        # Add points
        points = 10
        if is_streak_continued:
            points += habit['current_streak'] * 2 # Bonus for longer streaks
        data['user_points'] += points

        # Add to history
        habit['history'].append({
            "date": datetime.now().isoformat(),
            "points_earned": points
        })

        # Check for level up
        # ... (logic for leveling)

        # Save data
        f.seek(0)
        json.dump(data, f, indent=2)
        f.truncate()

        print(f"Successfully logged '{habit_name}'. Current streak: {habit['current_streak']} days.")

```

## References

- **[1] Atomic Habits by James Clear:** A foundational book on habit formation that inspired many of the principles in this skill. [https://jamesclear.com/atomic-habits](https://jamesclear.com/atomic-habits)
- **[2] The Power of Habit by Charles Duhigg:** Explores the science behind why we do what we do in life and business. [https://charlesduhigg.com/the-power-of-habit/](https://charlesduhigg.com/the-power-of-habit/)
- **[3] Gamification on Wikipedia:** For more information on the theory and application of game-design elements in non-game contexts. [https://en.wikipedia.org/wiki/Gamification](https://en.wikipedia.org/wiki/Gamification)
- **[4] JSON Data Interchange Format:** Official website for the JSON standard used for data storage in this skill. [https://www.json.org/](https://www.json.org/)

