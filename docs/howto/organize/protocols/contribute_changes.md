# How to Contribute Changes

> **You don't need to be a developer to help improve these documents.**  
> This guide shows you exactly how to share ideas and suggest changes, step by step.

---

## Overview: Two Ways to Participate

### Just Want to Discuss an Idea?
**→ Open a GitHub Issue** (no technical skills needed)  
Perfect for: Sharing suggestions, asking questions, starting discussions

### Want to Make the Change Yourself?
**→ Edit on GitHub** (easier than you think!)  
Perfect for: Fixing typos, clarifying language, adding examples

**→ Use VS Code** (optional, for bigger changes)  
Perfect for: Reorganizing sections, adding new pages, testing locally

---

## Part 1: Starting a Discussion (GitHub Issues)

**Think of this as a suggestion box or discussion forum.** No technical knowledge required.

### What is a GitHub Issue?

Anyone can:
- Propose an idea for improvement
- Ask questions about existing practices
- Share what's working or not working in their circle
- Discuss whether a change aligns with core principles

### Step-by-Step: Opening an Issue

1. **Go to the Issues page**  
   Visit: [practice_circle/issues](https://github.com/simondilhas/practice_circle/issues)

2. **Click "New issue"**  
   Look for the green button (top right)
   
   ![GitHub issues page](/assets/images/github_issue.png)

3. **Give it a clear title**  
   Examples:
   - "Suggestion: Shorten session length to 60 minutes"
   - "Question: How do online circles handle silence?"
   - "Feedback: The facilitation guide was confusing on X"

4. **Describe your idea**  
   Include:
   - **What problem does this solve?** (e.g., "New participants find 90 minutes overwhelming")
   - **What are you suggesting?** (e.g., "Offer a 60-minute beginner option")
   - **How does it align with core principles?** (e.g., "Makes practice more accessible")

   ![New issue form filled out](/assets/images/github_issue_filled_out.png)

5. **Submit the issue**  
   Click the green "Submit new issue" button

6. **Join the discussion**  
   - The community can comment, ask questions, discuss
   - You'll get email notifications when someone responds
   - If there's support, someone (maybe you!) can create a formal proposal

### You're Done! 

That's it. You've contributed to the community without writing a single line of code.

---

## Part 2: Making Simple Changes Online

**No software to install. Edit right in your browser.**

This is perfect for:
- Fixing typos or grammar
- Clarifying confusing sentences
- Adding examples or resources
- Small formatting improvements

### Step-by-Step: Editing on GitHub

1. **Fork the repository** (first time only)  
   Go to: [practice_circle](https://github.com/simondilhas/practice_circle)  
   Click the "Fork" button in the top right corner  
   This creates your own copy where you can make changes safely
   
   ![Fork the repository](/assets/images/github_fork.png)
   
   **Note**: If you've already forked it, skip this step!

2. **Find the page you want to edit**  
   Navigate to it on the website, or go directly to:  
   `https://github.com/YOUR_USERNAME/practice_circle/tree/main/docs/`  
   (Replace YOUR_USERNAME with your GitHub username)

3. **Click the file you want to edit**  
   Example: `howto/organize/roles/facilitator.md`

4. **Click the pencil icon** (top right of the file)  
   It says "Edit this file" when you hover over it

5. **Make your changes**  
   - The file opens in a simple text editor
   - You'll see the raw markdown (don't worry, it's readable!)
   - Make your edits just like in a word processor
   
   **Markdown basics** (all you need to know):
   ```markdown
   # Heading 1
   ## Heading 2
   
   **bold text**
   *italic text*
   
   - Bullet point
   - Another point
   
   [Link text](https://example.com)
   ```

   ![GitHub web editor](/assets/images/github_make_changes.png)

6. **Preview your changes** (optional)  
   Click the "Preview" tab to see how it looks

7. **Commit your changes**  
   Scroll down to "Commit changes" section:
   - **Title**: Brief description (e.g., "Fix typo in facilitator guide")
   - **Description**: Explain what you changed and why
   - Make sure "Create a new branch for this commit" is selected
   - Click the green "Commit changes" button

   ![Commit changes form](/assets/images/github_commit.png)

8. **Create a pull request**  
   - On the next page, click "Create pull request"
   - Review the summary, click "Create pull request" again
   - Done! Your suggestion is now visible for review

### What Happens Next?

- Your "pull request" appears in the community queue
- Others can review, comment, suggest improvements
- Once approved (see [Evolve the Circle](../lifecycle/evolve_the_circle.md) for process), it gets merged
- The website updates automatically!

---

## Part 3: Using VS Code (Optional, Not Scary!)

**For bigger changes or if you want to preview locally before submitting.**

VS Code is a free text editor made by Microsoft. Despite being a "developer tool," it's actually quite friendly for editing markdown documents.

### Why Use VS Code?

- Edit multiple files at once
- See the full folder structure
- Preview markdown as you type
- Work on changes over multiple sessions (save drafts locally)
- Better for reorganizing or adding new pages

### First-Time Setup (15 minutes)

1. **Install VS Code**  
   Download from: [code.visualstudio.com](https://code.visualstudio.com/)  
   (It's free and works on Windows, Mac, Linux)

2. **Install Git**  
   Download from: [git-scm.com](https://git-scm.com/)  
   (This lets you download and sync the documents)

3. **Configure Git** (first time only)  
   Open VS Code's terminal (View → Terminal) and run:
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your.email@example.com"
   ```

### Getting the Documents

1. **Fork the repository** (if you haven't already)  
   Go to: [practice_circle](https://github.com/simondilhas/practice_circle)  
   Click the "Fork" button in the top right

2. **Clone your fork**  
   In VS Code:
   - Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac)
   - Type "Git: Clone"
   - Paste: `https://github.com/YOUR_USERNAME/practice_circle.git`  
     (Replace YOUR_USERNAME with your GitHub username)
   - Choose a folder to save it

3. **Open the folder**  
   File → Open Folder → Select the `practice_circle` folder

4. **Create a new branch** (your workspace for changes)  
   In the terminal:
   ```bash
   git checkout -b my-changes
   ```
   (Replace `my-changes` with a short description, e.g., `update-facilitator-guide`)

### Making Changes

1. **Navigate to the file**  
   Use the file explorer on the left side  
   Example: `docs/howto/organize/roles/facilitator.md`

2. **Edit the file**  
   - Just type like in any text editor
   - Install the "Markdown Preview" extension for live preview

3. **Save your work**  
   `Ctrl+S` (or `Cmd+S`)

### Submitting Your Changes

1. **Stage your changes**  
   In the terminal:
   ```bash
   git add .
   ```

2. **Commit your changes**  
   ```bash
   git commit -m "Brief description of what you changed"
   ```

3. **Push to your fork**  
   ```bash
   git push -u origin my-changes
   ```

4. **Create a pull request**  
   - Go to your fork on GitHub: `https://github.com/YOUR_USERNAME/practice_circle`
   - GitHub will show a notification about your recent push
   - Click "Compare & pull request"
   - Add description and submit
   
   Or go directly to:  
   `https://github.com/simondilhas/practice_circle/compare`

### That's It!

Your changes are now submitted for review, just like the web editor method.

---

## Understanding the Review Process

After you submit changes (via either method), they go through a review process. This protects the community while enabling evolution.

**See [Evolve the Circle](../lifecycle/evolve_the_circle.md)** for details on:
- Change tiers (small improvements vs. major changes)
- How review and approval works
- Experimental testing for significant changes
- Timeline expectations

**Key points:**
- Small fixes: Quick approval (1-2 days)
- Bigger changes: Discussion period, testing may be needed
- You'll get feedback and can revise your proposal
- The process is transparent and collaborative

---

## FAQ

### Do I need permission to open an issue?
**No!** Anyone can open an issue. It's just a discussion.

### What if I mess something up?
**Nothing breaks permanently.** Every change is tracked and can be reverted. Don't worry!

### Can I edit without opening an issue first?
**Yes** for small fixes (typos, clarity). **No** for bigger changes—please discuss first so your work isn't wasted if the community doesn't support it.

### How long does review take?
- **Typos/small fixes**: 1-2 days
- **Medium changes**: 1 week
- **Major changes**: 2+ weeks with testing

### What if my pull request gets rejected?
It's not personal! The community might:
- Suggest revisions (you can update and resubmit)
- Explain why it doesn't fit right now
- Ask you to test it first as an experiment

This is collaborative refinement, not judgment.

### I'm still intimidated. Can someone help?
**Yes!** Open an issue saying "I'd like to suggest X but need help with the technical part." Someone will assist you.

---

## Remember

- **Start small**: Fix a typo, clarify a sentence
- **Discussion is valuable**: You don't need to make changes yourself
- **Mistakes are okay**: Everything is reversible
- **Community helps**: Ask questions, request assistance
- **Practice over perfection**: Just like meditation practice, contributing is a practice too

**You're helping shape something meaningful. Thank you.**

