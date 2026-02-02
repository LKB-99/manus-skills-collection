---
name: sleep-analyzer
description: An in-depth analysis of sleep patterns with personalized sleep hygiene recommendations.
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Sleep Analyzer

## Overview
This skill provides a comprehensive analysis of your sleep data, identifying patterns and offering personalized recommendations to improve your sleep quality. By leveraging data from sleep trackers, this skill helps you understand your sleep architecture, including sleep stages, heart rate variability (HRV), and sleep efficiency. It then provides evidence-based sleep hygiene recommendations to help you get more restful and restorative sleep.

## When to Use This Skill
This skill is particularly useful in the following scenarios:

*   **Analyzing Sleep Tracker Data:** You have data from a sleep tracker (like a smartwatch or a dedicated sleep sensor) and want to understand what it means.
*   **Improving Sleep Quality:** You're feeling tired despite getting enough hours of sleep and want to improve the quality of your rest.
*   **Establishing a Healthy Sleep Routine:** You want to create a consistent and effective sleep schedule and bedtime routine.
*   **Investigating Sleep Issues:** You're experiencing sleep disturbances and want to identify potential causes and solutions.
*   **Optimizing Performance:** You want to leverage sleep as a tool to enhance your physical and cognitive performance.

## Core Capabilities

### Sleep Data Analysis
The skill can analyze various sleep metrics to provide a detailed picture of your sleep patterns. This includes:

*   **Sleep Stages:** Understand the time spent in each sleep stage (Light, Deep, REM) and how it compares to recommended ranges. Deep sleep is crucial for physical recovery, while REM sleep is essential for memory consolidation and emotional regulation.
*   **Heart Rate Variability (HRV):** Analyze the variation in time between your heartbeats during sleep. HRV is a key indicator of your body's recovery and readiness. A higher HRV during sleep is generally associated with better rest and recovery.
*   **Sleep Latency:** Determine how long it takes you to fall asleep. A healthy sleep latency is typically between 15 to 20 minutes.
*   **Sleep Efficiency:** Calculate the percentage of time you spend asleep while in bed. A sleep efficiency of 85-95% is considered healthy.
*   **Sleep Disturbances:** Identify the number and duration of awakenings during the night.

### Personalized Sleep Hygiene Recommendations
Based on the analysis of your sleep data, the skill provides tailored recommendations to improve your sleep hygiene. These recommendations cover various aspects of your lifestyle and environment, such as:

*   **Consistent Sleep Schedule:** Establishing a regular sleep-wake cycle, even on weekends.
*   **Optimized Sleep Environment:** Creating a cool, dark, and quiet bedroom.
*   **Relaxing Bedtime Routine:** Implementing calming activities before bed to signal to your body that it's time to sleep.
*   **Dietary and Substance Use Habits:** Understanding how caffeine, alcohol, and late-night meals can impact your sleep.
*   **Exercise and Physical Activity:** Learning how the timing and intensity of exercise can affect your sleep.

## Step-by-Step Workflow

1.  **Provide Sleep Data:** Start by providing your sleep data. You can do this by pointing the skill to a file (e.g., a CSV export from your sleep tracker) or by manually inputting the key metrics.
2.  **Data Analysis:** The skill will process the data, analyzing your sleep stages, HRV, sleep latency, efficiency, and any disturbances.
3.  **Receive Analysis Report:** You will receive a detailed report summarizing the findings from your sleep data analysis. This report will highlight areas where your sleep is strong and where there is room for improvement.
4.  **Get Personalized Recommendations:** Based on the analysis, the skill will generate a set of personalized sleep hygiene recommendations.
5.  **Implement and Track:** Implement the recommended changes to your routine and environment. Continue to track your sleep to see how the changes are impacting your sleep quality over time.

## Best Practices

*   **Be Consistent with Data:** For the most accurate analysis, provide at least a week's worth of consistent sleep data.
*   **Keep a Sleep Diary:** Supplement your sleep tracker data with a sleep diary. Note down factors that might influence your sleep, such as stress levels, meals, and activities.
*   **Focus on Trends:** Don't get too caught up in the data from a single night. Look for trends and patterns over time.
*   **Be Patient:** It can take time to see the results of changes to your sleep hygiene. Be patient and consistent with your efforts.
*   **Consult a Professional:** If you have persistent sleep problems, it's important to consult with a healthcare professional.

## Examples

### Example 1: Analyzing a CSV file of sleep data

**User Request:**
"Analyze my sleep data from the past week. The data is in the file `sleep_data.csv`."

**Manus Action:**
```python
import pandas as pd

df = pd.read_csv('sleep_data.csv')

# --- Perform analysis on the dataframe ---

# Example: Calculate average sleep duration
average_sleep_duration = df['sleep_duration'].mean()

# --- Generate a report ---
report = f"""## Sleep Analysis Report

**Average Sleep Duration:** {average_sleep_duration:.2f} hours

... (rest of the report)
"""

print(report)
```

### Example 2: Getting sleep hygiene recommendations for low deep sleep

**User Request:**
"My sleep tracker shows I'm getting very little deep sleep. What can I do to improve it?"

**Manus Action:**
```
# Recommendations for increasing deep sleep
recommendations = """## Recommendations for Increasing Deep Sleep

1.  **Consistent Sleep Schedule:** Go to bed and wake up at the same time every day, even on weekends.
2.  **Create a Cool, Dark, and Quiet Bedroom:** The ideal temperature for sleep is around 65°F (18°C).
3.  **Avoid Alcohol Before Bed:** Alcohol can suppress deep sleep.
4.  **Get Regular Exercise:** But avoid intense exercise too close to bedtime.
5.  **Take a Warm Bath Before Bed:** A warm bath can help you relax and may increase deep sleep.

"""

print(recommendations)
```

## References

*   [How To Analyse Your Sleep Quality? - The Medical Futurist](https://medicalfuturist.com/analyze-sleep-quality)
*   [5 Things Your Sleep Tracker Is Telling You - Sleep.com](https://www.sleep.com/sleep-tech/what-your-sleep-tracker-tells-you)
*   [Sleep hygiene: Simple practices for better rest - Harvard Health](https://www.health.harvard.edu/staying-healthy/sleep-hygiene-simple-practices-for-better-rest)
