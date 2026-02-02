---
name: social-media-scheduler
description: Schedule and automate social media posts with metrics analysis.
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Social Media Scheduler & Automation

## Overview
This skill empowers Manus to act as a comprehensive social media management assistant. It provides a robust framework for planning, scheduling, and automatically publishing content across various social media platforms. Beyond simple scheduling, the skill integrates capabilities for performance analysis, enabling Manus to track key metrics, generate reports, and refine social media strategy based on data-driven insights. It is designed for marketers, content creators, and businesses looking to streamline their social media workflow, maintain a consistent online presence, and optimize their engagement strategies without manual intervention for every post.

## When to Use This Skill
This skill is particularly useful in the following scenarios:

- **Automating Repetitive Posting:** When you need to schedule a high volume of posts across multiple platforms like Twitter, LinkedIn, Facebook, and Instagram.
- **Campaign Management:** To plan and execute a multi-platform social media campaign over a specific period, ensuring timely delivery of all content.
- **Content Curation and Scheduling:** When you have a batch of content (articles, images, videos) ready and want to schedule it for publication over the coming days or weeks.
- **Performance Tracking:** To automatically gather engagement data (likes, shares, comments, clicks) for your posts and analyze which content performs best.
- **Maintaining Consistent Activity:** For users who want to ensure their social media accounts remain active with regular posts even during off-hours or weekends.
- **Cross-Platform Promotion:** To schedule the same or similar content to be posted across different social networks, tailored to each platform's format.
- **Reporting and Analysis:** When you need to generate periodic reports on your social media performance to share with stakeholders or to inform future strategy.

## Core Capabilities

### 1. Content Scheduling
The primary function is to schedule social media posts. Manus can parse a content plan from a structured file (like a CSV or Markdown table) and schedule each post for a specific date and time.

- **Multi-Platform Support:** The skill is designed to be extensible to various platforms by leveraging their respective APIs or automation tools.
- **Flexible Timing:** Supports scheduling with precise date and time, including timezone considerations.
- **Bulk Scheduling:** Ability to ingest a content calendar and schedule dozens of posts in a single operation.

### 2. Automated Publishing
Once scheduled, Manus will execute the posts automatically at the designated times. This involves using the `Browser` or `Bash` (with tools like `curl`) to interact with social media platform APIs or web interfaces.

- **Text and Media:** Capable of publishing posts that include text, links, and media files (images, videos).
- **Error Handling:** Includes logic to handle potential posting failures (e.g., API errors, network issues) and retry or report the failure.

### 3. Performance Metrics Analysis
After publishing, the skill can be used to revisit the posts to collect performance data. This is crucial for understanding audience engagement and content effectiveness.

- **Data Collection:** Manus can scrape or query post URLs to gather metrics like likes, comments, shares, retweets, and click-through rates.
- **Data Aggregation:** The collected data is stored in a structured format (e.g., a CSV file) for analysis.
- **Report Generation:** Manus can process the aggregated data to create summary reports, identify trends, and highlight top-performing content.

### 4. Content Management
The skill includes helper functions for managing the content to be scheduled.

- **Content Calendar Template:** Provides a template for users to fill in their content plan.
- **Image and Video Handling:** Can reference local media files to be included in posts.
- **Link Shortening:** Can integrate with URL shortening services (like Bitly) via API to create trackable, clean links.

## Step-by-Step Workflow

### Step 1: Create a Content Calendar
First, you need to define your content plan in a structured format. A CSV file is recommended for its simplicity and ease of parsing. Create a file named `content_calendar.csv`.

**`content_calendar.csv` Template:**
```csv
platform,publish_datetime_utc,post_text,media_path,link
"twitter","2026-03-15 14:00:00","Discover how AI is transforming healthcare. Our latest blog post dives deep into the future of medicine. #AI #Healthcare #Tech","","https://example.com/blog/ai-in-healthcare"
"linkedin","2026-03-15 16:30:00","Excited to share our new research on the impact of regenerative medicine. This article explores innovative treatments that are changing patients' lives. Read more here: [link] #RegenerativeMedicine #Innovation #MedTech","","https://example.com/research/regenerative-medicine"
"facebook","2026-03-16 10:00:00","Check out our new patient success story! See how minimally invasive techniques helped John get back on his feet faster. #PatientStory #Orthopedics #Success","./images/patient_story.jpg","https://example.com/stories/johns-journey"
"instagram","2026-03-17 18:00:00","A look inside our state-of-the-art clinic. We are committed to providing the best care with the latest technology. #Clinic #Healthcare #JoãoPessoa","./images/clinic_tour.mp4",""
```

