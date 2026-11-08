---
layout: post
title: "Extreme Vibe Coding: The Making of DataMap"
date: 2025-04-21 19:23:53 +0000
---

Inspired by [shinyheatmap.com](https://shinyheatmap.com), which Ming Tang shared on X, I started a side project: **[DataMap](https://github.com/gexijin/datamap)**, a lightweight Shiny app for generating heatmaps. Built on [**shinylive**](https://posit-dev.github.io/r-shinylive/) and [**webR**](https://docs.r-wasm.org/webr/latest/), the app runs entirely in the browser with no server, which makes it secure and scalable. My main motivation, though, was to explore the limits of AI-assisted coding (vibe coding). Could AI do all the coding?

Here's my experience.

![]({{ site.baseurl }}/assets/uploads/2025/04/heatmap-1.png)

## Tools and Environment

- **IDE**: Visual Studio Code with the GitHub Copilot and Copilot Chat extensions.
- **Version control**: GitHub Desktop simplified code management and version tracking, and provided a safety net for experimentation.
- **LLMs**: My main assistant was Claude 3.7 Sonnet, chosen for its strong R coding ability (as shown in benchmarks). Occasionally, I turned to ChatGPT (the o1 and o3-mini models) and Google Gemini 2.5 Pro.
- **Web app framework**: R/Shiny with shinylive and webR via WebAssembly. Since webR supports only a subset of R packages, and I wanted to stay lightweight, I limited myself mostly to the `shiny` and `pheatmap` packages.

## Extreme Vibe Coding: My Workflow

My workflow evolved into a structured, iterative process:

1. **Ideate and strategize**: As the product manager, I first clearly define the enhancement or fix.
2. **Prepare code for Claude.ai**: Upload the relevant `.R` files to a **new** Claude.ai chat. Claude conveniently accepts file uploads, unlike ChatGPT.
3. **Draft and polish prompts**: Carefully craft prompts, polishing them with the Grammarly plugin directly in the chat box. I found that writing well matters.
4. **AI code generation**: Submit the prompt and review the initial AI-generated code.
5. **AI self-review loop**: Explicitly prompt Claude to "Review your code thoroughly." If it uncovers issues or alternative solutions, ask it to review again until the code stabilizes.
6. **Test AI code**: Paste the code into VS Code and test it.
7. **Iterative refinement**: Use a few follow-up prompts to fix minor issues or enhance features. Occasionally, you just have to discard all changes and rethink the approach.
8. **Version control**: Commit working changes frequently using GitHub Desktop. Archive the Claude session and start fresh for each new feature or module.
9. **Repeat**: Iterate continuously, improving incrementally.

This approach let me rapidly prototype and refine DataMap, leveraging AI's strengths while managing its limitations.

## Overall Experience

With AI-assisted coding, I developed about 90% of DataMap's functionality in just three days, without manually writing any code. The remaining 10%, however, especially detailed debugging, UX refinements, and complex logic errors, proved far more challenging.

AI coding often feels like a self-driving car: it handles routine tasks exceptionally well but struggles with edge cases that require deep human understanding. For example, Claude frequently introduced subtle logical errors in data-analysis steps. These were hard to catch, because AI-generated code usually looks correct and runs smoothly, masking the underlying logic problems.

Nevertheless, the productivity boost is undeniable, especially for rapid initial prototyping.

## Key Lessons Learned

1. **AI accelerates but does not replace human coding.** AI generated roughly 95% of DataMap's code, but the critical remaining 5% required substantial manual intervention. Debugging logic and improving UX in particular always needed careful human input.

2. **Small steps, frequent commits.** Regularly committing small, working changes to GitHub is crucial. I learned this the hard way: ambitious changes frequently broke the app, leading to painful rollbacks and lost progress. Frequent, incremental commits greatly reduced this.

3. **Modular code is crucial.** Splitting code into reusable, clearly defined functions and Shiny modules proved invaluable. DataMap's 3,800 lines of R code are divided into one main app file and six smaller modules (~500 lines each). This structure made the code easier for both humans and AI to work with, and prevented unintended side effects across modules.

4. **Ask AI to self-evaluate.** One-shot AI solutions are rarely optimal. Prompting Claude to "thoroughly review your code" often uncovered overlooked mistakes or better approaches. When repeated reviews kept flagging new issues, it signaled deeper complexity and called for extra caution in testing.

5. **Context management is essential.** Good context makes AI far more helpful. For small inline edits, GitHub Copilot worked smoothly, using open files as context. For larger, cross-module tasks, manually uploading the relevant code to Claude.ai gave better results.

6. **Claude excels at refactoring.** Initially, DataMap had no Shiny modules. I asked Claude to "extract the heatmap functionality as a Shiny module," expecting to make significant adjustments. Amazingly, the refactored code worked on the first attempt. Claude separated all the logic and defined the reactive variables connecting the main app and the module.

7. **Productivity gains are uneven.** Rapid initial progress slowed significantly as the codebase matured. Easy AI-driven wins dominated the early stage, while later refinements, particularly UX optimization and edge-case handling, required extensive manual tuning. For instance, generating reproducible R code from the app's visualizations, a crucial feature for users, took nearly a full day to get right. Sometimes you get stuck, and prompt after prompt fails. Ironically, some tough issues resolved themselves during unrelated changes.

8. **Documentation: fast but imperfect.** Generating comprehensive HTML documentation was almost instant: upload the code, prompt Claude, and voilà, a clear, structured guide complete with example datasets. Similarly, drafting a manuscript in a LaTeX journal template with AI-generated initial content saved significant time. Claude even suggested relevant references. Although the draft required extensive editing, AI dramatically streamlined the writing process. Still, writing, creating demo videos, and posting on social media took considerable time.

## Bonus Tool Tip: UitHub.com

An unexpected discovery was [UitHub.com](https://uithub.com), a handy tool that generates plain-text snapshots of GitHub repositories. By replacing "github" with "uithub" in a repository URL, I could quickly import an entire project into a Claude chat, which greatly helped with larger refactoring and restructuring tasks.

For example:

- Original: `https://github.com/gexijin/datamap`
- Snapshot: `https://uithub.com/gexijin/datamap`

## Conclusion

Overall, this extreme vibe coding experience was immensely positive. Most of the app was developed in a week, and the entire project, including fine-tuning the app and submitting the manuscript, was finished in two weeks. Human-AI collaboration proved to be a massive productivity multiplier, dramatically accelerating development while still demanding careful human oversight, strategic context management, and disciplined version control.

After I shared the app on [X/Twitter](https://x.com/StevenXGe/status/1912641691376329153) and [LinkedIn](https://www.linkedin.com/posts/steven-ge-ab016947_datascience-bioinformatics-shinyapps-activity-7318405746998554626-7rgI?utm_source=share&utm_medium=member_desktop&rcm=ACoAAAnP5OQBxgAfMbwdbo0DbaqOnljtT1tcp2w) on April 16, 2025, the posts drew lots of likes and reposts, totaling about 70,000 impressions. According to GitHub statistics, around 1,000 users tried the app within a few days. In that time, the repository received 27 stars and 5 forks. Within 12 hours, a user submitted a Python version of the app built with Streamlit. I even had a Zoom call with a user at a top university who reported an issue when using DataMap to visualize genomics data. These are pretty good outcomes for a side project built mostly by AI in a short time.

Of course, this was possible partly because I am an experienced Shiny developer. I have also created heatmaps in other apps, such as [iDEP](http://bioinformatics.sdstate.edu/idep/), which, unlike DataMap, is a massive beast that took seven years to develop.

AI tools like Claude.ai, GitHub Copilot, and ChatGPT are revolutionizing software development. However, nuanced human input, particularly in debugging, UX optimization, and strategic design, remains irreplaceable. Embracing AI as a partner, rather than expecting complete autonomy, is the key to unlocking maximum productivity.
