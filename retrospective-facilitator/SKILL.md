---
name: retrospective-facilitator
description: "Facilitates agile retrospectives with templates, analysis, and actionable insights. Use this skill when users want to conduct, facilitate, or improve agile retrospective meetings. Triggers: retrospective, retro, agile, sprint review, post-mortem, team feedback, continuous improvement, retrospectiva, post mortem."
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Retrospective Facilitator

## Overview
This skill is designed to assist agile teams in conducting effective and engaging retrospectives. It provides a structured approach to facilitating these crucial meetings, from setting the stage to generating actionable insights. By leveraging a variety of templates, analysis techniques, and best practices, the Retrospective Facilitator skill helps teams to continuously improve their processes, collaboration, and overall performance. It is particularly useful for Scrum Masters, Agile Coaches, and anyone responsible for leading a team's reflection and improvement efforts.

## Automatic Triggers

**ALWAYS activate this skill when user mentions:**
- Keywords: retrospective, retro, agile, sprint review, post-mortem, team feedback, continuous improvement, retrospectiva, post mortem, facilitate retrospective, run a retro
- Phrases: "facilitate a retrospective", "run a sprint review", "conduct a post-mortem", "gather team feedback", "improve our sprint process", "facilitar uma retrospectiva", "conduzir uma retrospectiva"
- Context: Any discussion about reviewing a past work period (like a sprint or project), identifying areas for improvement, and creating action plans for the team.

**Example user queries that trigger this skill:**
- "We just finished our sprint, I need to run a retrospective."
- "Can you help me facilitate a post-mortem for the recent outage?"
- "Quero fazer a retrospectiva do nosso último projeto."
- "What are some good templates for a team feedback session?"

## When to Use This Skill
This skill is most valuable in the following scenarios:

- **End of a Sprint or Iteration:** The primary use case is to facilitate the retrospective ceremony at the end of a sprint in a Scrum or other agile framework.
- **Project Mid-point or Milestone:** For longer projects, it can be used to conduct a mid-project review to assess what's working and what isn't.
- **After a Major Incident or Event:** When a significant event (positive or negative) occurs, this skill can help the team analyze the situation and learn from it.
- **Team Health Check:** It can be used for periodic team health checks to proactively identify and address any underlying issues.
- **When Team Engagement is Low:** If retrospectives have become stale or unproductive, this skill can help to re-energize the team and make the meetings more engaging and valuable.

## Core Capabilities

### 1. Template-Driven Facilitation
The skill provides a selection of popular and effective retrospective templates to guide the conversation. Each template is designed to focus the team's feedback on different aspects of their work.

**Available Templates:**

- **Start, Stop, Continue:** A simple and powerful technique for identifying what the team should start doing, stop doing, and continue doing.
- **4 L's (Liked, Learned, Lacked, Longed For):** A more reflective template that encourages the team to think about their experiences during the sprint.
- **Sailboat:** A metaphorical exercise where the team identifies the "wind" (what's helping them move forward), the "anchors" (what's holding them back), the "rocks" (risks), and the "island" (their goals).
- **Starfish:** A more granular template that asks the team to consider what they should start doing, stop doing, continue doing, do more of, and do less of.
- **Mad, Sad, Glad:** A template focused on the emotional journey of the team during the sprint, helping to surface and address any frustrations or concerns.

### 2. Actionable Insights Generation
The skill helps to analyze the feedback collected during the retrospective and identify the most important themes and patterns. It then guides the team in creating concrete, actionable improvement items.

**Analysis Techniques:**

- **Affinity Grouping:** The skill can help to group similar feedback items together to identify common themes.
- **Dot Voting:** It can facilitate a dot voting session to help the team prioritize the most important issues to address.
- **Root Cause Analysis (5 Whys):** The skill can guide the team through a "5 Whys" exercise to identify the root cause of a problem.

### 3. Retrospective History and Analysis
The skill can maintain a history of past retrospectives, allowing the team to track their progress over time and identify recurring issues. This can be a powerful tool for driving continuous improvement.

**Historical Data Points:**

- **Action Items:** A record of all action items generated in past retrospectives, including their status (to do, in progress, done).
- **Themes:** A list of the most common themes that have emerged over time.
- **Team Sentiment:** A qualitative analysis of the team's sentiment over time, based on the feedback provided.

## Step-by-Step Workflow

1.  **Initiate the Retrospective:** Start by invoking the skill and providing the name of the team and the sprint number.

    ```bash
    manus retrospective-facilitator --team "Team Phoenix" --sprint 23
    ```

