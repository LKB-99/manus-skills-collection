---
name: podcast-producer
description: Complete podcast production including scriptwriting, audio editing, and transcription.
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Podcast Producer

## Overview
This skill provides a comprehensive workflow for producing a podcast from start to finish. It covers everything from initial concept and scriptwriting to audio recording, editing, and final transcription for show notes or content repurposing. This skill is designed for users who want to create high-quality podcasts efficiently, leveraging AI and automation to streamline the production process.

## When to Use This Skill
This skill is particularly useful in the following scenarios:

- **New Podcast Creation:** When you have an idea for a podcast but need a structured process to get started.
- **Automating Existing Podcasts:** For podcasters looking to automate repetitive tasks like editing, transcription, and show note generation.
- **Content Repurposing:** To transform existing content (blog posts, webinars, etc.) into a podcast format.
- **Interview-Based Podcasts:** To streamline the process of recording, editing, and transcribing interviews with guests.
- **Solo Podcasts:** For individuals who want to produce their own podcasts without a large team.

## Core Capabilities

### 1. Scriptwriting and Show Planning
This skill helps you structure your podcast episodes, from brainstorming topics to writing a full script.

- **Topic Generation:** Brainstorm episode ideas based on your podcast's theme and target audience.
- **Outline Creation:** Generate a structured outline for your episode, including introduction, main segments, and conclusion.
- **Full Scriptwriting:** Write a complete script, including host narration, interview questions, and transitions.
- **Show Notes Preparation:** Automatically generate draft show notes, including key takeaways, guest bios, and resource links.

**Template: Episode Outline**
```markdown
# [Episode Title]

**A. Introduction (1-2 minutes)**
-   Hook: Start with a compelling question, story, or statistic.
-   Brief overview of the episode's topic.
-   Introduce yourself and any guests.

**B. Main Segment 1: [Topic 1] (5-7 minutes)**
-   Key point 1
-   Supporting detail/example
-   Key point 2
-   Supporting detail/example

**C. Main Segment 2: [Topic 2] (5-7 minutes)**
-   Key point 1
-   Supporting detail/example
-   Key point 2
-   Supporting detail/example

**D. Interview with [Guest Name] (10-15 minutes)**
-   Question 1: ...
-   Question 2: ...
-   Question 3: ...

**E. Conclusion (2-3 minutes)**
-   Recap of main points.
-   Call to action (e.g., subscribe, leave a review, visit website).
-   Outro music.
```

### 2. Audio Recording and Editing
This capability focuses on capturing high-quality audio and refining it for a professional sound.

- **Recording Guidance:** Provides best practices for recording audio, including microphone techniques and environment setup.
- **Automated Audio Cleanup:** Uses tools to automatically remove background noise, filler words ('um', 'ah'), and long pauses.
- **Audio Enhancement:** Applies equalization (EQ), compression, and normalization to improve audio quality and consistency.
- **Music and Sound Effects:** Adds intro/outro music and sound effects to enhance the listening experience.

**Example: Using `ffmpeg` for basic audio cleanup**
```bash
# Normalize audio to -16 LUFS (a common standard for podcasts)
ffmpeg -i input.wav -filter:a loudnorm=I=-16:TP=-1.5:LRA=11 -ar 44100 output.wav

# Apply a high-pass filter to remove low-frequency rumble
ffmpeg -i input.wav -af "highpass=f=80" output.wav

# Apply a noise reduction filter (requires a noise profile)
# First, create a noise profile from a silent section
ffmpeg -i input.wav -ss 00:00:05 -t 00:00:10 -f null -af "anullsink,ametadata=print:key=lavfi.astats.Overall.RMS_level,anullsink" - > noise_profile.txt
# Then, apply the noise reduction
ffmpeg -i input.wav -af "afftdn=nr=10:nf=-20" output.wav
```

### 3. Transcription and Content Repurposing
This capability turns your audio into text, opening up new possibilities for content distribution.

- **Automated Transcription:** Generates a full text transcript of your podcast episode with high accuracy.
- **Speaker Diarization:** Identifies and labels different speakers in the transcript.
- **Timestamping:** Adds timestamps to the transcript, making it easy to navigate the audio.
- **Content Extraction:** Pulls out key quotes, summaries, and action items from the transcript to be used in show notes, blog posts, or social media.

**Template: Show Notes from Transcript**
```markdown
## Episode Summary
[A 2-3 paragraph summary of the episode, generated from the transcript.]

## Key Takeaways
-   [Takeaway 1]
-   [Takeaway 2]
-   [Takeaway 3]

## Memorable Quotes
-   "[Quote 1]" - [Speaker], [Timestamp]
-   "[Quote 2]" - [Speaker], [Timestamp]

## Resources Mentioned
-   [Resource 1](link)
-   [Resource 2](link)
```

## Step-by-Step Workflow

1.  **Phase 1: Pre-Production**
    1.  **Define Episode Goal:** Use `Write` to create a new document outlining the episode's topic, target audience, and desired outcome.
    2.  **Brainstorm & Outline:** Use AI-powered tools or the `Browser` tool to research the topic. Create a detailed outline using the template provided above.
    3.  **Write Script:** Write the full script in a new file. For interview-based shows, prepare a list of questions for your guest.
    4.  **Guest Coordination:** If you have a guest, send them the outline, questions, and recording instructions.