### Step 2: Initiate the Scheduling Process
Instruct Manus to use the `social-media-scheduler` skill and provide the path to your `content_calendar.csv` file.

**User Prompt Example:**
> "Manus, please schedule the social media posts defined in `/home/ubuntu/project/content_calendar.csv`."

### Step 3: Manus Parses and Confirms the Schedule
Manus will read the CSV file, parse each row, and confirm the schedule with you before proceeding.

- **Action:** Use the `Read` tool to access `content_calendar.csv`.
- **Internal Logic:** Loop through each entry, validate the data (e.g., check if `publish_datetime_utc` is in the future), and store it in an internal schedule list.
- **Feedback:** Present a summary of the planned posts to the user for confirmation.

### Step 4: Automated Posting at Scheduled Times
This part of the workflow runs in the background. In a real-world scenario, this would involve setting up cron jobs or using a task scheduler. Within the Manus environment, it can be simulated by checking the current time against the schedule periodically.

- **Action:** At the scheduled time, Manus uses the `Browser` or `Bash` tool.
- **Example (Twitter using `curl` - conceptual):**
  ```bash
  # This is a conceptual example. Actual implementation requires OAuth 1.0a.
  # The user would need to have their Twitter developer credentials configured.
  ACCESS_TOKEN="..."
  ACCESS_TOKEN_SECRET="..."
  CONSUMER_KEY="..."
  CONSUMER_SECRET="..."

  STATUS="Discover how AI is transforming healthcare. Our latest blog post dives deep into the future of medicine. #AI #Healthcare #Tech https://example.com/blog/ai-in-healthcare"

  # The actual command would be much more complex, involving signing the request.
  curl --request POST --url 'https://api.twitter.com/2/tweets' --header "Authorization: Bearer $ACCESS_TOKEN" --header 'Content-Type: application/json' --data "{\"text\": \"$STATUS\"}"
  ```
- **Logging:** After attempting a post, Manus should log the result (success or failure) and the URL of the live post if successful. Create a `publication_log.csv`.

**`publication_log.csv` Template:**
```csv
original_platform,publish_datetime_utc,status,post_url,notes
"twitter","2026-03-15 14:00:00","success","https://twitter.com/user/status/123456789",""
"linkedin","2026-03-15 16:30:00","failure","","API connection error"
```

### Step 5: Performance Data Collection
After a set period (e.g., 24-48 hours), instruct Manus to collect engagement metrics for the published posts.

**User Prompt Example:**
> "Manus, please collect the performance metrics for the posts in `publication_log.csv` and save the results in `performance_data.csv`."

- **Action:** Manus reads `publication_log.csv`. For each successful post, it uses the `Browser` tool to navigate to the `post_url`.
- **Web Scraping (Conceptual):**
  - Navigate to the URL.
  - Use browser interaction tools to find elements containing like counts, comment counts, etc.
  - Extract the text or numerical value from these elements.
- **Data Storage:** Append the collected metrics to a new file, `performance_data.csv`.

**`performance_data.csv` Template:**
```csv
post_url,collection_datetime_utc,likes,comments,shares,clicks
"https://twitter.com/user/status/123456789","2026-03-16 14:05:00",152,23,45,312
```

### Step 6: Generate a Performance Report
Finally, ask Manus to analyze the collected data and generate a report.

**User Prompt Example:**
> "Manus, analyze `performance_data.csv` and generate a summary report highlighting the best-performing posts."

- **Action:** Read `performance_data.csv`.
- **Analysis:** Calculate total engagement, average engagement per post, and identify the post with the highest metrics.
- **Output:** Generate a Markdown file (`report.md`) with the analysis.

**`report.md` Template:**
```markdown
# Social Media Performance Report (Mar 15-17, 2026)

## Summary
- **Total Posts Analyzed:** 1
- **Total Likes:** 152
- **Total Comments:** 23
- **Total Shares:** 45

## Top Performing Post

**Post:** [https://twitter.com/user/status/123456789](https://twitter.com/user/status/123456789)
- **Platform:** Twitter
- **Likes:** 152
- **Comments:** 23
- **Shares:** 45

## Insights
- The post about AI in healthcare on Twitter received significant engagement, indicating strong interest in this topic among the audience.
```

