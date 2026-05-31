# AI Learning Course – Continuously Evolving Document
> **Source:** [AI Agents for Beginners – Part 1 (Free Labs)](https://www.youtube.com/watch?v=MZhjki7t6p8) – KodeKloud  
> **Last Updated:** 2026-05-31  
> **Course Series:** AI Agents for Beginners (OpenClaw Case Study)  
> **Video Duration:** 1:07:33  

---

# Module 1: AI Agents – Fundamentals & Architecture

---

## 1. Overview

This module is the foundation of AI agent development. It starts from scratch — explaining how ChatGPT and Large Language Models (LLMs) work under the hood — and progressively builds up to understanding tool-calling, AI workflows, and what makes something an "AI agent." By the end of this module you can make your first LLM API call in Python and understand the key architectural differences between workflows and agents.

**Prerequisites:** Basic Python knowledge (variables, functions, loops). No prior AI experience needed.

**Course Path:**
---

## 2. Key Concepts

### 2.1 What is ChatGPT and How GPT Works

**`GPT`** stands for **Generative Pre-trained Transformer**.

- **Generative** – It *generates* new text as output, rather than just classifying or searching.
- **Pre-trained** – It was trained in advance on a massive dataset of internet text, books, and code *before* you ever interact with it.
- **Transformer** – The underlying neural network architecture (introduced in the 2017 paper *"Attention Is All You Need"*). Transformers are exceptionally good at understanding relationships between words across long distances in text.

ChatGPT is a *product* built on top of GPT models (like GPT-3.5, GPT-4, GPT-4o). The model itself is the math — ChatGPT is the interface.

**How it generates text (simplified):**
1. You give it input text (a prompt).
2. The model converts your text into numbers (tokens).
3. It passes those numbers through many layers of the Transformer neural network.
4. It predicts the *most likely next token*, one at a time.
5. It keeps predicting tokens until it decides to stop.

> **Key insight:** ChatGPT doesn't "look up" answers. It *generates* plausible continuations of text based on patterns learned during training.

---

### 2.2 How Large Language Models (LLMs) Work

An **LLM** is a neural network with billions of parameters (weights/numbers), trained on vast amounts of text data to predict the next word/token in a sequence.

**Training process:**
1. Collect a huge corpus of text (web pages, books, code, Wikipedia, etc.)
2. Break the text into tokens.
3. Train the model to predict the next token, given all previous tokens.
4. Adjust billions of internal weights using backpropagation to reduce prediction error.
5. Repeat billions of times until the model learns language patterns deeply.

**After pre-training:** Models are often fine-tuned with human feedback (RLHF – Reinforcement Learning from Human Feedback) to be more helpful, harmless, and honest.

**Popular LLMs:**
| Model | Creator | Notes |
|---|---|---|
| GPT-4o | OpenAI | Multimodal, fast |
| Claude 3.5 / 4 | Anthropic | Strong reasoning |
| Gemini 1.5 / 2 | Google | Long context |
| LLaMA 3 | Meta | Open source |
| Mistral | Mistral AI | Open source, efficient |

---

### 2.3 Tokens & Tokenization

> ⭐ **MUST MEMORIZE:** Tokens are the fundamental unit of all LLM interactions. Everything is measured in tokens.

A **token** is a chunk of text — roughly 3/4 of a word on average. It is *not* exactly a word.

**Examples:**
- `"ChatGPT"` → 2 tokens: `Chat`, `GPT`
- `"tokenization"` → 3 tokens: `token`, `ization`, `...`
- `"Hello"` → 1 token
- `" Hello"` (with space) → 1 token (different from `"Hello"`)
- A single character like `"Z"` → 1 token

**Why tokens matter:**
- **Cost:** LLM APIs (like OpenAI) charge *per token* — both input and output.
- **Speed:** More tokens = slower response.
- **Context limit:** Every LLM has a maximum number of tokens it can process at once (the context window).
- **Behavior:** The LLM "thinks" in tokens, so unusual tokenization of a word can affect its understanding.

**Tokenizer tools:** OpenAI's [Tokenizer](https://platform.openai.com/tokenizer) lets you visualize how text gets tokenized.

**Rule of thumb:** 1,000 tokens ≈ 750 words.

---

### 2.4 Temperature & Sampling

**Temperature** controls the *randomness* (or creativity) of LLM outputs.

Think of it as a dial:
- **Low temperature (0.0 – 0.3):** Deterministic, predictable, focused. The model picks the highest-probability token almost always. Good for factual Q&A, code generation, structured outputs.
- **Medium temperature (0.5 – 0.7):** Balanced creativity and coherence. Good for general conversation and summaries.
- **High temperature (0.8 – 1.5+):** Creative, diverse, sometimes surprising or "hallucinating." Good for brainstorming, creative writing.

**How sampling works under the hood:**
After the model computes a probability distribution over all possible next tokens, sampling strategies determine *how* you pick from that distribution:

- **Greedy sampling:** Always pick the highest probability token (temperature=0 equivalent).
- **Temperature scaling:** Divide the logits (raw scores) by the temperature value before converting to probabilities. Low temperature sharpens the distribution; high temperature flattens it.
- **Top-k sampling:** Only sample from the top-k most likely tokens.
- **Top-p (nucleus) sampling:** Sample from the smallest set of tokens whose cumulative probability exceeds p (e.g., p=0.9).

**Practical guidance:**
| Use Case | Recommended Temperature |
|---|---|
| Code generation | 0.0 – 0.2 |
| Factual Q&A | 0.0 – 0.3 |
| Chatbot conversation | 0.5 – 0.7 |
| Creative writing | 0.8 – 1.2 |
| Brainstorming | 0.9 – 1.3 |

---

### 2.5 Context Windows

> ⭐ **MUST MEMORIZE:** The context window is a hard limit. Exceeding it causes data to be silently dropped.

The **context window** (also called *context length*) is the maximum number of tokens an LLM can process in a single interaction. It includes:
- The system prompt
- The entire conversation history
- The user's current message
- The model's response (generated tokens)

**Why it matters:**
- If your conversation or document exceeds the context window, the model cannot see the older parts — it literally doesn't have access to them.
- This is the LLM's "working memory." It has no persistent memory between sessions unless you explicitly provide it.

**Example sizes:**
| Model | Context Window |
|---|---|
| GPT-3.5 | 16,384 tokens (~12,000 words) |
| GPT-4o | 128,000 tokens (~96,000 words) |
| Claude 3.5 Sonnet | 200,000 tokens (~150,000 words) |
| Gemini 1.5 Pro | 1,000,000+ tokens |

**Real-world implication:** When building agents that maintain long conversations or process large documents, you need strategies like summarization, chunking, or Retrieval-Augmented Generation (RAG) to work around context limits.

---

### 2.6 Prompting Techniques

A **prompt** is the input you provide to an LLM. Prompt engineering is the skill of crafting inputs to get better outputs.

#### 2.6.1 Zero-Shot Prompting
Giving the model a task with *no examples*. Works well for simple tasks because LLMs have seen millions of similar tasks during training.

#### 2.6.2 Few-Shot Prompting
Providing *a few examples* (shots) of input→output pairs before asking the model to complete a new one. This helps the model understand the expected format and style.

#### 2.6.3 Chain-of-Thought (CoT) Prompting
Asking the model to *reason step by step* before giving a final answer. Dramatically improves performance on multi-step reasoning tasks (math, logic, planning).

#### 2.6.4 Role-Based / System Prompting
Assigning a persona or role to the model through a **system prompt** that sets behavior for the entire conversation.

```python
system_prompt = """You are an expert Python developer and code reviewer.
You write clean, efficient code following PEP8 conventions.
When reviewing code, always explain your reasoning."""
```

#### 2.6.5 Other Techniques
- **ReAct Prompting:** Reason + Act — the model interleaves reasoning steps with tool calls. Fundamental to agent design.
- **Self-Consistency:** Generate multiple answers and pick the most common one.
- **Tree-of-Thought:** Explore multiple reasoning branches simultaneously.

---

### 2.7 Your First LLM API Call in Python

```python
from openai import OpenAI

client = OpenAI(api_key="your-api-key-here")

response = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "What is a large language model?"}
    ],
    temperature=0.7
)

print(response.choices[0].message.content)
```

**Key concepts in the API call:**
- `model` – Which LLM to use.
- `messages` – A list of message objects, each with a `role` and `content`.
- `temperature` – Controls randomness (0.0 to 2.0).
- `response.choices[0].message.content` – The generated text response.

---

### 2.8 Roles and Messages

LLM APIs use a structured conversation format with three **roles**:

| Role | Who it represents | Purpose |
|---|---|---|
| `system` | The developer | Sets the AI's persona, instructions, constraints. Only sent once at start. |
| `user` | The end user | The human's messages and questions. |
| `assistant` | The AI model | The AI's previous responses (included for conversation history). |

**Why this matters for agents:** When building agents, you inject tool results, memory, and context into the `system` or `user` messages to guide the agent's behavior.

```python
messages = [
    {"role": "system", "content": "You are a travel planning assistant."},
    {"role": "user", "content": "I want to visit Japan in April."},
    {"role": "assistant", "content": "Great choice! April is cherry blossom season..."},
    {"role": "user", "content": "What about budget accommodations?"}
]
```

---

### 2.9 When to Use an LLM

LLMs are powerful but not always the right tool. Use an LLM when:

✅ The task requires **natural language understanding or generation**  
✅ The input/output is **unstructured text**  
✅ The task benefits from **common-sense reasoning**  
✅ You need **flexible, adaptable** behavior  

Do NOT use an LLM when:  
❌ A simple `if/else` statement or regex would solve it  
❌ You need **100% deterministic** results every time  
❌ The task is purely mathematical (use a calculator/code)  
❌ **Latency and cost** are critical constraints for a simple lookup  

---

### 2.10 What are Tools (Function Calling)

> ⭐ **MUST MEMORIZE:** Tools are what elevate LLMs from "chat assistants" to "agents."

**Tools** (also called *function calling* or *tool use*) allow an LLM to request the execution of external functions — giving it the ability to take actions in the real world.

**How it works:**
1. You define tools (functions) and describe them to the LLM in natural language.
2. When the user asks something that requires a tool, the LLM outputs a *structured request* to call that tool (not the answer itself).
3. Your code executes the tool and returns the result to the LLM.
4. The LLM uses the tool's result to formulate its final answer.

**Example:**
```python
tools = [
    {
        "type": "function",
        "function": {
            "name": "get_weather",
            "description": "Get the current weather for a city",
            "parameters": {
                "type": "object",
                "properties": {
                    "city": {
                        "type": "string",
                        "description": "The city name, e.g., 'London'"
                    }
                },
                "required": ["city"]
            }
        }
    }
]
```

**Real-world tools LLMs can use:**
- Web search (Bing, Google)
- Code execution (Python interpreter)
- Database queries (SQL)
- API calls (weather, stock prices, email)
- File system operations (read/write files)
- Browser automation

---

### 2.11 Tool Integration (The Full Loop)

This loop is the **core mechanism** behind all AI agents.

---

### 2.12 AI Workflows

An **AI Workflow** is a *predefined, deterministic sequence of steps* that may include LLM calls and tool calls, but the overall flow is fixed by the developer.

**Characteristics:**
- The sequence of steps is hardcoded/predetermined.
- If X happens, always do Y then Z.
- Predictable, reliable, easy to debug.
- Less flexible than agents.

**Example – Document Processing Workflow:**

**When to use workflows:**
- When the process is well-defined and repeatable.
- When reliability and auditability matter more than flexibility.
- When you're doing the same task millions of times (cost efficiency).
- Production pipelines, data processing, report generation.

---

### 2.13 AI Agents vs. AI Workflows – The Key Difference

> ⭐ **MUST MEMORIZE:** This is the single most important distinction in modern AI development.

| | **AI Workflow** | **AI Agent** |
|---|---|---|
| **Control flow** | Predetermined by developer | Determined dynamically by the LLM |
| **Decision making** | Hardcoded if/else logic | LLM decides what to do next |
| **Flexibility** | Low | High |
| **Reliability** | High (predictable) | Lower (can make unexpected decisions) |
| **Use case** | Known, repetitive tasks | Open-ended, novel tasks |
| **Cost** | Lower (efficient) | Higher (more LLM calls) |
| **Debugging** | Easy | Hard |

**The fundamental difference:** In a workflow, *you* decide what happens next. In an agent, *the LLM* decides what happens next.

**An AI Agent:**
1. Receives a high-level goal from the user.
2. Uses an LLM to *reason* about what steps to take.
3. Selects and calls tools based on its reasoning.
4. Observes the results and *re-reasons*.
5. Continues until the goal is achieved.

This **Reason → Act → Observe → Repeat** loop is called the **ReAct pattern** and is the foundation of almost all agents.

---

### 2.14 When to Use Workflows vs. Agents

**Use a Workflow when:**
- The task is well-defined and repeatable (e.g., "every new user gets a welcome email")
- You need deterministic, auditable results
- Cost and latency are primary concerns
- The task is a known, structured process

**Use an Agent when:**
- The task is open-ended or complex (e.g., "research this company and write a report")
- The steps to completion are not known upfront
- The agent needs to adapt based on intermediate results
- You need multi-step reasoning over multiple data sources

**In practice:** Many production systems use a *hybrid* approach — a workflow orchestrates the overall process, but individual steps may be agentic.

---

## 3. Terminology

| Term | Definition |
|---|---|
| **LLM** | Large Language Model — a neural network trained on massive text data to generate human-like text |
| **GPT** | Generative Pre-trained Transformer — the architecture behind ChatGPT |
| **Transformer** | Neural network architecture using attention mechanisms, ideal for sequence data |
| **Token** | The basic unit of text LLMs process (~3/4 of a word on average) |
| **Tokenization** | The process of splitting text into tokens before feeding to an LLM |
| **Temperature** | Parameter (0.0–2.0) controlling randomness in LLM output |
| **Context Window** | Maximum tokens an LLM can process in a single interaction |
| **Prompt** | The input text provided to an LLM |
| **Prompt Engineering** | The skill of crafting inputs to get better LLM outputs |
| **Zero-shot** | Asking the model to complete a task with no examples |
| **Few-shot** | Providing a few input→output examples before the main task |
| **Chain-of-Thought (CoT)** | Prompting the model to reason step-by-step |
| **System Prompt** | Developer-defined instructions that guide the LLM's entire behavior |
| **Function Calling / Tool Use** | Mechanism allowing LLMs to request execution of external functions |
| **AI Workflow** | Predefined sequence of steps with fixed control flow |
| **AI Agent** | System where an LLM dynamically determines what actions to take |
| **ReAct Pattern** | Reason-Act-Observe loop; the core pattern of most AI agents |
| **RLHF** | Reinforcement Learning from Human Feedback — technique used to fine-tune LLMs for safety and helpfulness |
| **Hallucination** | When an LLM confidently generates incorrect or fabricated information |
| **Inference** | Running a trained model to generate outputs (as opposed to training) |
| **Parameters** | The billions of numerical weights in an LLM that encode its knowledge |
| **Fine-tuning** | Further training a pre-trained model on specific data to adapt its behavior |

---

## 4. Examples

### Example 1: Token counting impact on cost
```python
# GPT-4o pricing: ~$0.005 per 1,000 input tokens
text = "Tell me about the history of artificial intelligence and its impact on modern society"
# ≈ 15 tokens → costs fractions of a cent

long_doc = open("contract.pdf").read()  # 50,000 words ≈ 66,667 tokens
# Input cost alone: ~$0.33 per call
# For 1,000 users/day: ~$330/day just for input tokens
```

### Example 2: Temperature effect on code generation
```python
# Low temperature → consistent, safe output
response_low = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "Write a Python function to sort a list"}],
    temperature=0.0  # Deterministic
)

# High temperature → creative but potentially buggy
response_high = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "Write a Python function to sort a list"}],
    temperature=1.5  # Creative/random
)
```

### Example 3: Tool-calling agent (minimal implementation)
```python
import json
from openai import OpenAI

client = OpenAI()

def get_weather(city: str) -> str:
    # In reality, call a weather API
    return f"Weather in {city}: 22°C, Partly Cloudy"

def run_agent(user_message: str):
    tools = [{
        "type": "function",
        "function": {
            "name": "get_weather",
            "description": "Get current weather for a city",
            "parameters": {
                "type": "object",
                "properties": {"city": {"type": "string"}},
                "required": ["city"]
            }
        }
    }]
    
    messages = [{"role": "user", "content": user_message}]
    
    while True:
        response = client.chat.completions.create(
            model="gpt-4o",
            messages=messages,
            tools=tools
        )
        
        msg = response.choices[0].message
        
        # If the model wants to call a tool
        if msg.tool_calls:
            messages.append(msg)  # Add assistant's tool request
            for tool_call in msg.tool_calls:
                args = json.loads(tool_call.function.arguments)
                result = get_weather(**args)
                messages.append({
                    "role": "tool",
                    "tool_call_id": tool_call.id,
                    "content": result
                })
        else:
            # Model is done — return final answer
            return msg.content

print(run_agent("What's the weather like in Tokyo?"))
# Output: "The current weather in Tokyo is 22°C and partly cloudy."
```

### Example 4: Context Window Overflow Problem
```python
# This will silently drop older messages when you exceed the context limit
conversation_history = []

def chat(user_message):
    conversation_history.append({"role": "user", "content": user_message})
    
    # WARNING: After ~100+ exchanges, older messages are truncated!
    # The model will "forget" earlier parts of the conversation
    response = client.chat.completions.create(
        model="gpt-4o",
        messages=conversation_history
    )
    
    reply = response.choices[0].message.content
    conversation_history.append({"role": "assistant", "content": reply})
    return reply

# Solution: implement a sliding window, summarization, or use RAG
```

---

## 5. Common Doubts

**Q: Is ChatGPT the same as GPT-4?**  
A: No. GPT-4 is the underlying *model* (the mathematical engine). ChatGPT is a *product* (the chat interface, guardrails, memory features, and UI) built on top of GPT models. You can access GPT-4 directly through the OpenAI API without going through ChatGPT.

**Q: Why does the LLM give different answers to the same question each time?**  
A: Because of temperature and sampling. When temperature > 0, the model randomly samples from probable next tokens, so outputs vary. Set temperature=0 for consistent results (though not 100% guaranteed identical due to floating-point arithmetic).

**Q: What happens when the context window is full?**  
A: Older tokens are *silently dropped* from the model's context. The model cannot see them and will not know they existed. This can cause the model to "forget" earlier instructions or facts. There is no warning — you must track token counts manually.

**Q: How is a token different from a word?**  
A: Tokens are subword units. Common short words are one token. Longer or unusual words may be multiple tokens. Numbers and punctuation have their own tokens. The exact tokenization depends on the model's vocabulary (BPE — Byte Pair Encoding is common).

**Q: Do I always need tools to build an agent?**  
A: Yes, in practice. Without tools, the LLM can only generate text — it can't take actions. Tools are what give agents the ability to search the web, write files, call APIs, run code, and interact with the real world.

**Q: What's the difference between a workflow and an agent, really?**  
A: Ask yourself: *who decides what happens next?* If your Python code decides (if/else, hardcoded steps) → it's a workflow. If the LLM decides what action to take next based on reasoning → it's an agent.

**Q: Is it expensive to use LLM APIs?**  
A: It depends on usage. For prototyping and learning, costs are negligible (often under $1 for hundreds of calls). For production at scale, costs can be significant and need to be monitored. Using smaller, cheaper models (like gpt-4o-mini, Claude Haiku) for simple tasks helps control costs.

**Q: Can agents make mistakes?**  
A: Yes, frequently. Agents can hallucinate tool arguments, get stuck in loops, take wrong actions, or misunderstand goals. This is why production agents need careful guardrails, human-in-the-loop checkpoints, and extensive testing.

**Q: What is RLHF and why does it matter?**  
A: RLHF (Reinforcement Learning from Human Feedback) is the process that makes raw LLMs "assistant-like." Without RLHF, a model trained purely on internet text would often be harmful, unhelpful, or offensive. RLHF trains the model to prefer responses that humans rate as helpful and safe.

---

## 6. Interview Questions

**Q1: What is a Large Language Model (LLM)?**  
A: An LLM is a neural network with billions of parameters trained on massive text corpora. It uses the Transformer architecture and is trained to predict the next token in a sequence. Through this training, it learns grammar, facts, reasoning patterns, and even programming. Examples include GPT-4, Claude, and Gemini.

**Q2: What is tokenization and why does it matter for LLMs?**  
A: Tokenization is the process of splitting text into tokens — the basic units LLMs process. It matters because: (1) LLM APIs charge per token, (2) context windows are measured in tokens not words, (3) unusual tokenization of words can affect model behavior. Using tools like OpenAI's tokenizer helps estimate cost and context usage.

**Q3: Explain the context window. What happens when you exceed it?**  
A: The context window is the maximum number of tokens an LLM can process in one call, including all input and output. Exceeding it causes older tokens to be silently dropped from the model's view. Solutions include sliding window approaches, summarization of older context, and RAG (Retrieval Augmented Generation).

**Q4: What is temperature in LLMs and when would you set it to 0?**  
A: Temperature controls output randomness. Temperature=0 makes the model nearly deterministic (always picks the highest probability next token), useful for code generation, structured data extraction, or any task requiring consistent, repeatable outputs. Higher temperatures increase creativity but also risk of incoherence.

**Q5: What is function calling / tool use in LLMs?**  
A: Tool use allows LLMs to request execution of predefined functions. The developer describes available functions (name, description, parameters) to the model. When the user asks something requiring a tool, the model outputs a structured tool call request. The developer's code executes the function and returns the result to the model, which then generates a final response. This enables agents to interact with external systems.

**Q6: What is the difference between an AI workflow and an AI agent?**  
A: In a workflow, the developer hardcodes the control flow — the steps are predetermined and executed sequentially. In an agent, the LLM dynamically decides what actions to take next based on its reasoning. Agents are more flexible and can handle open-ended tasks, but are less predictable and more expensive than workflows.

**Q7: What is the ReAct pattern?**  
A: ReAct (Reason + Act) is a prompting/architectural pattern where the LLM alternates between reasoning steps and action steps. The model thinks "I need to do X, so I'll call tool Y," executes Y, observes the result, then reasons again about what to do next. This loop continues until the goal is achieved. It's the foundational pattern for most modern AI agents.

**Q8: What are the three message roles in the OpenAI chat API?**  
A: `system` (developer instructions that set the AI's behavior), `user` (human messages), and `assistant` (AI's previous responses, used to maintain conversation history). A fourth role, `tool`, is used when returning tool call results.

**Q9: What is few-shot prompting and when would you use it?**  
A: Few-shot prompting provides a few input→output examples in the prompt before the actual task. It helps the model understand the expected format, style, or reasoning pattern. It's useful when the task has a specific output format (e.g., JSON extraction), when zero-shot performance is poor, or when demonstrating a non-obvious pattern.

**Q10: What is chain-of-thought prompting?**  
A: CoT prompting instructs the model to think step-by-step before giving a final answer. Adding phrases like "Let's think step by step" or showing reasoning examples dramatically improves performance on multi-step math, logic, and planning tasks. It works because it forces the model to use intermediate computation steps rather than jumping to a conclusion.

---

## 7. Industry Usage

**LLMs & Tokens:**
- Every LLM-powered product (GitHub Copilot, Notion AI, Cursor) tracks token usage internally to manage costs and context.
- Enterprises building on LLM APIs implement token counting to estimate costs and prevent context overflows at scale.

**Temperature in Production:**
- Code generation tools (GitHub Copilot, Cursor) use low temperatures (0.0–0.2) for reliable, consistent code.
- Customer service bots use medium temperatures (0.5–0.6) to sound natural but stay on-topic.
- Marketing copy generators use higher temperatures (0.8+) for creative variety.

**Prompting Techniques:**
- Every major AI product has a team of "prompt engineers" or maintains a library of carefully crafted system prompts.
- Few-shot examples are embedded in system prompts to ensure consistent output format for parsing.

**Tool Use / Function Calling:**
- **Salesforce Einstein:** Uses tool calling to query CRM databases and update records via natural language.
- **Microsoft Copilot:** Calls Office 365 APIs (calendar, email, documents) through tool use.
- **Perplexity AI:** Uses web search as a tool to ground responses in current information.
- **OpenAI Assistants API / GPTs:** Built-in tools: code interpreter, file search, custom functions.

**AI Workflows:**
- Companies like Zapier, n8n, and Make (formerly Integromat) build workflow automation with embedded LLM steps.
- CI/CD pipelines that include AI steps (automatic PR review, changelog generation) are workflows.

**AI Agents:**
- **Devin (Cognition AI):** Software engineering agent that autonomously writes, debugs, and deploys code.
- **AutoGPT / BabyAGI:** Early open-source agent projects that popularized autonomous LLM agents.
- **OpenAI Swarm / CrewAI:** Multi-agent frameworks used in research and production for complex tasks.
- **Enterprise use cases:** Autonomous research agents, customer support escalation agents, financial report analysis agents.

---

## 8. Related Topics (Learn Next)

After completing this module, study these topics in order:

1. **RAG (Retrieval-Augmented Generation)** – How to give agents access to private/large knowledge bases without hitting context limits. [(KodeKloud RAG Crash Course)](https://kode.wiki/42tYcoz)
2. **Vector Databases** – The storage backbone of RAG systems (Pinecone, Weaviate, ChromaDB, pgvector).
3. **LangChain / LangGraph** – Popular frameworks for building LLM applications and multi-step agents.
4. **Multi-Agent Systems** – Orchestrating multiple specialized agents working together on complex tasks.
5. **Memory & Reasoning in Agents** – Short-term vs long-term memory, episodic memory, semantic memory.
6. **MCP (Model Context Protocol)** – Anthropic's open standard for giving AI models access to tools and context. [(KodeKloud MCP Tutorial)](https://kode.wiki/4cvYZeE)
7. **Evaluation & Testing for LLM Apps** – How to measure and improve agent reliability (evals, tracing with LangSmith/Arize).
8. **AI Fundamentals** – Backpropagation, neural networks, embeddings. [(KodeKloud AI Fundamentals)](https://kode.wiki/4cII5cZ)

**Prerequisite graph:**

---

## 9. Revision Notes

- **GPT** = Generative Pre-trained Transformer. ChatGPT is a product; GPT-4 is the model.
- LLMs predict the **next token** one at a time based on patterns learned during training.
- **Tokens** ≈ 3/4 of a word. Everything (cost, limits, speed) is measured in tokens.
- **Temperature = 0** → deterministic. **Temperature = 1+** → creative/random.
- **Context window** = working memory. It's a hard limit. Exceeding it silently drops old content.
- **System prompt** sets behavior. **User** sends messages. **Assistant** is the AI's response history.
- **Zero-shot** = no examples. **Few-shot** = provide examples. **CoT** = step-by-step reasoning.
- **Tools** = external functions the LLM can call. This is what makes an LLM an "agent."
- **Workflow** = developer decides steps (hardcoded). **Agent** = LLM decides steps dynamically.
- **ReAct loop** = Reason → Call Tool → Observe Result → Reason Again → Repeat.
- Use **workflows** for predictable, repeatable tasks. Use **agents** for open-ended, complex tasks.
- Most production systems are **hybrids**: a workflow orchestrates, agents handle complex subtasks.

---

*Document Version: 1.0 | Source: AI Agents for Beginners – Part 1 by KodeKloud | Updated: 2026-05-31*  
*Next update: Will be extended when Part 2 or additional videos are processed.*
