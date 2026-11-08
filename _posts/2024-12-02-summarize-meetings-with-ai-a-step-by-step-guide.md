---
layout: post
title: "Minutes in Minutes: Summarize Meetings with AI"
date: 2024-12-02 23:29:08 +0000
categories: ["AI"]
---

![]({{ site.baseurl }}/assets/uploads/2024/12/image-150x150.png)

Meetings are essential for collaboration, and documenting them keeps a record and informs those who couldn't attend. But summarizing meetings and writing minutes takes time. AI tools like ChatGPT or Claude make it easy: they are free, and in a few minutes you can get meeting minutes, detailed summaries, or even diagrams of the main ideas! This post walks you through summarizing meetings held on Zoom, in person, on Microsoft Teams, or on Google Meet.

## Zoom Meetings

Zoom's recording and transcription features make summarization straightforward.

### 1. Record the meeting

During your Zoom meeting, click the **Record** button. Zoom automatically processes the recording and generates several files, including a transcript.

### 2. Download the recording

1. A few minutes after the meeting, go to the Zoom web portal.
2. Find the meeting under the **Recordings** tab.
3. Download the recording. Once unzipped, it includes files for video, audio, and the **transcript**.

### 3. Summarize the transcript with AI

Upload the transcript file to **ChatGPT** or **Claude** and ask for a summary, for example:

- *"Summarize the meeting in a **brief paragraph.**"*
- *"Give me **bullet points** for key takeaways from this meeting. "*
- *"Give me a **detailed summary** for this meeting."*
- *"Summarize the main points shared **by John Doe**."*

The last one works because Zoom's transcript labels each line with the speaker's name, which is super convenient.

### 4. Generate a flowchart

Want a high-level, graphical summary? In ChatGPT, try this:

> *"Write and run code to draw a flowchart that captures the main idea of the meeting. "*

From the transcript of an hour-long recording, I got the diagram below. I am speechless at how well AI captured our main ideas!

![]({{ site.baseurl }}/assets/uploads/2024/12/meeting-flowchart-1024x288.jpg)

ChatGPT extracts the main ideas from the transcript and then writes Python code to draw a flowchart. It runs the code and gives you the flowchart to download.

This looks great, but the PNG file was low resolution and too wide. I refined it with this prompt:

> *"Can you give me a high-resolution version in PDF? Within each box, can you make it into two lines? This will reduce the width of the boxes, giving the entire diagram a better aspect ratio."*

![]({{ site.baseurl }}/assets/uploads/2024/12/improved-flow-chart-1024x561.jpg)

My jaw dropped! Within minutes, I had summaries at different levels, including the key opinions of each participant, and a diagram like this. I thought this kind of high-level thinking was uniquely human.

## In-Person Meetings

In-person meetings don't come with an automatic transcript, but you can create one with a recorder app and AI tools.

### 1. Record the meeting

- Capture the audio with a free recording app. Popular options include:
  - **iPhone**: Voice Memos
  - **Android**: Google Recorder, Otter.ai, or Easy Voice Recorder
- Get consent before recording.

### 2. Transfer the audio to your computer

Use your phone's sharing options (e.g., email, cloud storage, or USB transfer) to move the audio file to your computer.

### 3. Transcribe the audio in Word

1. Open Microsoft Word.
2. On the **Home** tab, select **Dictate** > **Transcribe**.
3. Upload the audio file, and Word generates a transcript. Review and correct it if necessary.

### 4. Summarize with AI

Copy the transcript from Word, paste it into ChatGPT or another AI tool, and follow the same steps as for Zoom transcripts.

## Microsoft Teams and Google Meet

Both **Microsoft Teams** and **Google Meet** have built-in recording and transcription.

### Microsoft Teams

- **Transcription:** During a meeting, select **More actions** > **Start transcription**. The transcript includes speaker attribution and is saved for review after the meeting.
- **Recording:** Select **More actions** > **Start recording**. Recordings and transcripts are stored in OneDrive or SharePoint, depending on your setup.

### Google Meet

- **Transcription:** During a meeting, click **Activities** > **Transcripts**. Transcripts are saved to the organizer's Google Drive and linked to the calendar event.
- **Recording:** Use **More options** > **Record meeting**. Recordings are saved to the "Meet Recordings" folder in Google Drive.

You can then upload the transcripts to ChatGPT or Claude for summarization. Always tell participants before recording or transcribing, to comply with privacy policies.

## Advantages of AI Meeting Summaries

- **Time-saving**: AI processes long transcripts in seconds.
- **Customizable**: You can request summaries of specific participants or particular parts of the meeting.
- **Focused**: AI can highlight important topics, decisions, and action items.

## Conclusion

Whether you start from a Zoom recording or an in-person audio file, AI tools like ChatGPT and Claude can turn meeting transcripts into concise, actionable minutes. These simple steps keep your team informed and aligned while saving time and effort. Try them at your next meeting!

*Based on personal experience, I hastily wrote down some notes and fed them to GPT-4o to write this post, which I then edited. Initial version 12/2/2024; I had the diagram idea and added it on 12/4/2024. AI also generated the picture and the title.*

*I am just AI's sidekick.*