2.  **Phase 2: Production (Recording)**
    1.  **Setup Environment:** Ensure you are in a quiet space with minimal echo. Use a quality microphone.
    2.  **Record Audio:** Record the episode. If recording remotely with a guest, use a tool that provides separate audio tracks for each speaker (e.g., Zencastr, Riverside.fm).
    3.  **Save Raw Audio:** Save the raw, unedited audio files in a dedicated project folder. Use a consistent naming convention (e.g., `EP01_raw_audio.wav`).

3.  **Phase 3: Post-Production (Editing & Mixing)**
    1.  **Import Audio:** Import the raw audio files into your editing software or use command-line tools like `ffmpeg`.
    2.  **Run Automated Cleanup:** Use `Bash` to execute scripts for noise reduction, filler word removal, and normalization. Many AI-powered services can also do this via API (e.g., Descript, Auphonic).
    3.  **Manual Edit:** Listen through the audio and make any necessary manual edits, such as removing mistakes or rearranging segments.
    4.  **Add Music & SFX:** Add your intro/outro music and any sound effects.
    5.  **Mix & Master:** Adjust the volume levels of different tracks (host, guest, music) to ensure a balanced mix. Export the final audio file in MP3 format.

4.  **Phase 4: Distribution & Repurposing**
    1.  **Transcribe Audio:** Use a transcription service or tool to generate a full transcript of the episode.
    2.  **Generate Show Notes:** Use the transcript to create detailed show notes, including a summary, key takeaways, and resources mentioned. Use the provided template.
    3.  **Create Audiogram/Video Clips:** Use tools like CapCut or Canva to create short video clips with animated waveforms for social media promotion.
    4.  **Publish:** Upload the final MP3 file and show notes to your podcast hosting provider.
    5.  **Promote:** Share the episode and promotional assets on your website, social media, and email newsletter.

## Best Practices

-   **Consistency is Key:** Publish episodes on a consistent schedule to build and retain an audience.
-   **Invest in Good Audio:** Audio quality is one of the most important factors for listener retention. A good microphone and a quiet recording space are essential.
-   **Edit for Clarity, Not Perfection:** The goal of editing is to make the episode easy to listen to. Don't obsess over removing every tiny imperfection.
-   **Repurpose Everything:** A single podcast episode can be turned into dozens of smaller content pieces. Create blog posts, social media updates, quote graphics, and more from each episode.
-   **Engage with Your Audience:** Encourage listeners to leave reviews, send in questions, and join your community. Mention them on the show to build a loyal following.
-   **Use a Project Management Structure:** Keep your files organized. Create a new folder for each episode with subfolders for scripts, raw audio, edited audio, and promotional materials.

## Examples

### Example 1: Starting a New Solo Podcast Episode

1.  **Goal:** Create a 15-minute solo episode about the 'Pomodoro Technique'.
2.  **Action:** Use the `Write` tool to create `EP05_pomodoro_script.md`.
3.  **Content (Outline):**
    ```markdown
    # Pomodoro Technique Deep Dive

    **Intro:**
    - Hook: "What if you could get more done in less time, just by using a tomato timer?"
    - Overview: Explain what the Pomodoro Technique is and why it's effective.

    **Segment 1: The 5 Steps**
    1. Choose a task.
    2. Set a 25-minute timer.
    3. Work without interruption.
    4. Take a 5-minute break.
    5. After 4 Pomodoros, take a longer break (15-30 mins).

    **Segment 2: Common Pitfalls**
    - Ignoring the timer.
    - Getting distracted.
    - Making tasks too big.

    **Conclusion:**
    - Recap the benefits.
    - CTA: "Try it for one day and see the difference. Let me know how it goes!"
    ```
4.  **Next Step:** Expand the outline into a full script, then proceed to recording.

### Example 2: Automating Post-Production with `ffmpeg` and a Shell Script

1.  **Goal:** Process a raw WAV file to improve its quality.
2.  **Action:** Create a shell script `process_audio.sh`.
3.  **Content (Script):**
    ```bash
    #!/bin/bash

    INPUT_FILE=$1
    OUTPUT_FILE="${INPUT_FILE%.*}_processed.mp3"

    echo "Processing $INPUT_FILE..."

    # 1. Apply high-pass filter to remove rumble
    # 2. Apply noise reduction (assumes a profile has been generated)
    # 3. Normalize loudness to -16 LUFS
    # 4. Convert to MP3 at 128k bitrate

    ffmpeg -i "$INPUT_FILE" \
    -af "highpass=f=80,afftdn,loudnorm=I=-16:TP=-1.5:LRA=11" \
    -ar 44100 \
    -c:a libmp3lame -b:a 128k \
    "$OUTPUT_FILE"

    echo "Processing complete. Output file: $OUTPUT_FILE"
    ```
4.  **Execution:**
    ```bash
    chmod +x process_audio.sh
    ./process_audio.sh EP01_raw_audio.wav
    ```

## References

-   [Transom.org](https://transom.org/): A great resource for all things audio storytelling.
-   [The Audacity to Podcast](https://theaudacitytopodcast.com/): Tips and tutorials for podcasters.
-   [ffmpeg Documentation](https://ffmpeg.org/ffmpeg-filters.html): Official documentation for ffmpeg audio filters.
-   [Riverside.fm Blog](https://riverside.fm/blog): Articles on podcasting trends and techniques.
-   [Descript](https://www.descript.com/): AI-powered audio/video editor with transcription and automated cleanup features.