## Best Practices

- **Use a Staging or Test Account:** When first setting up or testing the skill, use a test account for social media platforms to avoid posting unintended content to a live profile.
- **Secure Credential Management:** API keys and access tokens should be handled securely. Use environment variables or a secure vault for storing credentials rather than hardcoding them in scripts or files.
- **Respect API Rate Limits:** Be mindful of the rate limits imposed by each social media platform's API. Implement delays between actions to avoid being blocked.
- **Vary Content:** Avoid posting the exact same message across all platforms. Tailor the `post_text` for each platform’s audience and format conventions.
- **Use High-Quality Media:** Ensure that any images or videos referenced in `media_path` are of high quality and optimized for web viewing.
- **Monitor Regularly:** While the skill automates posting, it's good practice to manually check the accounts periodically to ensure posts are appearing as expected and to engage with comments from your audience.
- **Incremental Data Collection:** Run the performance collection task regularly (e.g., daily) to build a historical dataset of your social media engagement. This will allow for more powerful trend analysis over time.

## Examples

### Example 1: Scheduling a Week of Content for a Tech Blog

1.  **Goal:** Schedule five posts for the upcoming week on Twitter and LinkedIn.
2.  **`content_calendar.csv`:**
    ```csv
    platform,publish_datetime_utc,post_text,media_path,link
    "twitter","2026-04-01 09:00:00","Just released our guide to advanced prompt engineering. Level up your AI skills! #AI #PromptEngineering","","https://example.com/blog/prompt-guide"
    "linkedin","2026-04-01 09:05:00","Our new comprehensive guide to advanced prompt engineering is now available. A must-read for developers and AI enthusiasts looking to master generative models. #AI #LLM #Tech","","https://example.com/blog/prompt-guide"
    "twitter","2026-04-02 11:00:00","What is the future of web development? We explore the rise of serverless and edge computing. #WebDev #Serverless","./images/serverless.png","https://example.com/blog/future-webdev"
    "twitter","2026-04-03 15:00:00","Deep dive into Python's `asyncio` library for concurrent programming. #Python #Programming","","https://example.com/blog/python-asyncio"
    "linkedin","2026-04-05 10:00:00","Case Study: How our client increased their data processing speed by 300% using a custom data engineering solution built by our team. #DataEngineering #CaseStudy","","https://example.com/case-studies/data-speed"
    ```
3.  **Action:** Manus reads the file, schedules the five posts, and confirms the plan.

### Example 2: Running a Weekend Performance Analysis

1.  **Goal:** Collect and analyze the performance of posts from the past week.
2.  **Prerequisite:** A `publication_log.csv` file exists with the URLs of posts published during the week.
3.  **User Prompt:** "Manus, collect metrics from `publication_log.csv`, save to `performance_data_week1.csv`, and generate a report."
4.  **Action:**
    - Manus iterates through the URLs.
    - Uses the `Browser` tool to visit each one and scrape the like/comment/share counts.
    - Saves the data.
    - Creates a `report_week1.md` file summarizing which day of the week and which topics generated the most engagement.

## Advanced Features and Integrations

Beyond the core workflow, the `social-media-scheduler` skill can be enhanced with more advanced capabilities and integrations to create a truly intelligent social media automation system.

### 1. A/B Testing for Content Optimization
Manus can be instructed to test different versions of a post to see which performs better. This is invaluable for optimizing headlines, calls-to-action (CTAs), and imagery.

**Workflow:**
1.  **Define Variants in `content_calendar.csv`:** Add columns for A/B testing, like `post_text_b` and `media_path_b`.
2.  **Schedule Both Versions:** Schedule two similar posts targeted at comparable audience segments at similar times.
3.  **Measure and Compare:** After the collection period, Manus analyzes the performance of both `A` and `B` versions.
4.  **Report on Findings:** The final report will include a section on the A/B test results, declaring a winner and providing insights for future content.

**Example `content_calendar.csv` for A/B Test:**
```csv
platform,publish_datetime_utc,post_text,media_path,link,post_variant
"facebook","2026-04-10 12:00:00","Our new e-book on digital marketing is out! Download it now for free.","./images/ebook_cover_a.png","https://example.com/ebook","A"
"facebook","2026-04-10 12:05:00","Want to master digital marketing? Get our new e-book for free today!","./images/ebook_cover_b.png","https://example.com/ebook","B"
```

