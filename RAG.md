# AI Learning Course — Continuously Evolving Knowledge Base

> **Maintained Format:** Each topic is a standalone section. Cross-references link related topics.
> **Last Updated:** 2026-05-31
> **Source Videos:** KodeKloud – RAG Crash Course for Beginners (YouTube, Sep 22, 2025)

---

# Topic: Retrieval Augmented Generation (RAG)

## Overview

RAG (Retrieval Augmented Generation) is a technique that enhances Large Language Models (LLMs) by giving them access to external, up-to-date, or domain-specific knowledge at query time — without needing to retrain the model. Instead of relying solely on what the LLM memorized during training, RAG *retrieves* relevant documents from a knowledge base and *augments* the LLM's prompt with that context before generating a response.

**Analogy:** Think of an LLM as a very smart student who studied a lot but graduated in 2023. RAG is like giving that student an open-book exam — they can look up the latest information before answering.

**Video Source:** [RAG Crash Course for Beginners — KodeKloud](https://www.youtube.com/watch?v=swvzKSOEluc) (58:49)

---

## Key Concepts

### 1. The Problem RAG Solves

Large Language Models have two major limitations:
- **Knowledge cutoff:** They only know information up to their training date.
- **No private knowledge:** They have no access to your company's internal documents, policies, or proprietary data.

RAG solves both by connecting the LLM to an external, queryable knowledge base at inference (answer) time.

**Example use case:** A company wants a chatbot that answers questions about their internal HR policies. The LLM has never seen these documents. RAG retrieves the relevant policy sections and feeds them to the LLM so it can give accurate answers.

---

### 2. When NOT to Use RAG

RAG is powerful but not always the right solution. Avoid RAG when:

- **The LLM already knows the answer well** — e.g., general coding questions, math, public knowledge. Adding RAG adds unnecessary latency and cost.
- **You need reasoning, not retrieval** — some problems require the model to reason step-by-step rather than look things up.
- **Your data changes extremely frequently** — the retrieval index must be kept up to date; very high-frequency updates can be complex.
- **Low-latency is critical** — the retrieval step adds extra time to every response.
- **Fine-tuning is a better fit** — if you want the model to *behave differently* (e.g., write in a specific style), fine-tuning is more appropriate than RAG.

> **Key Insight:** RAG is for *knowledge injection*, not for changing model behavior or personality.

---

### 3. What is RAG? — The Full Architecture

The RAG pipeline has two major phases:

**Phase 1 — Indexing (Offline, done once or periodically):**
1. Collect your documents (PDFs, websites, databases, etc.).
2. Split documents into smaller chunks.
3. Convert each chunk into a numerical vector (embedding).
4. Store all vectors in a Vector Database.

**Phase 2 — Retrieval + Generation (Online, happens per query):**
1. User asks a question.
2. Convert the question into a vector (using the same embedding model).
3. Search the Vector Database for the most similar vectors (nearest neighbor search).
4. Retrieve the top-k matching document chunks.
5. Inject those chunks into the LLM prompt as context.
6. LLM generates an answer grounded in that retrieved context.
