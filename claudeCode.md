# Claude Code — Complete Developer Course

> **Source:** [Complete Claude Code Course In 2 Hours For Developers](https://www.youtube.com/watch?v=TAKDIvvUdc4)  
> **Instructor:** Krish Naik (1.43M subscribers)  
> **Duration:** 1 hour 58 minutes | **Published:** May 25, 2026  
> **Document Version:** 1.0 | **Last Updated:** June 2026  
> **Prerequisites:** Basic Python knowledge  

---

## Table of Contents

1. [Overview](#1-overview)
2. [Key Concepts](#2-key-concepts)
3. [Terminology](#3-terminology)
4. [Claude Ecosystem](#4-claude-ecosystem)
5. [Claude Code Installation & Integration](#5-claude-code-installation--integration)
6. [The Agentic Loop](#6-the-agentic-loop)
7. [Building with Claude Code](#7-building-with-claude-code)
8. [CLAUDE.md — Memory & Context Files](#8-claudemd--memory--context-files)
9. [Agents and Sub-Agents](#9-agents-and-sub-agents)
10. [Agent Views](#10-agent-views)
11. [Agent Teams](#11-agent-teams)
12. [Claude Skills](#12-claude-skills)
13. [Claude Plugins](#13-claude-plugins)
14. [Common Doubts](#14-common-doubts)
15. [Interview Questions & Answers](#15-interview-questions--answers)
16. [Industry Usage](#16-industry-usage)
17. [Related Topics](#17-related-topics)
18. [Revision Notes](#18-revision-notes)

---

## 1. Overview

Claude Code is an **agentic AI coding tool** built by Anthropic that reads your entire codebase, edits files, runs commands, and integrates with your development tools. It is available in your **terminal, IDE, desktop app, and browser**.

Unlike simple code-completion tools (like basic Copilot autocomplete), Claude Code operates in an **agentic loop** — it plans, acts, observes the result, and iterates until the task is complete. It understands your entire project context and can manage files, fix bugs, build features, and even spawn autonomous sub-agents to work in parallel.

This course targets developers who want to use Claude Code productively in real projects, aligned with the **Claude Certified Architect** certification curriculum.

**What you will learn:**
- Setting up Claude Code in your development environment
- Using Claude Code to understand and work inside existing codebases
- Building autonomous agents and sub-agents
- Running agent teams that communicate with each other
- Creating reusable skills and installing third-party plugins
- Using Plan Mode, Auto Mode, and Accept-Edit mode effectively

---

## 2. Key Concepts

### 2.1 Agentic Coding Tool

A traditional AI assistant waits for a single prompt and returns a single answer. Claude Code is **agentic** — it breaks down a complex task into smaller sub-tasks, takes actions (read files, write code, run terminal commands), observes the outcome, and continues iterating until the goal is accomplished.

**Analogy:** Think of a regular AI as a calculator — you give it an input, it gives you an output. Claude Code is more like a junior developer who sits next to you: you give it a task, it opens your codebase, starts working, runs the app to test it, fixes the error, and comes back to you when done.

### 2.2 The Agentic Loop

The agentic loop is the core engine that powers Claude Code. It consists of three repeating stages:

```
[Read / Understand Context] → [Plan & Execute Action] → [Observe Result & Iterate]
```

- **Stage 1 — Context Gathering:** Claude reads files, folder structures, configs, and relevant documentation.
- **Stage 2 — Action Execution:** Claude writes code, modifies files, runs terminal commands, calls APIs, etc.
- **Stage 3 — Observation & Iteration:** Claude checks the result (e.g., runs the code, reads error messages) and loops back to Stage 1 if the task is not complete.

The loop continues **unless and until the task is resolved**. For example, if there is a bug, Claude will keep retrying until the bug is fixed.

### 2.3 Plan Mode vs Auto Mode vs Accept-Edit Mode

These are the three operating modes you can switch between using `Shift+Tab` inside Claude Code:

| Mode | Description | Best Used For |
|------|-------------|---------------|
| **Plan Mode** | Claude first creates a detailed plan/blueprint of what it will do, then waits for your approval before executing | Complex tasks; risky changes; large refactors |
| **Auto Mode** | Claude executes tasks automatically without stopping for confirmation at each step | Trusted tasks; rapid prototyping |
| **Accept-Edit Mode** | Claude asks for your explicit confirmation before applying each file edit | Code reviews; cautious production work |

**Plan Mode internally spawns a separate sub-agent** that creates the plan as an independent Claude instance running in the background — it is not just a text description, but an actual agentic process.

### 2.4 Context Window

The **context window** is the maximum amount of text (code, instructions, conversation) that Claude can hold in "working memory" at one time.

- **Claude Opus 4.7** — 1 million token context window (default in Claude Code)
- **Claude Sonnet 4.6** — Smaller but faster; switchable within settings

A large context window means Claude can understand your entire large codebase at once, rather than just a few files.

### 2.5 Memory Scopes

Claude Code has three memory levels that determine where instructions and agent configurations are stored:

| Scope | Location | Visible To |
|-------|----------|------------|
| **Project Scope** | Inside the project folder | Everyone working on that project |
| **User Scope** | Tied to the current OS user account | Only the current user, across all projects |
| **Local Scope** | The local desktop/machine | The specific machine being used |

### 2.6 CLAUDE.md (Cloud.mmd) File

The `CLAUDE.md` file (shown as `cloud.mmd` in the course) is a **special Markdown file placed at the root of your project**. Claude Code automatically loads this file into its context at the start of every conversation in that project.

You use it to give Claude persistent instructions about your project — its architecture, coding conventions, what libraries to use, what not to touch, etc. Use `/init` to auto-generate it from an existing codebase.

---

## 3. Terminology

| Term | Definition |
|------|------------|
| **`> claude`** | Terminal command to launch Claude Code in the current directory |
| **Agentic Loop** | The iterative cycle of: gather context → take action → observe result → repeat |
| **Plan Mode** | An operating mode where Claude creates an execution plan before acting |
| **Auto Mode** | Claude acts fully autonomously without requesting confirmation |
| **Accept-Edit Mode** | Claude asks for permission before each file modification |
| **Sub-Agent** | A separate Claude instance spawned to handle a specific sub-task independently |
| **Agent View** | A live terminal panel showing the real-time status of all running agents |
| **Agent Team** | A collaborative group of Claude agents that share a task list and communicate with each other |
| **Skill** | A reusable collection of instructions, resources, and examples that teaches Claude how to perform a specific type of task |
| **Plugin** | A third-party package integration that provides additional tools, resources, or capabilities to Claude Code via a standard interface |
| **CLAUDE.md** | A Markdown file loaded into every project conversation as persistent context |
| **`/init`** | Slash command that auto-generates a `CLAUDE.md` for your current project |
| **`/plugins`** | Slash command to browse the installed and available plugins marketplace |
| **MCP Server** | Model Context Protocol server — a standardized way to connect external tools and data sources to Claude |
| **Context Window** | Maximum amount of text Claude can process at one time (1M tokens for Opus 4.7) |
| **Plan.mmd File** | A Mermaid diagram file auto-generated by Claude to document the architecture or execution plan |
| **Claude Opus 4.7** | The most capable Claude model with a 1M token context window (default for Claude Code) |
| **Claude Sonnet 4.6** | A faster, lighter Claude model switchable from settings |
| **Exa Search** | A third-party web search plugin that can be integrated into Claude Code |
| **Context7** | A plugin that provides up-to-date open-source library documentation to Claude |

---

## 4. Claude Ecosystem

### 4.1 The Three Main Products

Anthropic's product ecosystem around Claude consists of three primary tools relevant to developers:

**Claude.ai (Web App)**
- The conversational web interface (chat.claude.ai)
- Great for analysis, writing, explaining concepts, and Excel-like tasks
- Has Projects, Live Artifacts, and Contexts
- "Personal assistant for doing multiple tasks" — good for running a company, writing, research

**Claude Desktop App**
- Downloadable desktop application
- Allows you to select a local folder and give instructions
- Coding happens inside the app interface
- Less recommended for developers — the terminal/IDE approach gives more visibility

**Claude Code (Terminal / IDE Tool)**
- The main focus of this course
- CLI tool: just type `claude` in any terminal to start
- Available in: terminal, IDE (VS Code extension), desktop app, browser
- For developers: terminal + IDE is the recommended approach because you see all the actions being taken

### 4.2 Integrations Available in the Ecosystem

Claude can be integrated across different surfaces:
- **Chrome browser** — as a browser extension
- **Slack** — as a workspace app/extension
- **GitHub** — via plugin for PR reviews, issue management
- **VS Code / Cursor** — IDE extension
- **Custom scripts** — via the Claude API

### 4.3 Models Available in Claude Code

| Model | Context Window | Best For |
|-------|---------------|---------|
| Claude Opus 4.7 | 1,000,000 tokens | Deep codebase understanding, complex tasks (default) |
| Claude Sonnet 4.6 | Smaller | Faster responses, lighter tasks |

You can switch models from Claude Code's settings at any time.

---

## 5. Claude Code Installation & Integration

### 5.1 Platform Support

| Platform | Installation Method |
|----------|---------------------|
| macOS / Linux / WSL | `npm install -g @anthropic-ai/claude-code` |
| Windows PowerShell | PowerShell install command from docs |
| Windows CMD | `curl`-based install command from docs |

Always check the [official docs](https://docs.anthropic.com/claude-code) for the latest install command for your OS.

### 5.2 Pricing

Claude Code is available under the following plans:
- **Pro Plan** — ~$20/month — gives access to Claude Code
- **Pro Max Plans** — higher usage limits and access to more powerful models

### 5.3 Starting Claude Code

```bash
# Navigate to your project folder
cd my-project

# Start Claude Code
claude
```

When you first run `claude` in a folder, it will ask: **"Do you trust this folder?"** — type `yes` to allow it to read and write files in that directory.

### 5.4 Integrating with VS Code (IDE)

1. Install the Claude Code VS Code extension from the marketplace
2. Open a project in VS Code
3. Claude Code appears as a panel in the sidebar
4. The same agentic loop works directly from within the IDE

### 5.5 Understanding a New Codebase (Real-World Scenario)

One of the most powerful use cases: **joining a new company or project**. Instead of spending days reading documentation:

```
> claude "analyze this project and tell me about its architecture, 
  the main modules, and how they connect"
```

Claude will scan every folder and file, create an internal agentic loop, and give you a structured summary. You can then ask follow-up questions like "what does the authentication module do?" or "how does the data flow from the API to the database?"

---

## 6. The Agentic Loop

### 6.1 How It Works Step by Step

```
User gives a task
       ↓
Claude reads the project context (files, folders, configs)
       ↓
Claude creates an internal plan
       ↓
Claude executes the first action (writes code / runs command)
       ↓
Claude reads the output / error
       ↓
If task NOT complete → loop back to plan step
If task COMPLETE → return result to user
```

### 6.2 What Triggers Each Stage

- **Context-gathering only:** Simple questions about the codebase (e.g., "what does this file do?")
- **Full loop:** Bug fixes, feature implementations, refactoring
- **Repeated loop:** Complex bugs where Claude keeps trying different approaches until the bug is resolved

### 6.3 Adapting to Task Type

The agentic loop **adapts dynamically** to the complexity of what you ask:
- A simple question might only need Stage 1 (context gathering)
- A bug fix cycles through all three stages repeatedly
- A new feature build might run dozens of iterations

### 6.4 Running in a Sandbox

Claude Code can execute scripts in a sandboxed environment to test its own code changes — if an error occurs, it automatically feeds that error back into the loop and continues fixing.

---

## 7. Building with Claude Code

### 7.1 Slash Commands (Built-in Commands)

Slash commands are special instructions that trigger built-in behaviors:

| Command | What It Does |
|---------|-------------|
| `/init` | Scans the current project and auto-generates a `CLAUDE.md` file with project context |
| `/plugins` | Opens the plugin marketplace to browse, install, or manage plugins |
| `Shift+Tab` | Cycles between Plan Mode, Auto Mode, and Accept-Edit Mode |

### 7.2 Creating a Plan File (plan.mmd)

When building something complex, instruct Claude to first write a plan:

```
> "Before you start coding, write down your entire execution plan 
  as a Mermaid diagram in a file called plan.mmd"
```

This creates a visual architecture diagram that:
- Serves as documentation for the team
- Gives Claude a reference to follow as it builds
- Can be committed to the repository as living documentation

### 7.3 Real Example — Building from Scratch vs. Joining Existing

**Joining an existing project (most common in industry):**
```
> "I just joined this team. Analyze the entire codebase and give 
  me a summary of: 1) the main components, 2) the tech stack, 
  3) how data flows from the API to the database"
```

**Implementing a new feature:**
```
> "Add a user authentication module using JWT tokens. 
  Follow the existing patterns in the codebase."
```

**Fixing a bug:**
```
> "The login function throws a 500 error when the email contains 
  a '+' character. Find and fix it."
```

Claude will then loop through reading the relevant files, writing the fix, testing it, and reporting back.

### 7.4 Projects Feature (Context Management)

In Claude Code / Claude.ai, you can create **Projects** that preserve context across conversations. This is useful for:
- Ongoing software development where context must persist
- Team projects where everyone needs the same Claude context
- Long-term codebases where you don't want to re-explain architecture every session

---

## 8. CLAUDE.md — Memory & Context Files

### 8.1 What Is CLAUDE.md?

`CLAUDE.md` is a special Markdown file placed in the **root of your project folder**. Every time you start a new Claude Code conversation in that folder, Claude automatically loads this file first.

Think of it as **persistent memory for Claude about your project** — you write it once and Claude "remembers" your project conventions every time.

### 8.2 What to Put in CLAUDE.md

```markdown
# Project: MyApp

## Architecture
- Frontend: React + TypeScript
- Backend: FastAPI (Python)
- Database: PostgreSQL with SQLAlchemy ORM
- Auth: JWT tokens via python-jose

## Coding Conventions
- Use snake_case for Python variables and functions
- Use camelCase for JavaScript/TypeScript
- Always add docstrings to Python functions
- Never commit .env files

## Do NOT modify
- /legacy folder (old client code, keep intact)
- database/migrations (always generate new migrations, never edit old ones)

## Key Files
- main.py — FastAPI app entry point
- config.py — All environment-based configuration
```

### 8.3 How to Generate CLAUDE.md Automatically

```bash
# Inside Claude Code, type:
/init
```

Claude scans your entire project and creates an appropriate `CLAUDE.md` for you. You can then edit it to add additional constraints or remove irrelevant sections.

### 8.4 Memory Scope Locations

```
/project-root/CLAUDE.md        → Project scope (everyone on the project sees this)
~/.claude/CLAUDE.md            → User scope (applies to all projects for this OS user)
/local-machine/CLAUDE.md       → Local scope (applies only on this machine)
```

---

## 9. Agents and Sub-Agents

### 9.1 What Is a Sub-Agent?

A **sub-agent** is a separate, independent Claude Code instance that is spawned by the main Claude session to handle a specific task. Each sub-agent:
- Has its **own isolated context window**
- Executes its task independently from the parent
- Returns a **single summary result** back to the caller when done
- Operates in parallel with other sub-agents

**Key difference from Agent Teams:** Sub-agents do NOT communicate with each other. They are like workers in separate rooms who hand their finished work back to a coordinator.

### 9.2 Built-In Sub-Agents (Examples)

When you press `Shift+Tab` in Claude Code, you can see built-in sub-agent modes:

| Agent | Role |
|-------|------|
| **Edit Mode** | Focuses on applying file edits |
| **Plan Mode** | Runs as a planner sub-agent to create a structured execution plan |

### 9.3 Creating a Custom Agent

In Claude Code, you can create named custom agents. During agent creation, you configure:

1. **Agent Name** — e.g., `code-improvement-advisor`
2. **Description** — What this agent does
3. **Tools Available** — Which tools the agent can use (file read/write, terminal, web search, etc.)
4. **Model** — Which Claude model to use (Opus 4.7, Sonnet 4.6, or inherit from parent)
5. **Background Color** — Visual identifier in the Agent View
6. **Memory Scope** — Where the agent's configuration is stored (Project / User / Local)

**Example agent created in the course:** `code-improvement-advisor` — scans a codebase and suggests code quality improvements.

### 9.4 Running Agents

```bash
# Start a specific named agent
claude --agent code-improvement-advisor

# Or reference the agent in a task:
> "Run the code-improvement-advisor agent on the /api folder"
```

Agents run in the background. You can manage and observe them through **Agent Views**.

### 9.5 Sub-Agents vs Agent Teams — Key Comparison

| Feature | Sub-Agents | Agent Teams |
|---------|-----------|-------------|
| Communication | None (isolated) | Peer-to-peer communication |
| Context | Own isolated context window | Shared context + task list |
| Coordination | Return results to caller only | Can claim tasks, collaborate, coordinate |
| Use Case | Independent parallel tasks | Complex collaborative workflows |
| Task Visibility | Private | Shared visible task list |

---

## 10. Agent Views

### 10.1 What Is Agent View?

Agent View is a **live monitoring panel in Claude Code** that shows all currently running agents in real time. You can see:
- Which agents are active
- What task each agent is currently working on
- Status of each agent (running / completed / error)
- Logs of what each agent has done

### 10.2 Why It Matters

Without Agent View, running multiple background agents is like having employees working in separate rooms with no visibility. Agent View is your **real-time dashboard** for multi-agent workflows.

### 10.3 Practical Use Case

You have three agents running in parallel:
1. Agent A — analyzing the authentication module
2. Agent B — reviewing the database schema
3. Agent C — checking the API endpoints for security issues

Agent View shows all three simultaneously in your terminal so you can monitor progress without switching between multiple terminal windows.

### 10.4 How It Works Technically

- All agents run as **independent Claude Code processes**
- They appear as separate entries in the Agent View panel
- You can run multiple agents **from a single terminal instance** using Agent View
- Each agent has its own context window and memory

---

## 11. Agent Teams

### 11.1 What Is an Agent Team?

An **Agent Team** is a group of Claude agents that:
- Share a **centralized, visible task list**
- **Communicate with each other** peer-to-peer
- Claim tasks from the shared list when available
- Send their findings back to teammates and the team lead
- Coordinate to solve a complex problem collaboratively

### 11.2 Architecture of an Agent Team

```
[Main Agent / Team Lead]
         |
    [Shared Task List]
    - Task 1
    - Task 2  
    - Task 3
         |
   ┌─────┴─────┐
[Agent A]   [Agent B]
   Claims     Claims
   Task 1     Task 2
      \         /
       Communicate
       findings
          ↓
   [Team Lead consolidates]
          ↓
   [Final result to user]
```

### 11.3 Step-by-Step Flow

1. You give Claude a complex task (e.g., "review this entire codebase for RAG implementation quality")
2. The main agent breaks it into sub-tasks and creates a **shared task list**
3. Claude **spawns N teammate agents** (number depends on the task)
4. Each teammate **claims a task** from the shared list
5. Teammates **work in parallel** and communicate findings to each other
6. Once all tasks are complete, the team lead **consolidates the results**
7. When done, the team gracefully shuts down (teammates confirm shutdown and terminate)

### 11.4 Collaborative Team Structure Benefits

- **Shared context and visibility** — all agents see the same task list
- **Peer-to-peer communication** — agents can share findings and build on each other's work
- **Better coordination** — agents don't duplicate effort
- **Higher quality output** — combined output often exceeds what a single agent could produce

### 11.5 Real Example from the Course

```
Task: "Review the codebase for RAG implementation and page indexing"
Team created:
  - Teammate 1: Reviews page indexing flow
  - Teammate 2: Reviews RAG implementation quality

Both teammates work in parallel, communicate findings, mark tasks complete, 
send consolidated findings to the team lead.
Result: "3 small clarity fixes. Correct page index flow. No duplicated code."
Team gracefully shuts down after both teammates confirm completion.
```

---

## 12. Claude Skills

### 12.1 What Is a Skill?

A **Skill** is a reusable collection of instructions, resources, and examples that **teaches Claude Code how to complete a specific type of task**. Once saved, you can invoke the skill by name without re-explaining everything each time.

**Analogy:** Think of a skill as a **macro or template** for Claude. If you always need Claude to generate API documentation in a specific format, you create a skill for it once and reuse it across projects.

### 12.2 When to Use Skills

Skills are useful when:
- You perform the same type of task repeatedly (e.g., "explain this PR", "add docstrings to this module", "generate a changelog")
- You want to standardize how Claude does something across your team
- You want Claude to remember a complex workflow without re-prompting every time

### 12.3 Creating a Skill

When you create a skill, Claude:
1. Creates a `skill.md` file in a dedicated skills folder
2. Populates it with the instructions, resources, and examples you provided
3. Registers it so you can invoke it by name

**Example: Open-Source Documentation Skill**
```
Skill name: open-source-documentation
Description: Uses Context7 plugin to fetch and summarize 
             the latest docs for any open-source library

Usage: "open-source documentation for [library name]"
```

### 12.4 Invoking a Skill

```bash
# In Claude Code, type:
> "open-source documentation for FastAPI"

# Claude automatically runs the skill steps using Context7 plugin
# to fetch the latest FastAPI docs and return a structured summary
```

### 12.5 Saving Skills at Different Scopes

| Scope | Where Saved | When to Use |
|-------|-------------|-------------|
| Project | `/project-root/.claude/skills/` | Skills specific to one project |
| User | `~/.claude/skills/` | Personal skills used across all projects |
| Local | Local machine config | Machine-specific skills |

---

## 13. Claude Plugins

### 13.1 What Is a Plugin?

A **plugin** is a package integration that provides additional **tools, resources, or capabilities** to Claude Code through a standard interface. Plugins connect Claude to third-party services and data sources.

**Analogy:** If Claude Code is a smartphone, plugins are like apps you install from an App Store.

### 13.2 Why Use Plugins?

Claude Code on its own has strong code reasoning, but many tasks require external data:
- Web search (Claude doesn't have live internet access by default)
- Up-to-date library documentation
- GitHub PR access
- Database connections
- Cloud services

Plugins fill these gaps.

### 13.3 Plugin Marketplace

Access the plugin marketplace inside Claude Code:
```bash
/plugins
# → discover, install, manage plugins
```

### 13.4 Key Plugins Covered in the Course

**Exa Search**
- Provides **real-time web search** capabilities to Claude Code
- Use case: "Find the latest breaking changes in Next.js 15"
- Installation: `claude install exa` (paste the install command from the plugin page)
- Requires: An Exa API secret key (set in plugin configuration)

**Context7**
- Provides **live, up-to-date open-source library documentation**
- Solves the problem: Claude's training data has a cutoff date — library docs change fast
- Use case: "What is the correct API for `useEffect` in React 19?"
- How it works: Fetches docs directly from the official source at query time

### 13.5 Installing a Plugin

```bash
# Method 1: via /plugins marketplace in Claude Code
/plugins → discover → install

# Method 2: via terminal command
claude install <plugin-name>

# After installation, configure API keys if required
# Then verify: /plugins → see installed list
```

### 13.6 MCP Server Integration

Plugins communicate with Claude via the **Model Context Protocol (MCP)**. MCP is Anthropic's standardized interface for connecting external tools and data sources to Claude models.

- Each plugin essentially wraps an external service as an MCP server
- Claude Code can query any MCP-compatible server
- You can see available MCP servers in the integrations section of Claude Code settings

---

## 14. Common Doubts

**Q: What is the difference between Claude.ai and Claude Code?**  
A: Claude.ai is the web chat interface — you type questions and get text answers. Claude Code is a developer tool that runs in your terminal and IDE. Claude Code can actually *read your files*, *run terminal commands*, *edit code*, and *spawn sub-agents* — it takes real actions in your project, not just chat.

**Q: Do I need to be an expert to use Claude Code?**  
A: No. The course requires only basic Python knowledge. Claude Code is designed to help developers at all levels — you give it natural language instructions and it handles the technical details.

**Q: Why use Plan Mode instead of just Auto Mode?**  
A: Auto Mode is fast but risky for critical tasks. Plan Mode makes Claude show you *exactly what it's going to do* before doing it. Always use Plan Mode when: working on production code, doing large refactors, or when mistakes would be expensive to undo.

**Q: What's the difference between a sub-agent and an agent team?**  
A: Sub-agents are isolated — they work alone and only report back to the parent. They have no visibility into each other. Agent Teams share a task list and communicate with each other peer-to-peer, like real team members collaborating. Agent Teams produce better results for complex tasks because agents can build on each other's findings.

**Q: What is a skill vs a plugin?**  
A: A **skill** is something you teach Claude *how to do* — a reusable set of instructions for a task (like a macro). A **plugin** is a connection to an *external service* that gives Claude new *capabilities* (like web search or live docs). Skills are Claude-internal; plugins are external integrations.

**Q: What is CLAUDE.md and why is it important?**  
A: `CLAUDE.md` is Claude's persistent memory for your project. Without it, Claude has no memory between conversations — you'd have to re-explain your project architecture every time. With `CLAUDE.md`, all project context is automatically loaded at the start of every session, making Claude immediately productive.

**Q: What is the agentic loop and why does it matter?**  
A: The agentic loop is what separates Claude Code from simple chatbots. It means Claude doesn't just answer once — it plans, acts, observes the result, and keeps iterating until the task is done. This is how Claude can fix multi-file bugs and build complete features autonomously.

**Q: Does Claude Code need internet access to work?**  
A: Claude Code itself works offline for local code tasks. However, certain features — like the Exa Search plugin (web search) or Context7 (live docs) — require internet access. The AI model itself runs on Anthropic's cloud, so you need an internet connection to use Claude Code at all.

**Q: Can I use Claude Code for free?**  
A: The base Claude Pro plan (~$20/month) gives access to Claude Code. Higher usage limits require Max plans. There is no fully free tier for Claude Code at the time of the course.

**Q: What does "context window" mean in practice?**  
A: The context window is how much your project Claude can "see" at once. With Opus 4.7's 1 million token window, Claude can hold roughly 750,000 words in context — meaning it can analyze even very large codebases in a single session without losing earlier context.

---

## 15. Interview Questions & Answers

**Q1: What is Claude Code and how is it different from other AI coding tools?**  
A: Claude Code is an agentic coding assistant by Anthropic that operates via a continuous loop — it reads files, writes code, runs commands, and iterates until a task is complete. Unlike copilot-style autocomplete tools that suggest the next line of code, Claude Code understands the entire project context and takes multi-step autonomous actions.

**Q2: Explain the agentic loop in Claude Code.**  
A: The agentic loop has three stages: (1) Context Gathering — Claude reads relevant files, folders, and configurations; (2) Action Execution — Claude writes code, modifies files, or runs commands; (3) Observation & Iteration — Claude checks the output and loops back until the task is resolved. For bug fixes, this can mean Claude tries multiple approaches until the bug is gone.

**Q3: What is the difference between Plan Mode and Auto Mode?**  
A: Plan Mode runs a background sub-agent to create a detailed execution plan before taking any action — it shows you the plan and waits for approval. Auto Mode executes tasks immediately without confirmation. Plan Mode is safer for production code; Auto Mode is faster for trusted development tasks.

**Q4: What are sub-agents and when would you use them?**  
A: Sub-agents are independent Claude instances spawned to handle specific sub-tasks. Each has its own isolated context window and runs in parallel. You use sub-agents when tasks can be divided and executed independently — for example, analyzing three different modules of a codebase simultaneously.

**Q5: How do Agent Teams differ from Sub-Agents?**  
A: Agent Teams are collaborative — they share a visible task list and communicate peer-to-peer. Sub-agents are isolated — they have no awareness of each other and only report back to the parent. Agent Teams are better for complex tasks requiring coordination; sub-agents are better for independent parallel work.

**Q6: What is CLAUDE.md and what goes in it?**  
A: `CLAUDE.md` is a Markdown file in the project root that Claude automatically loads at the start of every conversation. It contains persistent project context: architecture overview, coding conventions, tech stack details, files not to touch, and key configuration. It's generated via `/init` and acts as Claude's long-term memory for the project.

**Q7: What is the Model Context Protocol (MCP)?**  
A: MCP (Model Context Protocol) is Anthropic's standardized interface for connecting external tools, data sources, and services to Claude models. Plugins in Claude Code are essentially MCP servers. It allows Claude to access web search, GitHub, databases, and other third-party capabilities in a structured, safe way.

**Q8: What is a Claude Skill and how do you create one?**  
A: A skill is a reusable set of instructions and examples that teaches Claude how to perform a specific task. Once created, it is saved as a `.md` file and can be invoked by name. Skills are scoped to project, user, or local level. You create a skill by describing the task and workflow to Claude, which generates the skill file automatically.

**Q9: What memory scopes does Claude Code support?**  
A: Three scopes: (1) Project scope — stored in the project folder, visible to everyone on the team; (2) User scope — tied to the OS user account, applies across all projects for that user; (3) Local scope — applies only on the current machine, not synced.

**Q10: How does Claude Code handle context across large codebases?**  
A: Claude Opus 4.7, the default model for Claude Code, has a 1 million token context window — enough to load very large codebases. The CLAUDE.md file provides persistent architectural context. The agentic loop's context-gathering phase reads only the relevant files for each task, keeping context focused and efficient.

---

## 16. Industry Usage

**Onboarding New Developers**  
Companies use Claude Code to help new engineers understand existing codebases in hours instead of days. A developer can ask "analyze this entire project and explain the architecture" and get an immediate, comprehensive overview.

**Automated Code Review**  
Agent teams are deployed to review pull requests: one agent checks for security vulnerabilities, another checks for code style, a third checks for test coverage — all running in parallel and reporting a consolidated review.

**Bug Hunting at Scale**  
The agentic loop's ability to iteratively try fixes makes it powerful for complex, multi-file bugs that would take a human developer hours to track down.

**Feature Development Acceleration**  
Using Plan Mode + Auto Mode together, teams prototype new features rapidly. The developer describes the feature in natural language, Claude generates a plan, and after approval, implements it across multiple files.

**Documentation Generation**  
Skills like "generate API documentation" or "write a changelog" are created once and reused across all projects, standardizing documentation quality.

**Live Library Documentation (Context7 Plugin)**  
Since Claude's training data has a cutoff, the Context7 plugin ensures Claude always uses the *current* version of library documentation — critical when working with rapidly evolving frameworks.

---

## 17. Related Topics

These are the concepts and topics you should study next after completing this course:

- **Deep Agents / Autonomous Agents** — The instructor's next course covers how to build agents like Claude Code from scratch (using LangChain, LangGraph, or similar frameworks)
- **Model Context Protocol (MCP)** — Deep dive into how MCP works and how to build your own MCP servers
- **RAG (Retrieval-Augmented Generation)** — Understanding how retrieval is used to extend LLM context beyond the context window
- **LangChain / LangGraph** — Popular Python frameworks for building agentic workflows
- **OpenAI Agents SDK** — Alternative agentic SDK to compare with Claude's approach
- **Anthropic API** — Direct API access to Claude models for building custom applications
- **Vector Databases** — Pinecone, ChromaDB, Weaviate — used in conjunction with RAG and agents
- **FastMCP** — Framework for building MCP servers (mentioned in comments as having major updates in version 3.0)
- **Claude Certified Architect Exam** — Certification that validates deep knowledge of Claude Code concepts covered in this course

---

## 18. Revision Notes

**Core Concept**
- Claude Code = agentic AI coding tool (terminal + IDE + desktop + browser)
- Not just code completion — it *reads, writes, runs, iterates*

**The Agentic Loop**
- Read context → Execute action → Observe result → Repeat until done
- Adapts depth based on task complexity

**Modes (Shift+Tab to cycle)**
- Plan Mode → makes a plan first, waits for approval
- Auto Mode → fully autonomous
- Accept-Edit Mode → asks per file change

**Memory**
- CLAUDE.md = project persistent memory (auto-loaded every session)
- `/init` generates it automatically from your codebase
- 3 scopes: Project → User → Local

**Models**
- Default: Claude Opus 4.7 (1M token context)
- Alternative: Claude Sonnet 4.6 (faster, smaller)

**Agents**
- Sub-agents = isolated, parallel, no inter-communication, own context window
- Agent Teams = collaborative, shared task list, peer-to-peer communication
- Agent View = live monitoring dashboard for all running agents

**Skills vs Plugins**
- Skill = reusable instruction set (teaches Claude *how* to do something)
- Plugin = external service integration (gives Claude new *capabilities*)
- Key plugins: Exa Search (web), Context7 (live docs)
- Plugin interface = MCP (Model Context Protocol)

**Key Slash Commands**
- `/init` — generate CLAUDE.md
- `/plugins` — browse plugin marketplace

**Pricing**
- Claude Pro plan (~$20/month) = access to Claude Code
- Higher usage → Max plans

**Real-World Tips**
- Always use Plan Mode for production code changes
- Create CLAUDE.md for every serious project
- Use Agent Teams for complex multi-part code reviews
- Use Context7 plugin when working with evolving libraries
- Python knowledge is enough to get started