### 2. Optimal Post Timing Suggestions
By analyzing historical performance data from `performance_data.csv`, Manus can identify patterns in audience engagement and suggest the best times to post for maximum reach and interaction.

- **Analysis Logic:** The skill would process timestamps and engagement metrics to find correlations. For example, it might discover that for a specific user's audience, LinkedIn posts perform best on Tuesdays between 9:00 AM and 11:00 AM UTC.
- **User Interaction:** When asked to schedule a post without a specific time, Manus could proactively suggest an optimal slot: 
> "I see you want to post to LinkedIn. Based on past performance, posts published on Tuesdays around 10:00 AM UTC receive 30% more engagement. Would you like to schedule for this coming Tuesday?"

### 3. Content Generation and Curation Assistance
Integrate with other Manus capabilities or external AI tools to help create content.

- **Image Generation:** Use the `generate` tool to create unique images for posts based on the `post_text`. 
    > **User:** "Manus, schedule a post about the benefits of hydration. Also, generate a vibrant image of a glass of water with lemon and mint."
- **Text Generation:** If a user provides a topic or a link, Manus can draft the `post_text` for them.
    > **User:** "Manus, create a Twitter post based on this article: [link]. Use relevant hashtags."
- **Article Curation:** Use the `search` tool to find recent, relevant articles on a given topic that can be shared.

### 4. Sentiment Analysis on Comments
For a deeper understanding of audience reception, the skill can be extended to perform sentiment analysis on the comments received on posts.

- **Workflow:**
    1.  During the `Performance Data Collection` step, scrape not just the count but also the text of the comments.
    2.  Use a sentiment analysis library (e.g., NLTK in Python) or an API to classify each comment as positive, negative, or neutral.
    3.  Aggregate the sentiment scores.
- **Reporting:** The performance report can include a sentiment breakdown, offering qualitative insights beyond quantitative metrics. 
    > "The post about our new feature received 85% positive comments, with users frequently mentioning the 'ease of use'."

### 5. Integration with E-commerce Platforms
For businesses, the skill can connect with platforms like Shopify or WooCommerce to automate product promotion.

- **Trigger-Based Posting:** Automatically schedule a post when a new product is added to the store.
- **Sales-Driven Content:** Generate posts featuring products that are on sale or have recently received high ratings.

**Conceptual Workflow:**
1.  Manus is given access to a store's product feed (e.g., an XML or CSV file).
2.  The user sets a template for new product announcements.
    > "New in store! {product_name}. Check it out: {product_url} #NewArrival #ShopNow"
3.  Manus monitors the feed. When a new product appears, it automatically populates the template and adds it to the content schedule.

## Additional Examples

### Example 3: A Doctor Sharing Health Tips

1.  **Goal:** Dr. Lucas wants to schedule a month's worth of weekly health tips on Facebook and Instagram.
2.  **Content Strategy:** The posts will alternate between short informational text posts, images with tips, and short video explanations.
3.  **`content_calendar.csv`:**
    ```csv
    platform,publish_datetime_utc,post_text,media_path,link
    "facebook","2026-05-04 19:00:00","Tip of the week: Staying hydrated is key for joint health. Aim for at least 8 glasses of water a day! #HealthTips #Hydration #Wellness","",""
    "instagram","2026-05-11 19:00:00","Simple stretches you can do at your desk to prevent back pain. #Stretching #DeskJob #PainRelief","./videos/desk_stretches.mp4",""
    "facebook","2026-05-18 19:00:00","Did you know that Vitamin D is crucial for bone strength? A little bit of sun can go a long way. #VitaminD #BoneHealth","./images/sunshine.jpg",""
    "instagram","2026-05-25 19:00:00","Let's talk about the benefits of a balanced diet for managing chronic pain. #Nutrition #PainManagement #HealthyLiving","",""
    ```
4.  **Action:** Manus schedules the posts. Dr. Lucas can then use the performance analysis features to see which topics (hydration, exercise, nutrition) resonate most with his audience, helping him plan future content.

### Example 4: E-commerce Store Flash Sale

