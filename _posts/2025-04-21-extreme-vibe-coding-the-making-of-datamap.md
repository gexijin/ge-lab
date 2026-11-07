---
layout: post
title: "Extreme Vibe Coding: The Making of DataMap"
date: 2025-04-21 19:23:53 +0000
---

Inspired by [shinyheatmap.com](https://shinyheatmap.com), shared by Ming Tang on X, I embarked on a side project, creating **[DataMap](https://github.com/gexijin/datamap)**, a lightweight Shiny app designed to generate heatmaps. Based on [**shinylive**](https://posit-dev.github.io/r-shinylive/) and **[webR](https://docs.r-wasm.org/webr/latest/)**, the app runs in the browser in a serverless setup, ensuring security and scalability. Yet, my primary motivation was exploring the limits of AI-assisted coding (vibe coding). Could AI do all the coding?

Here’s my experience.

![]({{ site.baseurl }}/assets/uploads/2025/04/heatmap-1.png)

### Tools and Environment

- **IDE**: Visual Studio Code, enhanced with GitHub Copilot and Copilot Chat extensions.
- **Version Control**: GitHub Desktop simplified code management, version tracking, and provided a safety net for experimentation.
- **LLMs**: My main assistant was Claude Sonnet 3.7, chosen for its superior R coding capabilities (as shown in benchmarks). Occasionally, I turned to ChatGPT (o1 and o3-mini models) and Google Gemini 2.5 Pro.
- **Web App Framework**: R/Shiny with shinylive and webR via WebAssembly. Since webR supports only a subset of R packages, and the goal was to stay lightweight, I limited myself primarily to the `shiny` and `pheatmap` packages.

### Extreme Vibe Coding: my workflow

My coding workflow evolved into a structured iterative process:

1. **Ideate and Strategize**: As the product manager, I’d first clearly define enhancements or fixes.
2. **Prepare Code for Claude.ai**: Upload relevant `.R` files to a **new** Claude.ai chat—Claude conveniently accepts file uploads, unlike ChatGPT.
3. **Draft & Polish Prompts**: Carefully craft prompts, polishing them with Grammarly plugin directly in the chat box. I found it is important to write properly.
4. **AI Code Generation**: Submit prompts, review initial AI-generated code.
5. **AI Self-Review Loop**: Prompt Claude explicitly to "Review your code thoroughly." If it uncovers issues or alternative solutions, I ask it to review repeatedly until stability is reached.
6. **Test AI Code**: Implement and test the provided code in VS Code.
7. **Iterative Refinement**: Provide limited follow-up prompts to correct minor issues or further enhance features. Occasionally, you just have to discard all changes and rethink the approach.
8. **Version Control**: Commit successful code changes frequently to GitHub Desktop. Archive the Claude session and start fresh with each new feature or module.
9. **Repeat**: Iterate this process continuously, optimizing incrementally.

This approach helped me rapidly prototype and refine DataMap, effectively leveraging AI’s strengths while managing its limitations.

### Overall Experience

Using AI-assisted coding, I rapidly developed around 90% of DataMap’s functionality in just three days—without manually writing any code. However, the remaining 10%—especially tasks involving detailed debugging, UX refinements, and resolving complex logic errors—proved to be far more challenging.

AI coding often feels like self-driving cars: it handles routine tasks exceptionally well, but struggles with edge cases that require deep human understanding. For example, Claude frequently introduced subtle logical errors in data-analysis steps. These were harder to catch, as AI-generated code often appears syntactically correct and executes smoothly, masking underlying logical issues.

Nevertheless, the productivity boost is undeniably powerful, especially for initial rapid prototyping.

### Key Lessons Learned

1. **AI Accelerates but Does Not Replace Human Coding**. AI generated roughly 95% of DataMap's code, but the critical 5% required substantial manual intervention. Particularly, debugging logic and enhancing UX always needed careful human input.

1. **Small Steps, Frequent Commits**. Regularly committing small, working changes to GitHub is crucial. I learned this the hard way—ambitious changes frequently crashed the app, leading to painful rollbacks and lost progress. Frequent incremental commits mitigated this significantly.

1. **Modular Code Is Crucial**. Modularization—splitting code into reusable, clearly defined functions and Shiny modules—proved invaluable. DataMap's 3,800 lines of R code are neatly divided into one main app file and six smaller modules (~500 lines each). This structure simplified both human readability and AI-assisted refinements, preventing unintended side-effects across modules.

1. **Ask AI to Self-Evaluate**. One-shot AI solutions are rarely optimal. Regularly prompting Claude to "thoroughly review your code" often uncovered overlooked mistakes or better approaches. When repeated reviews consistently flagged new issues, it indicated deeper complexity—prompting extra caution in testing.

1. **Context Management is Essential**. Effective context management boosts AI assistance. For small inline edits, GitHub Copilot worked smoothly, using open files as context. For larger, cross-module tasks, manually uploading relevant code snippets to Claude.ai yielded better results.

1. **Claude Excels at Refactoring**. Initially, DataMap lacked modular Shiny structures. I asked Claude to "extract the heatmap functionality as a Shiny module," expecting significant adjustments. Amazingly, the AI-generated refactoring worked seamlessly on the first attempt. It separated all the logic and defined the dynamic variables connecting the main app and the module.

1. **Uneven Productivity Gains**. The rapid initial progress slowed significantly as the codebase matured. Easy AI-driven wins dominated the early stage, while later refinements, particularly UX optimization and edge-case handling, required extensive manual tuning. For instance, generating reproducible R code from the Shiny app’s visualizations—a crucial user feature—took nearly a full day to perfect. Sometimes you get stuck—prompt after prompt fails. Ironically, some tough issues resolved themselves inadvertently during unrelated changes.

1. **Documentation: Fast but Imperfect**. Generating comprehensive documentation in HTML was almost instant: upload the code, prompt Claude, and voilà—a clear, structured guide complete with example datasets. Similarly, drafting a manuscript using a LaTeX journal template with AI-generated initial content saved significant time. Claude even suggested relevant references. Although the initial draft required extensive human editing, it dramatically streamlined the overall writing process. But still, it took considerable time to do the writing, create demo videos, and post on social media.

### Bonus Tool Tip: UitHub.com

An unexpected discovery was [UitHub.com](https://uithub.com)—a handy tool for generating plain-text snapshots of GitHub repositories. By replacing “GitHub” with “UitHub” in URLs, it allowed me to quickly import entire project structures into Claude’s chat sessions, greatly facilitating larger refactoring and restructuring tasks.

For example:

- Original: `https://github.com/gexijin/datamap`
- Snapshot: `https://uithub.com/gexijin/datamap`

### Conclusion

Overall, this extreme vibe coding experience was immensely positive. Most of the app is developed in a week. The entire project is finished in two weeks, including fine-tuning the app and submitting the manuscript. Human-AI collaboration proved a massive productivity multiplier, dramatically accelerating development while demanding careful human oversight, strategic context management, and disciplined version control.

After I shared this app on [X/Twitter](https://x.com/StevenXGe/status/1912641691376329153) and [LinkedIn](https://www.linkedin.com/posts/steven-ge-ab016947_datascience-bioinformatics-shinyapps-activity-7318405746998554626-7rgI?utm_source=share&utm_medium=member_desktop&rcm=ACoAAAnP5OQBxgAfMbwdbo0DbaqOnljtT1tcp2w) on April 16, 2025, there were lots of 'likes' and reposts, resulting in about 70,000 impressions. According to statistics from GitHub, the app has been used by around 1000 users in just a few days. In a few days, it received 27 stars and was forked 5 times. Within 12 hours, a user submitted a Python version of the app using Streamlit. I even had a Zoom call with a user at a top university who reported an issue when using DataMap to visualize genomics data. These are pretty good outcomes for a side project done mainly by AI in a short time.

Of course, this is possible partly because I am an experienced Shiny developer. I have also created heatmaps in other apps, such as [iDEP](http://bioinformatics.sdstate.edu/idep/), which, unlike DataMap, is a massive beast that took 7 years to develop.

AI tools like Claude.ai, GitHub Copilot, and ChatGPT are revolutionizing software development. However, nuanced human intervention—particularly in debugging, UX optimization, and strategic design—is still irreplaceable. Embracing AI as a partner, rather than expecting complete autonomy, is key to unlocking maximum productivity.
