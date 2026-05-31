# 🤖 AI Learning Course — Living Document

> **Maintained by:** [Your Name]
> **Last Updated:** 2026-06-01
> **Source Format:** YouTube Courses, Articles, Documentation
> **Format:** Markdown (Git-compatible, evolving document)

---

## 📑 Table of Contents

1. [Claude Code](#1-claude-code)
2. [Terminal & CLI Basics](#2-terminal--cli-basics)
3. [IDEs & Development Environments](#3-ides--development-environments)
4. [Antigravity IDE](#4-antigravity-ide)
5. [CLAUDE.md — The Project Brain](#5-claudemd--the-project-brain)
6. [Advanced Claude Code Features](#6-advanced-claude-code-features)
7. [Context Management & Token Efficiency](#7-context-management--token-efficiency)
8. [Model Context Protocol (MCP)](#8-model-context-protocol-mcp)
9. [Skills in Claude Code](#9-skills-in-claude-code)
10. [Sub-Agents & Agent Orchestration](#10-sub-agents--agent-orchestration)
11. [Agent Teams](#11-agent-teams)
12. [Git Worktrees for Parallel AI Work](#12-git-worktrees-for-parallel-ai-work)
13. [Cloud Deployment with Modal](#13-cloud-deployment-with-modal)
14. [Building & Selling AI Products](#14-building--selling-ai-products)

---

## Sources Log

| # | Title | Author | Platform | Date Added | Topics Covered |
|---|-------|---------|----------|------------|----------------|
| 1 | CLAUDE CODE FULL COURSE 4 HOURS: Build & Sell (2026) | Nick Saraev | YouTube | 2026-06-01 | Claude Code, Antigravity, MCP, Sub-Agents, Git Worktrees, Modal, Context Management, Skills, Agent Teams |

---

---

# 1. Claude Code

## Overview

**Claude Code** is an AI-powered coding assistant made by Anthropic (the company behind Claude). Unlike simple chatbots, Claude Code works directly inside your development environment (your coding workspace) and can read, write, edit, and run code on your behalf. Think of it like having a very smart programming partner who can actually reach into your project and make changes — not just suggest them in a chat box.

In Nick Saraev's 2026 course, Claude Code is positioned as the central tool for building full applications, automating workflows, and running complex multi-agent pipelines — all without needing deep programming experience.

---

## Key Concepts

### 1.1 What Claude Code Actually Does

Claude Code operates as an **agentic AI assistant**. This means it does not just answer questions — it takes *actions*. When you give Claude Code a task like "build me a website with a contact form," it will:

1. Create files and folders in your project
2. Write all the necessary code
3. Run tests or preview servers if needed
4. Iterate and fix errors it encounters

This is fundamentally different from tools like ChatGPT where you copy-paste code yourself. Claude Code acts autonomously within defined boundaries.

### 1.2 Claude Code vs. Traditional Coding

| Feature | Traditional Coding | Claude Code |
|---|---|---|
| Who writes the code | You (human) | Claude (AI) + You (directing) |
| Speed | Hours/days | Minutes |
| Knowledge required | Deep programming skill | High-level instruction skill |
| Error handling | Manual debugging | AI self-corrects |
| Scalability | Limited by your time | Parallelized with agents |

### 1.3 How Claude Code Fits Into a Workflow

A typical Claude Code workflow looks like this:

1. **You open your IDE** (e.g., Antigravity or VS Code)
2. **You start a Claude Code session** in the terminal or GUI
3. **You write instructions** in plain English (or with technical detail)
4. **Claude builds, edits, or debugs** your project
5. **You verify the output**, request changes, and iterate

### 1.4 The "Agentic Loop"

Claude Code works in what's called an **agentic loop** — a cycle where it:
- **Observes** the current state of your project (reads files, sees errors)
- **Plans** what to do (decides which files to edit)
- **Acts** (writes/changes code)
- **Verifies** (checks if the result is correct)
- **Repeats** until the task is done

This is why it's called "agentic" — it has *agency*, meaning it can make decisions and take multiple steps on its own.

---

## Terminology

| Term | Definition |
|------|------------|
| **Claude Code** | Anthropic's AI coding agent that works inside your development environment |
| **Anthropic** | The AI safety company that created Claude |
| **Agentic AI** | AI that takes autonomous, multi-step actions to complete tasks |
| **Agentic Loop** | The repeating cycle of observe → plan → act → verify |
| **Prompt** | The instruction or request you give to Claude |
| **Context Window** | The maximum amount of text/code Claude can "see" at one time |
| **Token** | The basic unit Claude uses to read/write text (roughly ¾ of a word) |
| **Session** | One continuous conversation/working period with Claude Code |

---

## Examples

**Example 1: Building a web app in under 15 minutes**

Nick demonstrates in the course: you can open Claude Code in Antigravity, type "build me a landing page for a freelance photography business with a contact form and pricing section," and Claude will create an entire working web app in minutes — complete with HTML, CSS, and JavaScript.

**Example 2: Debugging**

If a page isn't loading correctly, you describe the problem to Claude Code: "The submit button doesn't work on mobile." Claude reads your code, identifies the issue, and fixes it — without you touching any code.

**Example 3: Email Classification App**

One full project in the course is building a Gmail classifier — an app that reads your emails and labels them into categories automatically. This is done entirely with Claude Code in an afternoon.

---

## Common Doubts

**Q: Do I need to know how to code to use Claude Code?**
A: No — but knowing *some* basics helps you verify that what Claude built is correct. The course teaches you how to "verify" outputs even without deep coding knowledge. You give instructions in English, Claude writes the code.

**Q: Is Claude Code the same as GitHub Copilot or Cursor?**
A: They're similar in concept but different in power. Copilot is a code *suggester* (autocompletes lines). Cursor is more agentic but still tied to one file. Claude Code is fully agentic — it can manage your whole project, run commands, and work across many files at once.

**Q: Will Claude Code break my existing code?**
A: It can make mistakes. That's why the course emphasizes **verification** (checking every output) and **Git** (version control — so you can always roll back changes).

**Q: Is it expensive to run?**
A: Claude Code uses tokens, which cost money. The course dedicates a whole section to **token management** to help you minimize costs.

---

## Interview Questions

**Q1: What is Claude Code and how does it differ from a traditional AI chatbot?**
> Claude Code is an agentic AI coding assistant. Unlike chatbots that respond in conversation, Claude Code takes autonomous multi-step actions inside your development environment — reading, writing, editing, and running code on your behalf.

**Q2: What does "agentic" mean in the context of AI?**
> Agentic AI systems can make sequential decisions and take actions to complete longer-horizon tasks without requiring step-by-step human guidance. They observe context, plan, act, and verify in a loop.

**Q3: What is a token in AI systems?**
> A token is the basic unit of text that language models process. One token ≈ 3-4 characters or ¾ of an English word. Costs and context limits are measured in tokens.

**Q4: Why is context window size important for Claude Code?**
> The context window limits how much code/instructions Claude can "see" at once. If your project is too large, Claude may lose track of earlier instructions. This is why context management strategies (like CLAUDE.md and Skills) are critical.

---

## Industry Usage

- **Freelancers** use Claude Code to build client websites and automation tools in hours instead of days
- **Startup founders** prototype products without a full engineering team
- **Content agencies** automate content pipelines (e.g., Nick's own 7-figure 1SecondCopy business)
- **Developers** use it to parallelize work — running multiple Claude Code instances simultaneously on different features

---

## Related Topics

- [CLAUDE.md — The Project Brain](#5-claudemd--the-project-brain)
- [Context Management & Token Efficiency](#7-context-management--token-efficiency)
- [Sub-Agents & Agent Orchestration](#10-sub-agents--agent-orchestration)
- [Git Worktrees for Parallel AI Work](#12-git-worktrees-for-parallel-ai-work)

---

## Revision Notes

- Claude Code = AI that writes code AND takes actions in your project
- Works via an agentic loop: observe → plan → act → verify
- No deep coding knowledge needed, but verification skills are important
- Costs are measured in tokens — always monitor token usage
- Works best inside an IDE (Antigravity recommended in this course)

---

---

# 2. Terminal & CLI Basics

## Overview

The **terminal** (also called command line, CLI, or shell) is a text-based interface for controlling your computer. Instead of clicking buttons and icons, you type commands. Claude Code is launched and runs primarily through the terminal, so understanding basic terminal concepts is essential.

---

## Key Concepts

### 2.1 Terminal vs. Graphical User Interface (GUI)

- A **GUI** (Graphical User Interface) is what most people are familiar with: windows, icons, mouse clicks. Examples: Finder on Mac, Windows Explorer.
- A **Terminal** (or CLI — Command Line Interface) is text-only. You type commands, press Enter, and the computer responds with text output.

**Why does it matter for Claude Code?**
Claude Code runs as a terminal application. When you start a Claude Code session, you type commands in the terminal. This is where you instruct Claude, see its progress, and review outputs.

### 2.2 Key Terminal Concepts

| Concept | Explanation |
|---------|-------------|
| **Directory** | A folder. `cd foldername` moves you into it |
| **File Path** | The address of a file, e.g., `/home/user/project/app.py` |
| **Command** | An instruction you type, e.g., `ls` to list files |
| **Shell** | The program that interprets your terminal commands (e.g., bash, zsh) |
| **Environment Variable** | Hidden settings stored on your system, like API keys |
| **Process** | A running program |

### 2.3 Essential Terminal Commands for Claude Code Users

```bash
cd foldername      # Navigate into a folder
cd ..              # Go up one level
ls                 # List files in current directory
pwd                # Show current directory path
mkdir foldername   # Create a new folder
cat filename.txt   # Print file contents
claude             # Start a Claude Code session
```

---

## Terminology

| Term | Definition |
|------|------------|
| **CLI** | Command Line Interface — text-based computer control |
| **Terminal** | The window/app where you type CLI commands |
| **Shell** | The language interpreter for terminal commands (bash, zsh, fish) |
| **stdin/stdout** | Standard input (keyboard) / standard output (screen text) |
| **Environment Variable** | Key-value pair stored in the OS, often used for secrets like API keys |

---

## Common Doubts

**Q: Is the terminal the same on Mac, Windows, and Linux?**
A: Similar but not identical. Mac/Linux use Unix-based shells (bash/zsh). Windows has Command Prompt and PowerShell. For Claude Code, Mac and Linux are most natively supported; Windows users often use WSL (Windows Subsystem for Linux).

**Q: Do I need to memorize all terminal commands?**
A: No. You only need a handful to navigate and run Claude Code. Claude itself can also write and run terminal commands on your behalf.

---

## Interview Questions

**Q1: What is the difference between a terminal and an IDE?**
> A terminal is a text-based interface for running commands on your operating system. An IDE (Integrated Development Environment) is a graphical application that provides code editing, syntax highlighting, file management, and often an embedded terminal — all in one place.

**Q2: What is an environment variable and why is it used for API keys?**
> An environment variable is a named value stored at the OS level, accessible by programs. API keys are stored as environment variables rather than hardcoded in files to prevent accidental exposure (e.g., in public Git repos).

---

## Industry Usage

Every software developer uses the terminal daily. For AI workflows with Claude Code, you'll use the terminal to: launch sessions, manage files, run scripts, set environment variables, and deploy to cloud services.

---

## Related Topics

- [IDEs & Development Environments](#3-ides--development-environments)
- [Claude Code](#1-claude-code)
- [Git Worktrees for Parallel AI Work](#12-git-worktrees-for-parallel-ai-work)

---

## Revision Notes

- Terminal = text-based computer control
- GUI = graphical (icons, mouse); CLI = text (commands, keyboard)
- Claude Code is launched from the terminal
- Key commands: `cd`, `ls`, `pwd`, `mkdir`
- API keys are stored as environment variables for security

---

---

# 3. IDEs & Development Environments

## Overview

An **IDE (Integrated Development Environment)** is a software application that provides everything a developer needs in one place: a code editor, file browser, terminal, and often AI assistance. This is your "workbench" when building projects with Claude Code.

---

## Key Concepts

### 3.1 What Is an IDE?

An IDE bundles together:
- **Code Editor**: Where you write and view code (with syntax coloring)
- **File Explorer**: Shows the structure of your project
- **Terminal**: An embedded command line
- **Extensions/Plugins**: Add-ons for extra features (Git, linters, AI)
- **Debugger**: Tools to find and fix errors

### 3.2 Visual Studio Code (VS Code)

**VS Code** is the most popular free IDE in the world, made by Microsoft. Key features:

- Extremely extensible via extensions
- Has a built-in terminal
- Works with every programming language
- Free and open source
- Used in the Claude Code course as a reference

### 3.3 Why the IDE Choice Matters for Claude Code

Claude Code works within your IDE's file system. A well-configured IDE makes it easier to:
- See changes Claude makes in real-time
- Preview running applications
- Manage multiple project files
- Review diffs (what changed) before accepting

---

## Terminology

| Term | Definition |
|------|------------|
| **IDE** | Integrated Development Environment — all-in-one coding workspace |
| **VS Code** | Visual Studio Code, the most popular free IDE (made by Microsoft) |
| **Extension** | A plugin that adds features to your IDE |
| **Syntax Highlighting** | Color-coding code by type (keywords, strings, variables) |
| **Linter** | A tool that checks your code for errors and style issues |
| **Diff** | A comparison showing what changed between two versions of a file |

---

## Common Doubts

**Q: Can I use Claude Code without an IDE?**
A: Yes — Claude Code runs in the terminal and works on plain project folders. But an IDE makes your workflow dramatically smoother, especially for reviewing Claude's changes.

**Q: Should I use VS Code or Antigravity?**
A: For beginners, the course recommends **Antigravity** because it's designed specifically for AI-assisted coding. VS Code is more powerful for traditional developers. Both work with Claude Code.

---

## Interview Questions

**Q1: What is the difference between a text editor and an IDE?**
> A text editor (like Notepad) only edits text. An IDE adds features like debugging, version control integration, terminal access, intelligent code completion, and project management — making it a complete development platform.

---

## Related Topics

- [Antigravity IDE](#4-antigravity-ide)
- [Claude Code](#1-claude-code)

---

## Revision Notes

- IDE = all-in-one coding workspace
- VS Code = most popular free IDE; great for general development
- Antigravity = AI-native IDE recommended in this course
- IDEs include: editor, file browser, terminal, debugger, extensions
- Claude Code works in the terminal *within* your IDE

---

---

# 4. Antigravity IDE

## Overview

**Antigravity** (also called "Antigravity IDE") is an AI-native development environment specifically designed for working with AI coding assistants like Claude Code. It is Nick Saraev's recommended IDE for this course. Unlike VS Code (which was designed for human coders and later got AI features), Antigravity is built from the ground up to make AI-assisted development smooth and visual.

> **Note from Nick (pinned comment):** Antigravity updated its interface after the course was filmed. To match what's shown in the course, install **"Antigravity IDE"** specifically.

---

## Key Concepts

### 4.1 What Makes Antigravity Different

- **AI-first design**: Every panel and feature is oriented around AI assistance
- **Visual project browser**: Easier for beginners to see what Claude is doing
- **Integrated Claude Code**: Launch and monitor Claude sessions directly
- **Preview panel**: See your web app update in real-time as Claude codes
- **Tight Git integration**: Review Claude's changes before committing

### 4.2 Getting Started with Antigravity

Steps covered in the course:
1. Download and install Antigravity IDE
2. Open or create a project folder
3. Set up your Anthropic API key as an environment variable
4. Launch a Claude Code session within Antigravity
5. Start giving instructions in natural language

### 4.3 Building Your First App

The course demonstrates building a complete web app in under 15 minutes:
1. Open a new project in Antigravity
2. Tell Claude: "Build a web app for [purpose] with [features]"
3. Claude writes all the code
4. Preview it in the built-in browser panel
5. Iterate: "Make the button red" / "Add a login form"

---

## Terminology

| Term | Definition |
|------|------------|
| **Antigravity** | AI-native IDE optimized for Claude Code and AI-assisted coding |
| **Antigravity IDE** | The specific version to install (post-update to match course) |
| **Preview Panel** | Live browser preview of your web app inside the IDE |
| **Project Folder** | The directory that contains all your project files |

---

## Common Doubts

**Q: Is Antigravity free?**
A: As of the course date (Feb 2026), there is a free tier. Check the current pricing on the Antigravity website.

**Q: What if Antigravity looks different from the course?**
A: Install "Antigravity IDE" (the specific version) to match the course interface, as noted in Nick's pinned comment.

---

## Industry Usage

AI-native IDEs like Antigravity represent the cutting edge of developer tooling in 2026. They are used by indie developers, freelancers, and small product teams that want to maximize AI leverage.

---

## Related Topics

- [IDEs & Development Environments](#3-ides--development-environments)
- [Claude Code](#1-claude-code)
- [CLAUDE.md — The Project Brain](#5-claudemd--the-project-brain)

---

## Revision Notes

- Antigravity = AI-first IDE, built for Claude Code workflows
- Recommended over VS Code for beginners in this course
- Install "Antigravity IDE" for the version shown in the course
- Provides: live preview, integrated Claude, visual file browser, Git diff viewer
- First app can be built in under 15 minutes using Antigravity + Claude Code

---

---

# 5. CLAUDE.md — The Project Brain

## Overview

**CLAUDE.md** is a special file you place at the root of your project folder. It acts as the **"project brain"** — a persistent memory document that Claude Code reads at the start of every session. Since Claude doesn't remember previous sessions by default (it has no persistent memory), CLAUDE.md is how you give it the context it needs: what your project is, how it's structured, what conventions to follow, and what tools to use.

Think of it like a briefing document you hand to a new contractor before they start working.

---

## Key Concepts

### 5.1 Why CLAUDE.md Is Essential

Without CLAUDE.md, every time you start a new Claude Code session, Claude starts "fresh" — it doesn't know:
- What your project does
- How your files are organized
- What coding style you prefer
- What APIs and tools are connected
- What has already been built

With CLAUDE.md, Claude reads this file first and becomes immediately context-aware, saving you from re-explaining everything each session.

### 5.2 What Goes in CLAUDE.md

A well-written CLAUDE.md typically includes:

```markdown
# Project: [Your Project Name]

## Purpose
Brief description of what this project does.

## Tech Stack
- Frontend: React, Tailwind CSS
- Backend: Python, FastAPI
- Database: PostgreSQL
- Deployment: Modal

## File Structure
/src         - Frontend code
/api         - Backend API routes
/scripts     - Utility scripts

## Coding Conventions
- Use 2 spaces for indentation
- Always write comments for non-obvious logic
- Function names should be descriptive verbs

## Important Rules
- Never delete files without asking
- Always run tests before committing
- Use environment variables for all API keys

## Current Status
- [x] User authentication complete
- [ ] Payment integration in progress
- [ ] Email notifications pending
```

### 5.3 CLAUDE.md as a Living Document

CLAUDE.md should be **updated as your project grows**. When Claude builds a new feature, add it to the project status. When you establish a new convention, add it to the rules. Over time, CLAUDE.md becomes a comprehensive spec for your entire project.

### 5.4 The `.claude` Directory

Related to CLAUDE.md is the `.claude` directory (hidden folder). This is where Claude Code stores:
- **Slash command definitions** (custom shortcuts)
- **Hook configurations** (automatic actions on events)
- **Plugin settings**
- **Skills** (reusable task templates)

---

## Terminology

| Term | Definition |
|------|------------|
| **CLAUDE.md** | A project-level Markdown file that acts as Claude Code's persistent memory |
| **.claude directory** | Hidden folder where Claude stores hooks, commands, skills, and configs |
| **Project Brain** | Nickname for CLAUDE.md — the persistent context document |
| **Tech Stack** | The collection of technologies used in a project |
| **Convention** | An agreed-upon rule or style standard for how code is written |

---

## Examples

**Example: E-commerce project CLAUDE.md excerpt**

```markdown
# Project: ShopBot

## Purpose
An automated e-commerce store that processes orders and sends confirmation emails.

## Rules
- All database writes must be wrapped in try/catch blocks
- Never hardcode prices — always fetch from the database
- Email confirmations use the Resend API (key in .env as RESEND_API_KEY)

## Current Known Issues
- Checkout sometimes times out on slow connections (investigating)
```

---

## Common Doubts

**Q: Does Claude actually read CLAUDE.md every time?**
A: Yes — Claude Code is configured to load CLAUDE.md at the start of each session. This is one of the most important conventions to set up properly.

**Q: Should CLAUDE.md be committed to Git?**
A: Generally yes, so the whole team benefits. But omit sensitive details — API keys should always be in `.env` files (which are in `.gitignore`), never in CLAUDE.md.

**Q: Can I have multiple CLAUDE.md files?**
A: Yes — you can place them in subdirectories for specific components, and Claude will read the appropriate one based on context.

---

## Interview Questions

**Q1: What is CLAUDE.md and why is it important?**
> CLAUDE.md is a Markdown file at the project root that provides Claude Code with persistent context about the project. Since Claude has no cross-session memory, this file acts as a briefing document — covering project purpose, tech stack, conventions, and status. Without it, Claude starts "blank" every session.

**Q2: How does CLAUDE.md relate to the concept of "context" in AI?**
> Context is the information an AI has available when processing a request. CLAUDE.md front-loads critical project context so Claude doesn't waste tokens re-discovering the project structure. It's a form of "long-term memory injection" into a stateless AI system.

---

## Industry Usage

- Large engineering teams maintain detailed CLAUDE.md files as a form of AI onboarding documentation
- Solo developers use CLAUDE.md to stay consistent across days/weeks of development
- The CLAUDE.md pattern is becoming a standard convention across AI coding tools

---

## Related Topics

- [Claude Code](#1-claude-code)
- [Context Management & Token Efficiency](#7-context-management--token-efficiency)
- [Skills in Claude Code](#9-skills-in-claude-code)

---

## Revision Notes

- CLAUDE.md = persistent project memory for Claude
- Placed at project root; read by Claude at session start
- Contains: project purpose, tech stack, file structure, rules, current status
- The `.claude/` directory stores hooks, commands, plugins, skills
- Update CLAUDE.md as the project evolves — it's a living document
- **Never** put API keys or secrets in CLAUDE.md

---

---

# 6. Advanced Claude Code Features

## Overview

Beyond basic prompting, Claude Code has a rich set of advanced features that dramatically increase productivity: **Hooks**, **Slash Commands**, **Plugins**, and integration with external services. The course dedicates a significant portion to these features (starting around the 54-minute mark).

---

## Key Concepts

### 6.1 Hooks

**Hooks** are automatic actions that run when specific events happen in Claude Code. Think of them as "triggers."

Examples:
- **Pre-commit hook**: Before Claude commits code to Git, automatically run tests
- **Post-edit hook**: After Claude edits a file, automatically format the code
- **Error hook**: When Claude encounters an error, automatically notify you via a specific message format

Hooks are defined in the `.claude/` directory and help automate repetitive safeguards.

### 6.2 Slash Commands

**Slash commands** are custom shortcuts you define to give Claude quick, reusable instructions.

Example slash commands:
- `/deploy` → Triggers a standard deployment process
- `/test` → Runs the test suite and reports results
- `/summarize` → Creates a summary of recent changes
- `/refactor [filename]` → Refactors a specific file to match conventions

You define them in `.claude/commands/` as Markdown files.

```markdown
# /deploy

Run the following steps in order:
1. Run all tests (abort if any fail)
2. Build the production bundle
3. Deploy to Modal
4. Send a Slack notification with the deployment URL
```

### 6.3 Plugins

**Plugins** in Claude Code (introduced around 3:09 in the course) extend Claude's capabilities by connecting it to external tools and APIs. Plugins are similar to "tools" in agent frameworks — they give Claude new abilities beyond code editing.

Examples:
- **Gmail plugin**: Claude can read and label your emails
- **GitHub plugin**: Claude can create issues, manage PRs
- **Notion plugin**: Claude can update your project notes
- **Web search plugin**: Claude can look up information online

### 6.4 The .claude Directory Structure

```
.claude/
├── commands/        # Slash command definitions
│   ├── deploy.md
│   └── test.md
├── hooks/           # Event-triggered automations
│   ├── pre_commit.sh
│   └── post_edit.sh
├── skills/          # Reusable task templates (see Skills section)
└── settings.json    # Global Claude Code configuration
```

---

## Terminology

| Term | Definition |
|------|------------|
| **Hook** | An automatic action triggered by a specific event in Claude Code |
| **Slash Command** | A `/keyword` shortcut for a complex, reusable instruction |
| **Plugin** | An extension that gives Claude Code access to external tools/services |
| **.claude directory** | Hidden folder where all Claude Code configurations live |
| **Pre/Post Hook** | Hooks that run before or after a specific action |

---

## Common Doubts

**Q: Are hooks like webhooks?**
A: Conceptually similar but different in scope. Webhooks are triggered by external HTTP events (from other services). Claude Code hooks are triggered by local events within your Claude Code session (like editing a file or committing code).

**Q: Do I need to know bash to write hooks?**
A: Basic hooks can be simple shell scripts. Claude Code can actually help you write them — just describe what you want the hook to do.

---

## Interview Questions

**Q1: What are hooks in the context of Claude Code?**
> Hooks are event-triggered automations in Claude Code. They run automatically when specific events occur (e.g., pre-commit, post-file-edit). They're used to enforce quality gates, run tests, format code, and automate repetitive processes.

**Q2: What is the purpose of slash commands?**
> Slash commands are custom keyboard shortcuts that trigger complex, multi-step instructions. Instead of typing a long prompt each time, you define `/command` once and reuse it, making workflows faster and more consistent.

---

## Industry Usage

- Teams use hooks to enforce coding standards and run tests automatically
- Slash commands standardize common workflows across team members
- Plugins connect Claude Code to business tools (Gmail, Slack, Notion, GitHub)

---

## Related Topics

- [CLAUDE.md — The Project Brain](#5-claudemd--the-project-brain)
- [Model Context Protocol (MCP)](#8-model-context-protocol-mcp)
- [Skills in Claude Code](#9-skills-in-claude-code)

---

## Revision Notes

- **Hooks** = automatic triggers (pre/post events)
- **Slash Commands** = `/keyword` shortcuts for reusable instructions
- **Plugins** = extensions connecting Claude to external services
- All configured in the `.claude/` directory
- Hooks enforce quality; commands increase speed; plugins expand reach

---

---

# 7. Context Management & Token Efficiency

## Overview

**Context** is everything Claude can "see" during a session — your instructions, project files, conversation history, and any tool outputs. **Tokens** are the unit of measurement for this context. Managing context and tokens efficiently is one of the most important skills for working with Claude Code at scale, and the course dedicates a full section to it (starting ~2:13:53).

---

## Key Concepts

### 7.1 What Is the Context Window?

The context window is the maximum amount of text Claude can process at once. Think of it like working memory — Claude can only "think about" what's currently in the window.

- Claude 3 models have context windows ranging from **200K to 1M+ tokens**
- 1 token ≈ ¾ of an English word, or ~4 characters
- A 200K token window ≈ roughly 150,000 words ≈ a short novel

**Why it matters:** If your codebase is huge or your session is long, older parts of the conversation "fall off" the context window, causing Claude to lose track of earlier instructions.

### 7.2 Token Costs

Every token costs money. Claude Code is billed by:
- **Input tokens**: What you send to Claude (your prompts, files, history)
- **Output tokens**: What Claude generates (code, explanations, etc.)

Output tokens are typically more expensive than input tokens.

### 7.3 Strategies for Token Management

The course (2:27:23) covers these strategies:

**1. CLAUDE.md for persistent context** (avoids re-explaining every session)

**2. Compact summaries** — Instead of keeping full conversation history, periodically ask Claude to summarize the session so far, then start fresh with that summary.

**3. File-based context** — Rather than pasting huge files into the chat, tell Claude to `read file.py` — this is more efficient than including the full file in your prompt.

**4. Skills** — Pre-written task templates that avoid long prompt explanations (see Skills section)

**5. Scoped tasks** — Break large tasks into smaller pieces. Instead of "Build the whole app," do "Build the login system first."

**6. Use /compact or /clear commands** — Reset context when you start a new task.

### 7.4 Understanding Token "Burn Rate"

The course teaches how to monitor your token usage:
- Track tokens per task
- Identify expensive operations (large file reads, long explanations)
- Use tools/MCPs that are token-efficient

---

## Terminology

| Term | Definition |
|------|------------|
| **Context Window** | The maximum text Claude can process in one session |
| **Token** | The basic unit of AI text processing (~¾ of a word) |
| **Input Tokens** | Tokens you send to Claude (your prompts, files) |
| **Output Tokens** | Tokens Claude generates (code, text responses) |
| **Context Management** | Strategies to maximize useful context while minimizing cost |
| **Token Burn Rate** | How quickly you're consuming tokens in a session |
| **/compact** | A Claude Code command to compress context history |

---

## Common Doubts

**Q: What happens when Claude "runs out" of context?**
A: The oldest parts of the conversation are dropped. Claud