2.  **Select a Template:** The skill will present a list of available templates. Choose the one that best suits the team's needs for this retrospective.

    ```
    Please select a retrospective template:
    1. Start, Stop, Continue
    2. 4 L's (Liked, Learned, Lacked, Longed For)
    3. Sailboat
    4. Starfish
    5. Mad, Sad, Glad
    ```

3.  **Gather Feedback:** The skill will then create a shared document or whiteboard where team members can anonymously add their feedback based on the chosen template. The facilitator should encourage everyone to contribute.

4.  **Facilitate the Discussion:** Once the feedback has been collected, the facilitator will guide the team through a discussion of the items. The skill can help to keep the conversation focused and productive.

5.  **Generate Actionable Insights:** After the discussion, a skill will help the team to identify the most important themes and generate concrete, actionable improvement items. This may involve affinity grouping, dot voting, or root cause analysis.

6.  **Assign Ownership and Due Dates:** For each action item, the team should assign an owner and a due date. The skill will record this information and track the status of each item.

7.  **Close the Retrospective:** At the end of the meeting, the facilitator should summarize the key takeaways and the action items. The skill will then generate a summary of the retrospective and save it to the team's retrospective history.

## Best Practices

- **Create a Safe and Open Environment:** The facilitator should strive to create a psychologically safe environment where team members feel comfortable sharing their honest feedback without fear of blame or retribution.
- **Prime the Team for Participation:** Start the meeting with an icebreaker or a quick check-in to help the team to relax and get into the right mindset for the retrospective.
- **Focus on the "Why," Not the "Who":** The goal of the retrospective is to improve the process, not to place blame. The facilitator should guide the conversation away from personal attacks and towards a constructive discussion of the issues.
- **Make it Action-Oriented:** The retrospective should not be just a "gripe session." The team should leave the meeting with a clear understanding of what they are going to do to improve.
- **Follow Up on Action Items:** The facilitator should ensure that the action items from the retrospective are tracked and followed up on. This will help to ensure that the team is making progress on their improvement goals.
- **Vary the Templates:** To keep the retrospectives fresh and engaging, the facilitator should vary the templates used from time to time.

## Examples

### Example 1: Using the "Start, Stop, Continue" Template

**Facilitator:** "Welcome, everyone, to the retrospective for Sprint 23. For this retrospective, we're going to use the 'Start, Stop, Continue' template. Please take a few minutes to add your feedback to the board."

**Team Member 1:** (Adds a card to the "Start" column) "Start doing more pair programming on complex tasks."

**Team Member 2:** (Adds a card to the "Stop" column) "Stop accepting new work into the sprint after it has started."

**Team Member 3:** (Adds a card to the "Continue" column) "Continue having our daily stand-ups at 9:15 AM."

**(After the discussion and dot voting, the team decides to create the following action item):**

**Action Item:** "Create a formal policy for when new work can be added to a sprint."
**Owner:** "Sarah (Scrum Master)"
**Due Date:** "End of next sprint"

### Example 2: Using the "Sailboat" Template

**Facilitator:** "For this retrospective, we're going to use the 'Sailboat' template. Let's identify the wind in our sails, the anchors holding us back, the rocks we need to watch out for, and the island we're sailing towards."

**Team Member 1:** (Adds a card to the "Wind" section) "Our new CI/CD pipeline is a huge help."

**Team Member 2:** (Adds a card to the "Anchors" section) "We're still spending too much time on manual testing."

**Team Member 3:** (Adds a card to the "Rocks" section) "There's a risk that our main competitor will release a similar feature before we do."

**Team Member 4:** (Adds a card to the "Island" section) "Our goal is to deliver a high-quality, bug-free product that our customers love."

**(The team then discusses these items and creates action items to address the anchors and mitigate the rocks.)**

## References

- [Atlassian: 9 retrospective techniques that won't bore your team to tears](https://www.atlassian.com/blog/teamwork/revitalize-retrospectives-fresh-techniques)
- [Scrum.org: Facilitation Techniques for the Sprint Retrospective](https://www.scrum.org/resources/facilitation-techniques-sprint-retrospective)
- [Parabol: 8 Facilitation Tips for Fun & Effective Retros](https://www.parabol.co/blog/sprint-retrospective-facilitator-pro-tips/)
- [Retrium: 10 Retrospective techniques to try with your agile team](https://www.retrium.com/blog/10-retrospective-techniques-to-try-with-your-agile-team)
- [Miro: Retrospective Templates](https://miro.com/templates/retrospective/)
