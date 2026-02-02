---
name: competitor-analysis
description: A skill for conducting comprehensive market competitor analysis, including pricing, features, and positioning.
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Competitor Analysis

## Overview
This skill enables Manus to perform a thorough competitive analysis of a given market or industry. It systematically gathers, analyzes, and presents data on competitors, focusing on their product features, pricing strategies, market positioning, and customer sentiment. By leveraging this skill, users can gain actionable insights to inform their own business strategy, product development, and marketing efforts. The goal is to provide a clear, data-driven picture of the competitive landscape, highlighting opportunities and threats.

## When to Use This Skill
This skill is particularly useful in the following scenarios:

- **Product Launch:** Before launching a new product or feature, to understand the existing market and identify a unique value proposition.
- **Strategic Planning:** During annual or quarterly strategic planning to assess the competitive landscape and adjust business goals.
- **Market Entry:** When considering entering a new market, to evaluate the viability and identify key players.
- **Pricing Strategy Review:** When a company needs to define or update its pricing models based on competitor pricing.
- **Feature Development:** To prioritize a product roadmap by identifying feature gaps and opportunities relative to competitors.
- **Marketing & Sales:** To equip marketing and sales teams with competitive intelligence for better positioning and objection handling.
- **Investment Analysis:** For investors or analysts looking to evaluate the competitive strength of a company.

## Core Capabilities

### 1. Competitor Identification
- **Market Search:** Utilizes browser and search tools to identify direct and indirect competitors based on keywords, market categories, and industry reports.
- **SERP Analysis:** Analyzes Search Engine Results Pages (SERPs) to find companies ranking for relevant terms.
- **Company Profiling:** Gathers basic information about each identified competitor, such as company size, funding, and founding date.

### 2. Data Collection
- **Website Scraping:** Systematically browses competitor websites to extract information on product features, pricing pages, and marketing copy.
- **Pricing Analysis:** Captures detailed pricing information, including different tiers, billing cycles, and available discounts.
- **Feature Matrix Creation:** Builds a comprehensive matrix comparing the features of the user's product against multiple competitors.
- **Customer Review Analysis:** Gathers and summarizes customer reviews from platforms like G2, Capterra, and Trustpilot to gauge customer sentiment and identify common praises or complaints.

### 3. Market Positioning Analysis
- **SWOT Analysis:** Structures a SWOT (Strengths, Weaknesses, Opportunities, Threats) analysis for key competitors.
- **Value Proposition:** Identifies and articulates the core value proposition and unique selling points (USPs) of each competitor.
- **Target Audience:** Analyzes marketing messaging and content to infer the target customer profile for each competitor.

### 4. Reporting and Visualization
- **Comprehensive Reports:** Generates a detailed report in Markdown format summarizing all findings.
- **Data Tables:** Uses tables to present structured data like pricing and feature comparisons for easy analysis.
- **Summary and Insights:** Provides a high-level summary with key takeaways and strategic recommendations.

## Step-by-Step Workflow

1.  **Define Scope and Objectives:**
    - Start by clarifying the primary goal of the analysis. What specific questions need to be answered?
    - Identify the primary product or service to be benchmarked.
    - List 1-3 primary competitors if known. If not, the skill will identify them.

2.  **Identify Competitors:**
    - Use `search` with queries like `[industry] software`, `alternatives to [product]`, `top [market category] companies`.
    - Use the `browser` to explore industry reports, articles, and review websites (e.g., G2, Capterra).
    - Create a preliminary list of 5-10 direct and indirect competitors.
    - **Action:** `file(action='write', path='competitors.txt', text='Competitor 1
Competitor 2...')`

3.  **Gather Feature Data:**
    - For each competitor, navigate to their website, specifically the 
section.
    - Create a feature matrix in a Markdown file. List features down the first column and competitors across the top row.
    - Use `Y` (Yes), `N` (No), or `P` (Partial) to indicate feature presence.
    - **Template (`features.md`):**
      ```markdown
      | Feature           | Competitor A | Competitor B | Competitor C | Your Product |
      |-------------------|--------------|--------------|--------------|--------------|
      | Feature 1         | Y            | Y            | N            | Y            |
      | Feature 2         | Y            | N            | P            | Y            |
      | Feature 3         | N            | Y            | Y            | N            |
      ```