1.  **Goal:** Promote a 24-hour flash sale on Twitter.
2.  **Strategy:** Create a sense of urgency by posting a countdown.
3.  **`content_calendar.csv`:**
    ```csv
    platform,publish_datetime_utc,post_text,media_path,link
    "twitter","2026-06-01 08:00:00","FLASH SALE! ⚡ Get 30% off everything for the next 24 hours only! Use code FLASH30 at checkout. #FlashSale #Deal #LimitedTime","./images/sale_banner.png","https://example.com/shop"
    "twitter","2026-06-01 16:00:00","Our Flash Sale is still on! Only 8 hours left to get 30% off. Don't miss out! #Sale #Ecommece","","https://example.com/shop"
    "twitter","2026-06-02 07:00:00","Last chance! ⏰ Only 1 hour left in our 30% off Flash Sale. It's now or never! #LastChance #ShopNow","","https://example.com/shop"
    ```
4.  **Analysis:** After the sale, Manus can be tasked to collect click-through data from the links (if a URL shortener was used) to measure how effective each tweet was at driving traffic to the store.


## Troubleshooting and Edge Cases

- **Post URL Not Found:** If a `post_url` is invalid (e.g., the post was deleted), the skill should log the error and skip it during performance collection.
- **Platform UI Changes:** Web scraping is fragile and can break if a social media platform updates its website design. The skill must have robust error handling to detect when selectors for metrics (likes, comments) are no longer valid. A potential solution is to have fallback selectors or to notify the user that the scraping logic for a platform needs to be updated.
- **Handling Different Media Types:** The skill should validate the `media_path` and ensure the file type is supported by the target platform (e.g., Twitter supports JPG, PNG, GIF, MP4).
- **Character Limits:** Each platform has its own character limit (e.g., Twitter's 280 characters). The skill should truncate or warn the user if `post_text` exceeds the limit for a given platform.
- **Authentication Failures:** If API credentials expire or are revoked, the skill should provide a clear error message and guide the user on how to re-authenticate or update their credentials.

## Security Considerations

- **API Key Management:** As mentioned in Best Practices, never hardcode API keys. The skill should be designed to read credentials from secure environment variables. When interacting with the user, Manus should never expose these keys in its responses.
- **Input Sanitization:** All inputs from the `content_calendar.csv` file should be treated as untrusted. The skill should sanitize the `post_text` and other fields to prevent injection attacks, especially if the content is used to build shell commands or API requests.
- **Browser Isolation:** When using the `Browser` tool for scraping, it should be done in an isolated environment to prevent malicious JavaScript on a page from accessing sensitive information in the Manus environment.

## Future Enhancements

- **Interactive Dashboard:** Instead of a static Markdown report, the skill could generate an interactive HTML report with charts (e.g., using Chart.js) to visualize performance trends over time.
- **Follower Growth Tracking:** Extend the data collection to track follower counts on each platform, correlating follower growth with posting activity and content strategy.
- **Competitor Analysis:** The skill could be adapted to monitor the social media accounts of competitors, analyzing their posting frequency, content themes, and engagement rates to provide competitive intelligence.
- **Hashtag Recommendation:** Based on the `post_text` and historical data, the skill could suggest a list of optimal hashtags to increase discoverability and engagement.

## References

- **Social Media APIs:** To implement the posting and data collection features, you will need to refer to the official developer documentation for each platform.
    - **Twitter API:** [https://developer.twitter.com/en/docs/twitter-api](https://developer.twitter.com/en/docs/twitter-api)
    - **LinkedIn API:** [https://learn.microsoft.com/en-us/linkedin/](https://learn.microsoft.com/en-us/linkedin/)
    - **Facebook Graph API:** [https://developers.facebook.com/docs/graph-api](https://developers.facebook.com/docs/graph-api)
- **Web Automation & Scraping:**
    - **Selenium Documentation:** [https://www.selenium.dev/documentation/](https://www.selenium.dev/documentation/) (For browser automation)
    - **Beautiful Soup Documentation:** [https://www.crummy.com/software/BeautifulSoup/bs4/doc/](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) (For parsing HTML content)
- **Task Scheduling (Conceptual):**
    - **Cron Jobs:** [https://en.wikipedia.org/wiki/Cron](https://en.wikipedia.org/wiki/Cron) (A classic utility for time-based job scheduling in Unix-like operating systems).
