# AI Learning Course — Module 1: Claude Code

> **Source:** [CLAUDE CODE FULL COURSE 4 HOURS: Build & Sell (2026)](https://www.youtube.com/watch?v=QoQBzR1NIqI)  
> **Instructor:** Nick Saraev  
> **Duration:** 4 hours 10 minutes  
> **Date Added:** 2026-06-01  
> **Level:** Beginner → Intermediate  
> **Version:** 1.0

---

## Table of Contents

1. [Overview](#1-overview)
2. [Key Concepts](#2-key-concepts)
3. [Terminology](#3-terminology)
4. [Tools & Environment Setup](#4-tools--environment-setup)
5. [Examples & Walkthroughs](#5-examples--walkthroughs)
6. [Common Doubts & Beginner Questions](#6-common-doubts--beginner-questions)
7. [Interview Questions](#7-interview-questions)
8. [Industry Usage](#8-industry-usage)
9. [Related Topics](#9-related-topics)
10. [Revision Notes](#10-revision-notes)

---

## 1. Overview

### What is Claude Code?

Claude Code is an **agentic AI coding tool** developed by Anthropic, built on top of the Claude large language model (LLM). Unlike a standard chatbot where you ask a question and get a text answer, Claude Code works directly inside your terminal or development environment — it reads your files, writes code, runs commands, checks outputs, and iterates autonomously until a task is done.

Think of it like hiring a very capable software engineer who lives inside your terminal and can write, test, debug, and deploy code for you — while you guide it at a high level with plain English instructions.

**Key capability in one sentence:** Claude Code turns natural language instructions into working software, running autonomously in an agentic loop.

### What This Course Covers

This course is a full end-to-end journey covering:

- Setting up Claude Code from scratch
- Understanding the development environment (terminal, IDEs, Antigravity)
- Building your first web app using AI in under 15 minutes
- Using the `CLAUDE.md` file as a "project brain"
- Advanced features: hooks, slash commands, the `.claude` directory
- Context management and token efficiency
- Model Context Protocol (MCP) for connecting AI to external tools
- Skills (reusable automation building blocks)
- Sub-Agents (autonomous specialists that work in parallel)
- Agent Teams (orchestrated fleets of sub-agents)
- Git Worktrees for parallel development
- Deploying APIs to the cloud using Modal

---

## 2. Key Concepts

### 2.1 Claude Code — The Agentic Loop

**What it is:** Claude Code operates in a loop: you give it a goal → it writes code or runs a command → it checks the result → it decides the next step → it loops until done.

**Why it matters:** Traditional tools require you to write every line of code manually. Claude Code handles entire tasks autonomously, only stopping to ask you questions when it's uncertain.

**How the loop works:**
1. You provide a task in plain English (e.g., "Build a landing page with a payment form")
2. Claude reads your files and context
3. It decides what to do next (write a file, run a command, call an API)
4. It executes the action
5. It checks if the result was correct
6. It loops back to step 3 until the task is complete

**Important:** Claude Code is most effective when given **clear, specific goals**. Vague instructions like "make it better" produce poor results.

---

### 2.2 Terminal vs. Graphical User Interface (GUI)

**Terminal (CLI — Command Line Interface):**  
A text-based interface where you type commands directly into your computer. No buttons, no menus — just text. Claude Code natively runs in the terminal.

Example terminal command: `claude "Build a login page"`

**GUI (Graphical User Interface):**  
A visual interface with buttons, windows, and menus (like VS Code or Antigravity). Easier for beginners to navigate but less powerful for automation.

**Why Claude Code uses the terminal:** The terminal gives Claude Code full, unrestricted access to your filesystem and system commands — it can create files, install packages, run tests, and deploy — all without needing a mouse.

**Beginner tip:** You don't need to be a terminal expert. The course teaches you everything you need. Most interactions are just typing `claude "your task"`.

---

### 2.3 Integrated Development Environments (IDEs)

**What is an IDE?**  
An Integrated Development Environment is a software application that combines all the tools a developer needs: a code editor, file explorer, terminal, and debugger — in one place.

**Examples covered in this course:**
- **Visual Studio Code (VS Code):** The most popular free IDE. Has syntax highlighting, extensions, and a built-in terminal.
- **Antigravity (now "Antigravity IDE"):** The IDE Nick uses in this course. Built specifically for AI-assisted coding and integrates tightly with Claude Code. It provides a more visual interface for managing Claude Code sessions.

**Why IDEs matter for Claude Code:** IDEs let you visually monitor what Claude Code is doing — see files being created, review code, and interact with the project without only using the terminal.

> **Note (June 2026):** The course originally used "Antigravity," but the interface was updated. To follow along with the course visuals, install **"Antigravity IDE"** specifically.

---

### 2.4 The CLAUDE.md File — The Project Brain

**What it is:** `CLAUDE.md` is a special Markdown file you place at the root of your project. Claude Code automatically reads this file at the start of every session. It acts as persistent memory and instructions for the AI.

**Why it's critical:** By default, Claude Code forgets everything between sessions (due to context window limits). The `CLAUDE.md` file is the solution — it gives Claude a "briefing document" every time it starts work on your project.

**What to put in CLAUDE.md:**
- Project description and goals
- Tech stack (e.g., "This project uses React, TypeScript, and Supabase")
- Code style rules (e.g., "Always use 2-space indentation")
- File structure overview
- Important commands (e.g., how to run tests, how to deploy)
- Business logic explanations
- Things Claude should never do (e.g., "Never delete the /data folder")

**Example CLAUDE.md snippet:**
```markdown
# Project: SaaS Landing Page
## Stack: Next.js, Tailwind CSS, Stripe
## Commands:
- Dev server: `npm run dev`
- Deploy: `npm run build && vercel deploy`
## Rules:
- Always verify payment flows before marking complete
- Use TypeScript strict mode
```

**Industry analogy:** The `CLAUDE.md` is like an employee handbook for your AI developer. It tells Claude everything it needs to know before starting work.

---

### 2.5 The .claude Directory

**What it is:** A hidden folder (`.claude/`) created by Claude Code in your project root. It stores project-specific settings, custom commands, hooks, and skill definitions.

**Key files inside `.claude/`:**
- `settings.json` — Project configuration for Claude Code
- `commands/` — Custom slash commands
- `hooks/` — Automated actions that trigger on events
- `skills/` — Reusable task modules (explained in Section 2.8)

**Why it matters:** The `.claude` directory is what makes Claude Code customizable. You can program Claude to behave differently for each project by defining rules, shortcuts, and automations here.

---

### 2.6 Context Management and Token Efficiency

**What is a "context window"?**  
Claude (like all LLMs) can only "see" a limited amount of text at once. This limit is measured in **tokens** (roughly 1 token = 0.75 words). The maximum amount of text Claude can process in one session is called the **context window**.

**Why it matters for coding:** In a large codebase, Claude might run out of context before finishing a task. Managing context efficiently = faster, cheaper, more reliable AI coding.

**Strategies taught in the course:**

1. **CLAUDE.md compression** — Keep the project brain concise and well-organized. Don't dump your entire codebase in it.

2. **Scoped tasks** — Instead of "build the whole app," give Claude small, focused tasks ("build just the login component"). This uses fewer tokens per task.

3. **Fresh sessions for new tasks** — Start a new Claude Code session for unrelated tasks to avoid context pollution.

4. **`.claudeignore` file** — Similar to `.gitignore`, this tells Claude to ignore certain files (like `node_modules/` or large data files) to save tokens.

5. **Summarization** — Before a long session, ask Claude to summarize what it knows about the project into bullet points, then use that summary to restart.

**Token cost awareness:** Claude Code calls the Anthropic API, which costs money per token. Good context management = lower API costs.

---

### 2.7 Model Context Protocol (MCP)

**What is MCP?**  
Model Context Protocol is an open standard (developed by Anthropic) that defines how AI models connect to external tools, data sources, and services. Think of it as a **universal plugin system for AI**.

**The problem MCP solves:** Without MCP, to connect Claude to Gmail, a database, or a web browser, you'd need to write custom integration code for each one. MCP standardizes this — any MCP-compatible tool can plug into any MCP-compatible AI model.

**How it works:**
1. An **MCP Server** wraps a tool (e.g., Gmail, Postgres, Slack)
2. Claude Code connects to the MCP server
3. Claude can now call that tool as if it were a built-in function

**Real-world analogy:** MCP is to AI what the USB standard is to hardware. Before USB, every device needed a different port. After USB, one standard connects everything.

**MCP in this course covers:**
- Connecting Claude to Gmail (read emails, classify labels)
- Evaluating token costs when using MCP tools
- Practical MCP plugin exploration inside Claude Code

**Important insight:** MCPs significantly extend what Claude Code can do autonomously — reading your emails, browsing the web, querying databases — without you writing a single line of integration code.

---

### 2.8 Skills — Reusable Automation Modules

**What is a Skill?**  
A Skill is a reusable, parameterized task definition stored in your `.claude` directory. Instead of writing the same prompt or instructions every time you want Claude to do a repeated task, you define it once as a Skill and invoke it with a slash command.

**Analogy:** Skills are like functions in programming. Instead of copy-pasting the same code everywhere, you write a function once and call it by name.

**Structure of a Skill:**


**Example skill definition (classify-email.md):**
```markdown
# Skill: Classify Email
## Purpose: Categorize an incoming email by urgency and topic
## Inputs: email_subject, email_body
## Steps:
1. Read the email content
2. Identify the topic (support, sales, spam, urgent)
3. Apply the appropriate Gmail label
4. Return the classification result
```

**How to invoke:** Type `/classify-email` in Claude Code and it follows the defined steps.

**Why Skills matter for business:** Skills let non-technical users define business logic in plain English and have Claude execute it reliably and repeatedly — no programming required.

---

### 2.9 Sub-Agents

**What is a Sub-Agent?**  
A Sub-Agent is an autonomous Claude instance that runs in the background, independently executing a specific task while you (or a parent agent) continue other work. Sub-Agents are the key to **parallelism** in Claude Code workflows.

**The parent-child relationship:**
- **Parent Agent** (you / main Claude session) — Assigns tasks and coordinates
- **Sub-Agent** — Receives a specific task, executes it autonomously, reports back

**Why Sub-Agents are powerful:** Instead of doing tasks sequentially (one after another), Sub-Agents let you do them in parallel. A parent agent can spin up 5 Sub-Agents simultaneously — one writing tests, one writing documentation, one designing the UI, one setting up the database, one writing the backend.

**Transforming a Skill into a Sub-Agent:** A skill definition can be promoted to a Sub-Agent by adding execution context — giving it permissions to read/write files, call APIs, and make decisions autonomously.

**Real-world example from the course:**  
Email classification workflow:
1. Parent Agent reads new emails
2. Spawns a Sub-Agent per email: "Classify this email"
3. Each Sub-Agent runs in parallel
4. Results are aggregated and Gmail labels are applied

This scales an email classification task from minutes to seconds.

---

### 2.10 Agent Teams

**What is an Agent Team?**  
An Agent Team is a coordinated group of Sub-Agents working together on a larger goal, orchestrated by a parent agent. This is the foundation of multi-agent AI systems.

**Architecture:**

**How Agent Teams work:**
1. Parent agent receives a high-level goal (e.g., "Build a contact form with email notifications")
2. Parent decomposes it into sub-tasks
3. Assigns sub-tasks to specialized Sub-Agents
4. Sub-Agents execute in parallel
5. Parent agent reviews and integrates results

**The "Plan" concept:** Before spawning Sub-Agents, Claude Code creates a **Plan** — a structured breakdown of the task into steps, with each step assigned to a Sub-Agent. You can review and approve the plan before execution.

**Enabling Agent Teams:** In Claude Code, this is enabled through the settings or with specific prompts. The course demonstrates enabling and using Agent Teams for complex multi-component projects.

---

### 2.11 Git Worktrees — Parallel Development

**What is a Git Worktree?**  
Git Worktrees allow you to check out multiple branches of a Git repository simultaneously in different folders. Normally you can only work on one branch at a time. With worktrees, you can work on many branches at once.

**Why this matters for Claude Code / AI development:**  
When running multiple Claude Code instances (an Agent Team), each agent needs its own working directory so they don't conflict with each other. Git Worktrees provide exactly this — each Sub-Agent gets its own folder and branch to work in.

**Without Worktrees:** Agents would overwrite each other's changes, causing conflicts.  
**With Worktrees:** Each agent works in isolation; the parent merges results at the end.

**Setup:**
```bash
# Create a worktree for a new feature
git worktree add ../my-project-feature feature-branch

# List all worktrees
git worktree list
```

**Industry analogy:** Git Worktrees for AI is like giving each developer on a team their own desk. Everyone works without bumping into each other, and code is merged in at the end.

---

### 2.12 Hooks — Automated Event Triggers

**What are Hooks?**  
Hooks are scripts or instructions that automatically run when specific events occur in Claude Code. They let you automate repetitive checks and actions without manual intervention.

**Examples of hooks:**
- **Pre-task hook:** "Before starting any task, always re-read CLAUDE.md"
- **Post-edit hook:** "After editing any file, run the linter automatically"
- **Pre-commit hook:** "Before committing code, run all tests"
- **Error hook:** "If a command fails, log the error and notify me"

**Where hooks are defined:** In `.claude/settings.json` or dedicated hook files in `.claude/hooks/`.

**Why hooks are powerful:** They enforce quality and consistency. Instead of remembering to run tests every time, you define a hook once and Claude Code always runs them automatically.

---

### 2.13 Slash Commands

**What are Slash Commands?**  
Custom shortcuts you define that trigger specific behaviors in Claude Code. You type `/command-name` and Claude executes the pre-defined action associated with it.

**Examples:**
- `/new-component` → Generates a new React component with boilerplate
- `/write-tests` → Generates unit tests for the current file
- `/deploy` → Runs the full deployment pipeline
- `/summarize-session` → Creates a summary of what was done in this session

**Where they're defined:** In `.claude/commands/` as Markdown files.

**Why slash commands matter:** They turn complex multi-step Claude Code workflows into single commands. Great for teams where everyone needs to follow the same workflow.

---

### 2.14 Verification in AI Development

**The concept:** AI-generated code is not guaranteed to be correct. "Verification" refers to the practice of systematically checking that AI-generated outputs actually work as intended, especially for critical systems like payment processing.

**Why verification is critical:** The course dedicates a section to this because AI coding assistants have a well-known failure mode: they produce code that *looks* correct but has subtle bugs. For things like payment flows, these bugs can cost real money.

**Verification strategies taught:**
1. **Always test payment functionality manually** after AI builds it
2. **Use unit tests** — ask Claude to write tests for every component it builds
3. **Code review** — read the AI-generated code before merging
4. **Staging environments** — test in a non-production environment first
5. **Claude's self-verification** — ask Claude "Are you sure this code is correct? What edge cases might break it?"

**Key insight:** The best use of Claude Code is not "build it and ship it." It's "build it, verify it with AI-assisted tests, review it yourself, then ship it."

---

### 2.15 The Power of Automation — Business Context

**Core philosophy of the course:** Claude Code is not just a coding tool — it's an automation platform for building businesses. The instructor's background is in building automated businesses (he grew a content company to 7 figures using automation).

**The business model (Build & Sell):**
1. Use Claude Code to build software products or automation workflows
2. Sell the resulting products/services to clients or as SaaS
3. Use Claude Code to manage and scale the business operations

**Automation types covered:**
- Email classification and routing (Gmail + MCP)
- Web app development (landing pages, SaaS tools)
- API deployment (Modal)
- Project management (GitHub integration)

---

### 2.16 Deploying APIs with Modal

**What is Modal?**  
Modal is a cloud platform designed for running Python code and AI workloads. It makes it easy to deploy serverless functions, APIs, and ML models to the cloud without managing infrastructure.

**Why Modal + Claude Code:**  
Claude Code can write the Python API code, and Modal deploys it instantly. The combo allows someone with no DevOps experience to build and deploy production APIs.

**Typical workflow:**
1. Claude Code writes a Python API (e.g., a FastAPI endpoint)
2. You deploy it with `modal deploy your_script.py`
3. Modal provisions the infrastructure automatically
4. Your API is live and accessible via a public URL

**Use cases:** AI microservices, data processing pipelines, webhook handlers, ML inference endpoints.

---

## 3. Terminology

| Term | Definition |
|------|-----------|
| **`Agentic AI`** | An AI that takes sequences of actions autonomously to complete a goal, rather than just answering questions |
| **`Claude`** | The AI model created by Anthropic, the underlying intelligence in Claude Code |
| **`Claude Code`** | Anthropic's agentic coding tool that runs Claude in your development environment |
| **`Context Window`** | The maximum amount of text (in tokens) that an LLM can process at once |
| **`Token`** | The basic unit of text processing for LLMs (~0.75 words or ~4 characters per token) |
| **`CLAUDE.md`** | A special Markdown file that acts as persistent instructions/memory for Claude Code in a project |
| **`.claude/`** | Hidden directory in a project that stores Claude Code's project-specific configuration |
| **`MCP (Model Context Protocol)`** | An open standard for connecting AI models to external tools and data sources |
| **`MCP Server`** | A service that exposes a tool (e.g., Gmail, database) through the MCP standard |
| **`Skill`** | A reusable, parameterized task definition stored in `.claude/skills/` |
| **`Sub-Agent`** | An autonomous Claude instance that runs independently on a specific task |
| **`Agent Team`** | A coordinated group of Sub-Agents working on a larger goal under a parent orchestrator |
| **`Git Worktree`** | A way to check out multiple Git branches simultaneously in different directories |
| **`Hook`** | An automated script that runs when specific events occur in Claude Code |
| **`Slash Command`** | A custom shortcut (`/command`) that triggers pre-defined Claude Code behavior |
| **`Antigravity IDE`** | The IDE used in this course, designed for AI-assisted development with Claude Code |
| **`VS Code`** | Visual Studio Code — the most popular open-source code editor by Microsoft |
| **`Terminal / CLI`** | Text-based interface for interacting with a computer via typed commands |
| **`IDE`** | Integrated Development Environment — a software suite combining code editor, terminal, debugger |
| **`Modal`** | Cloud platform for deploying Python code and AI APIs without managing infrastructure |
| **`LLM`** | Large Language Model — the type of AI model Claude is (trained on vast amounts of text) |
| **`Parallelism`** | Doing multiple tasks simultaneously (Sub-Agents enable this for AI workflows) |
| **`Verification`** | The process of testing and confirming that AI-generated code works correctly |
| **`.claudeignore`** | A file that tells Claude Code which files/folders to ignore (like `.gitignore`) |
| **`Proposal`** | A plan Claude Code generates before starting a complex task, which you can approve/modify |
| **`Plan`** | Structured breakdown of a task into steps; created by the parent agent before spawning Sub-Agents |

---

## 4. Tools & Environment Setup

### 4.1 Required Tools

| Tool | Purpose | Cost |
|------|---------|------|
| **Anthropic API Key** | Required to run Claude Code | Pay-per-token (see anthropic.com/pricing) |
| **Antigravity IDE** | Visual IDE for Claude Code | Free (available on antigravity.dev) |
| **VS Code** | Alternative IDE / code editor | Free |
| **Git** | Version control (required for Worktrees) | Free |
| **Node.js / npm** | For web app development | Free |
| **Python** | For Modal deployments | Free |
| **Modal** | Cloud deployment platform | Free tier available |

### 4.2 Setup Steps (Summary)

1. **Get an Anthropic API key** — Sign up at console.anthropic.com
2. **Install Claude Code:**
```bash
   npm install -g @anthropic-ai/claude-code
```
3. **Set your API key:**
```bash
   export ANTHROPIC_API_KEY="your-api-key-here"
```
4. **Install Antigravity IDE** — From antigravity.dev
5. **Initialize a project:**
```bash
   mkdir my-project && cd my-project
   claude   # starts Claude Code in the current directory
```
6. **Create your CLAUDE.md** — Add project context
7. **Start building!**

### 4.3 GitHub for Project Management

The course demonstrates using GitHub (not just for code storage) as a project management tool integrated with Claude Code:
- Claude Code can read GitHub issues and convert them into tasks
- Pull requests can be reviewed and approved through Claude Code
- GitHub Actions can be triggered by Claude Code workflows

---

## 5. Examples & Walkthroughs

### 5.1 Building Your First Web App (< 15 Minutes)

**Goal:** Create a simple landing page with a payment form.

**Steps shown in the course:**
1. Open Antigravity IDE, start a new Claude Code session
2. Type: `"Build a landing page for a SaaS tool called TaskBot. It should have a hero section, features section, and a Stripe payment button."`
3. Claude Code creates the file structure, writes HTML/CSS/JS
4. Verify the output in the browser
5. Iterate: `"Make the hero section full-screen and add a gradient background"`

**Result:** A functional, designed landing page in under 15 minutes — with zero manual coding.

---

### 5.2 Email Classification with MCP + Sub-Agents

**Goal:** Automatically classify incoming Gmail emails into categories and apply labels.

**Workflow:**
1. Connect Gmail via MCP: `claude mcp add gmail`
2. Define a "classify-email" Skill in `.claude/skills/`
3. Parent agent reads the Gmail inbox
4. Spawns one Sub-Agent per email
5. Each Sub-Agent classifies the email (urgent / sales / support / spam)
6. Gmail labels are applied automatically

**Business value:** A task that would take 30 minutes manually now happens in under 60 seconds — and can run on a schedule without human intervention.

---

### 5.3 Using Git Worktrees for Parallel Development

**Goal:** Have three Sub-Agents building different features simultaneously.

```bash
# Create worktrees for three features
git worktree add ../project-auth auth-feature
git worktree add ../project-dashboard dashboard-feature
git worktree add ../project-api api-feature
```

Then spawn three Claude Code Sub-Agents, each pointed at a different worktree. They build in parallel. When done, the parent agent merges all branches.

**Result:** 3x faster development.

---

### 5.4 Deploying an API with Modal

```python
# api.py — written by Claude Code
import modal

app = modal.App("my-classifier-api")

@app.function()
@modal.web_endpoint()
def classify(text: str) -> dict:
    # Classification logic here
    return {"category": "urgent", "confidence": 0.95}
```

```bash
modal deploy api.py
# → Your API is live at https://your-name--my-classifier-api-classify.modal.run
```

---

## 6. Common Doubts & Beginner Questions

**Q: Do I need to know how to code to use Claude Code?**  
A: Not at all for basic tasks. You can build functional web apps using only plain English. However, knowing some coding helps you verify Claude's output and make targeted corrections. The course is designed for complete beginners.

**Q: Is Claude Code the same as GitHub Copilot?**  
A: No. GitHub Copilot suggests code as you type — it's a code autocomplete tool. Claude Code takes full goals and executes them autonomously — writing, running, and debugging code. Claude Code is far more autonomous and capable of completing entire features independently.

**Q: How much does Claude Code cost?**  
A: Claude Code itself is free to install. You pay Anthropic per API token used. For typical projects, costs range from a few dollars for simple tasks to $10–$50 for complex sessions. Efficient context management (CLAUDE.md, `.claudeignore`, scoped tasks) minimizes costs significantly.

**Q: What happens when Claude runs out of context?**  
A: Claude will stop remembering earlier parts of the conversation. This can cause it to make mistakes or repeat work. The solution is to keep CLAUDE.md updated with critical information, use `.claudeignore` to exclude unnecessary files, and start fresh sessions for new tasks.

**Q: Can Claude Code delete my files or break my project?**  
A: Yes, it technically can — Claude Code has file system access. Best practices to protect yourself: use Git (so everything is reversible with `git revert`), review Claude's "proposal" before approving large operations, and test in a separate branch first.

**Q: What is the difference between a Skill and a Sub-Agent?**  
A: A Skill is a reusable task template — instructions for *how* to do something. A Sub-Agent is an autonomous AI instance that *executes* a task. You can think of a Skill as the job description and a Sub-Agent as the employee. A Sub-Agent can use a Skill as its instructions.

**Q: Do I need to use Antigravity IDE or can I use VS Code?**  
A: Both work. VS Code with a terminal works fine for Claude Code. Antigravity IDE provides extra visual integrations with Claude Code. The course uses Antigravity, but the concepts apply to any IDE.

**Q: What is the CLAUDE.md file for — isn't Claude smart enough to figure things out?**  
A: Claude is smart, but it has no memory between sessions. Without CLAUDE.md, it starts every session knowing nothing about your project. CLAUDE.md is the solution to this memory problem — it's a briefing document that Claude reads at the start of every session.

**Q: Can I run multiple Claude Code instances at once?**  
A: Yes — this is the entire premise of Sub-Agents and Agent Teams. The course teaches you to orchestrate multiple parallel Claude instances using Git Worktrees to prevent conflicts.

**Q: What is MCP and why should I care?**  
A: MCP (Model Context Protocol) is the system that lets Claude connect to real-world tools — Gmail, databases, web browsers, Slack, etc. Without MCP, Claude is limited to your local files. With MCP, Claude can interact with the entire digital world. It dramatically expands what automation is possible.

---

## 7. Interview Questions

### Junior Level

**Q: What is Claude Code and how does it differ from a regular chatbot?**  
**A:** Claude Code is an agentic AI coding tool that runs autonomously in your development environment. Unlike a chatbot that answers questions, Claude Code takes goals as input, writes code, executes commands, reads results, and iterates until the task is done — all without constant human input. A chatbot is conversational; Claude Code is autonomous and action-oriented.

**Q: What is the CLAUDE.md file and why is it important?**  
**A:** `CLAUDE.md` is a special file placed at a project's root that Claude Code reads at the start of every session. It acts as persistent memory and project context for the AI, since LLMs have no memory between sessions. It contains the tech stack, coding standards, commands, and business rules. Without it, Claude starts each session knowing nothing about the project.

**Q: What is a token and why does it matter for AI tools like Claude Code?**  
**A:** A token is the basic unit of text that an LLM processes (roughly 0.75 words). LLMs have a context window limit — a maximum number of tokens they can process at once. For Claude Code, exceeding this limit means the AI may lose track of earlier context, make mistakes, or fail tasks. Token count also determines API cost, so managing tokens efficiently reduces expense.

**Q: What is the difference between a terminal and an IDE?**  
**A:** A terminal (CLI) is a text-only interface for entering commands. An IDE (Integrated Development Environment) is a visual tool combining a code editor, file explorer, terminal, and debugger. Claude Code runs natively in the terminal, but IDEs like VS Code or Antigravity provide a visual overlay that makes managing Claude Code sessions easier.

---

### Mid Level

**Q: Explain what Model Context Protocol (MCP) is and give an example of how it would be used.**  
**A:** MCP (Model Context Protocol) is an open standard by Anthropic for connecting AI models to external tools and data sources. It standardizes the communication between an AI and any external service (like Gmail, a database, or a web browser) via MCP Servers. For example, to connect Claude to Gmail, you'd add a Gmail MCP server. Claude can then read, classify, and label emails without writing any integration code. MCP is to AI what USB is to hardware — a universal connector.

**Q: What is the purpose of Git Worktrees in the context of multi-agent AI development?**  
**A:** Git Worktrees allow multiple branches of a Git repository to be checked out simultaneously in different directories. In multi-agent AI development, when an Agent Team spawns multiple Sub-Agents to work in parallel, each agent needs its own isolated working directory to avoid overwriting each other's changes. Git Worktrees provide this isolation — each Sub-Agent works in its own directory/branch. The parent agent merges results when all Sub-Agents complete their tasks.

**Q: How do Skills and Sub-Agents work together in Claude Code?**  
**A:** A Skill is a reusable, parameterized task definition (like a function). It defines the steps Claude should follow for a specific repeated task. A Sub-Agent is an autonomous Claude instance. A Skill can be given to a Sub-Agent as its operational instructions — the Sub-Agent executes the Skill autonomously in the background. For example, a "classify-email" Skill, when promoted to a Sub-Agent, becomes an autonomous email classifier that runs independently on each email in parallel.

---

### Senior Level

**Q: Describe the architecture of an Agent Team in Claude Code. What are the tradeoffs?**  
**A:** An Agent Team consists of a Parent Orchestrator Agent that decomposes a high-level goal into sub-tasks, assigns them to specialized Sub-Agents, monitors their progress, and integrates their results. Each Sub-Agent works in an isolated Git Worktree. The tradeoffs include: (1) **Parallelism benefits** — dramatically faster execution; (2) **Coordination overhead** — more complex orchestration logic, risk of merge conflicts; (3) **Token cost** — multiple parallel agents consume API tokens simultaneously, increasing cost; (4) **Error propagation** — if a Sub-Agent makes an incorrect assumption early, it may affect downstream agents. Best suited for large, decomposable tasks with clear boundaries between sub-tasks.

**Q: What strategies would you use to optimize token usage in a large-scale Claude Code deployment?**  
**A:** (1) **CLAUDE.md optimization** — keep it dense and precise, not verbose; (2) **`.claudeignore`** — exclude irrelevant files (node_modules, build artifacts, large datasets); (3) **Task scoping** — give Claude small, targeted tasks instead of broad goals; (4) **Session management** — start fresh sessions for unrelated tasks to avoid context pollution; (5) **Skill extraction** — encode common operations as Skills to avoid re-explaining them; (6) **Summarization checkpoints** — periodically summarize the session's work into CLAUDE.md to compress context; (7) **MCP tool selection** — use focused MCP tools that return minimal, relevant data.

---

## 8. Industry Usage

### How Companies Are Using Claude Code (as of 2026)

**Freelancers and Solo Builders:**  
Building and selling SaaS tools, landing pages, and automation workflows for clients with no team. Claude Code enables "1-person companies" that generate revenue previously requiring 5–10 engineers.

**Startups:**  
Using Agent Teams to run parallel development — frontend, backend, tests, and docs all built simultaneously. Claude Code compresses weeks of development into days.

**Automation Agencies:**  
Building client workflow automation (email management, data pipelines, report generation) using MCP-connected Claude Code. The business model: build once, sell to many similar clients.

**Content Companies:**  
Automating content operations — AI writes, formats, and publishes — freeing human team members for strategy and creativity. (Nick Saraev's own 1SecondCopy company is an example.)

**DevOps and API Development:**  
Combining Claude Code with Modal to build and deploy ML inference APIs and data processing services rapidly, reducing infrastructure work from days to hours.

### Real-World Use Case from the Course

A handyman asked a student to build a website for his small business. The student, following this course, built a fully functional business website using Claude Code in a single day — with no prior web development experience. Claude Code wrote the HTML, CSS, and JavaScript; the student guided and verified it. The result: a client-ready website built and delivered in 1 day instead of the typical 2–4 weeks.

---

## 9. Related Topics

The following topics should be studied next, building on what you've learned here:

| Topic | Why It's Related | Priority |
|-------|-----------------|---------|
| **Anthropic API & Pricing** | Understanding API costs for Claude Code budgeting | High |
| **Prompt Engineering** | Writing better instructions for Claude gives better code output | High |
| **Git & GitHub** | Worktrees and project management require Git proficiency | High |
| **Python Basics** | Required for Modal deployments and MCP server customization | Medium |
| **REST APIs** | Understanding API design helps you build and verify Claude Code outputs | Medium |
| **Model Context Protocol (Advanced)** | Building custom MCP servers to connect Claude to any tool | Medium |
| **AI Agents (General Theory)** | Understanding the broader concept of agentic AI systems | Medium |
| **Agentic Workflows (n8n, Make.com)** | Nick's other courses on visual workflow automation that complement Claude Code | Medium |
| **LLM Fundamentals** | Understanding how large language models work helps debug Claude's behavior | Low |
| **Vibe Coding** | Related approach taught in Nick's Gemini course — visual, intuitive AI coding | Low |
| **Docker & DevOps** | For more complex deployments beyond Modal | Low |

**Cross-references within this course document:**
- **Context Window → Tokens:** Understanding tokens (Section 3) explains why context management (Section 2.6) matters
- **MCP → Sub-Agents:** MCP tools can be called by Sub-Agents (Section 2.9), making them far more powerful
- **Skills → Sub-Agents → Agent Teams:** These three concepts form a hierarchy (Sections 2.8–2.10)
- **Git Worktrees → Agent Teams:** Worktrees (Section 2.11) are a prerequisite for running Agent Teams (Section 2.10)
- **CLAUDE.md → Context Management:** CLAUDE.md (Section 2.4) is the primary tool for context management (Section 2.6)

---

## 10. Revision Notes

**Core Ideas to Memorize:**

- Claude Code = AI developer that lives in your terminal, autonomous, runs in a loop
- `CLAUDE.md` = project brain / persistent memory — always keep it up to date
- `.claude/` directory = project config hub (commands, hooks, skills)
- Token = ~0.75 words; context window = token limit; exceeding it = AI forgets
- MCP = universal plugin standard for connecting AI to tools (Gmail, databases, etc.)
- Skill = reusable task template (like a function); stored in `.claude/skills/`
- Sub-Agent = autonomous Claude instance executing one task independently
- Agent Team = multiple Sub-Agents coordinated by a parent agent = parallelism
- Git Worktrees = lets multiple Sub-Agents work on different branches simultaneously
- Hooks = auto-triggered scripts on events (pre-task, post-edit, on-error)
- Slash Commands = custom shortcuts for repeated Claude Code actions
- Modal = easy cloud deployment for Python APIs written by Claude Code
- Verification = ALWAYS test AI-generated code, especially payment flows

**The "Build & Sell" Workflow:**
1. Define the product → write CLAUDE.md → build with Claude Code → verify → deploy via Modal → sell

**Key Mental Models:**
- Claude Code is a developer, not a chatbot — give it goals, not questions
- CLAUDE.md is the employee handbook for your AI team
- Sub-Agents are parallel workers; Agent Teams are your engineering department
- MCP is the USB port of AI — standardized connection to everything
- Skills are functions; Sub-Agents are the execution engine

---

*Document created: 2026-06-01 | Source: YouTube — Nick Saraev | Last updated: 2026-06-01 | Version: 1.0*

*To update this document with a new video, add content under existing sections if the topic overlaps, or create a new top-level Module file (e.g., `module-2-agentic-workflows.md`) if the topic is distinct.*