4.  **Gather Pricing Data:**
    - Navigate to the pricing page of each competitor's website.
    - Capture details for each pricing tier: price, billing cycle (monthly/annual), user limits, feature restrictions, and any free trials.
    - **Template (`pricing.md`):**
      ```markdown
      ### Competitor A Pricing

      | Tier    | Price (Monthly) | Price (Annual) | Key Features                               |
      |---------|-----------------|----------------|--------------------------------------------|
      | Basic   | $29/user/mo     | $24/user/mo    | Core features, 5 projects, 10GB storage    |
      | Pro     | $59/user/mo     | $49/user/mo    | All Basic features, unlimited projects, SSO |
      | Enterprise| Custom          | Custom         | Dedicated support, advanced security       |
      ```

5.  **Analyze Market Positioning:**
    - Review the homepage, "About Us," and solution pages of each competitor.
    - Identify their main marketing slogans, value propositions, and target audience messaging.
    - Use `search` to find news articles, press releases, or analyst reports about the competitors.
    - **Template (`positioning.md`):**
      ```markdown
      ### Competitor A Positioning

      - **Value Proposition:** "The easiest way for teams to collaborate."
      - **Target Audience:** Small to medium-sized businesses, remote teams.
      - **Key Differentiators:** Focus on simplicity and user experience.
      ```

6.  **Synthesize and Report:**
    - Consolidate all the collected data from `features.md`, `pricing.md`, and `positioning.md` into a single report file (`analysis_report.md`).
    - Start with an executive summary of the key findings.
    - Include sections for Feature Comparison, Pricing Analysis, and Market Positioning.
    - Conclude with a SWOT analysis and strategic recommendations.
    - **Action:** `file(action=\'write\', path=\'analysis_report.md\', text=\'# Competitor Analysis Report\n...\[all content]...

## Best Practices

- **Be Systematic:** Follow the step-by-step workflow to ensure all aspects of the analysis are covered consistently for each competitor.
- **Focus on Actionable Insights:** Don't just collect data. Analyze it to find meaningful patterns, gaps, and opportunities. The final report should guide decision-making.
- **Go Beyond the Website:** While websites are a primary source, supplement your analysis with customer reviews, social media mentions, and news articles to get a more holistic view.
- **Use Direct Quotes:** When analyzing positioning and customer sentiment, use direct quotes from the source to support your claims.
- **Stay Objective:** Avoid personal bias. The analysis should be a neutral, fact-based assessment of the competitive landscape.
- **Specify the "As-Of" Date:** The competitive landscape changes quickly. Always mention the date of the analysis to provide context for the findings.

## Examples

### Example 1: Basic Competitor Identification

**User Prompt:** "I'm building a new project management tool. Can you identify the top 3 competitors for Asana?"

**Manus Workflow:**
1.  `search(queries=["alternatives to Asana", "project management software competitors"]`
2.  Analyze search results to identify Trello, Monday.com, and ClickUp as top competitors.
3.  `file(action=\'write\', path=\'competitors.txt\', text=\'Trello
Monday.com
ClickUp

### Example 2: Detailed Feature and Pricing Analysis

**User Prompt:** "Analyze the feature set and pricing for project management tools Trello and Monday.com."

**Manus Workflow:**
1.  `browser(url=\'https://trello.com/pricing\', ...)` and `browser(url=\'https://monday.com/pricing\', ...)` to gather pricing data.
2.  `browser(url=\'https://trello.com/features\', ...)` and `browser(url=\'https://monday.com/features\', ...)` to gather feature data.
3.  Create `pricing.md` and `features.md` files with the collected information, using the templates provided above.
4.  Generate a summary report comparing the two tools based on the findings.

## References

- [G2 - Software Reviews](https://www.g2.com/)
- [Capterra - Find the Right Software](https://www.capterra.com/)
- [Trustpilot - Customer Reviews](https://www.trustpilot.com/)
- [Crunchbase - Company Data](https://www.crunchbase.com/)
- [Ahrefs Blog: How to Conduct a Competitive Analysis](https://ahrefs.com/blog/competitive-analysis/)
