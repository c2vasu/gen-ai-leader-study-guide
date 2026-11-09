# Section 2 — Google Cloud's Gen AI Offerings (~35%)

> **Naming note (2026):** At Google Cloud Next '26 (April 2026), **Vertex AI was renamed Gemini Enterprise Agent Platform** ("Agent Platform"), and many features got new names. Older courses and practice tests may still use the old names. See the [name-change table](../README.md#product-name-changes-2026) in the README.

## 2.1 Google Cloud's Strengths

**Definition / Concept:**
Know *why* an organization would choose Google Cloud for gen AI. Each strength maps to a business concern.

| Strength | What it means | Business concern it answers |
|----------|---------------|-----------------------------|
| **AI-first innovation** | Google Research and Google DeepMind produced many of the core advances (for example, the Transformer architecture) and ship them into products | "Will we get access to leading models?" |
| **Enterprise-ready, responsible platform** | Security, privacy, compliance, governance and AI Principles are built in | "Is it safe for regulated data?" |
| **Integrated ecosystem** | AI works across Workspace, Cloud, BigQuery, security tools and more | "Will it fit how we already work?" |
| **Open approach** | Model Garden offers Google, third-party (for example, Anthropic Claude, Meta Llama) and open-source models, plus open frameworks and standards | "Will we be locked into one model?" |
| **AI-optimized infrastructure** | Custom TPUs, GPUs and AI Hypercomputer | "Can it scale cost-effectively?" |

**Data control:** your data stays yours. Google Cloud does not use customer enterprise data to train its foundation models without permission, and customers control access, encryption and residency.

**Democratized development:** tools for every skill level, from no-code (Gemini Enterprise agent designer, AppSheet) and low-code (Agent Studio, AutoML) to full-code (ADK, APIs, notebooks).

**Exam Tips:**
- "Wants flexibility to use non-Google models" → **open approach / Model Garden**.
- "Worried about proprietary data training public models" → **data control / enterprise-ready**.

---

## 2.2 Prebuilt Offerings for AI-Powered Work

**Definition / Concept:**
Ready-to-use products that deliver value **without building anything**.

| Offering | What it is | Best for |
|----------|-----------|----------|
| **Gemini app** | Google's conversational AI assistant for writing, brainstorming, summarizing, translating and image generation | Individual productivity |
| **Gemini Advanced** (as named in the exam guide) | Upgraded tier with more capable models, longer context and extra features | Power users needing deeper reasoning |
| **Gems** | Custom, reusable Gemini assistants with saved instructions | Repeating the same task consistently |
| **Google Workspace with Gemini** | Gen AI built into Gmail, Docs, Sheets, Slides, Meet, Drive | Teams working in Workspace every day |
| **Gemini Enterprise** | Google's enterprise AI platform for employees: search across company data, chat, and prebuilt or custom agents that connect to business systems (absorbed the former **Google Agentspace**) | Company-wide knowledge discovery and agentic workflows |
| **Gemini Notebook** (notebooklm.google.com) | Research assistant grounded **only in the sources you upload**; can produce summaries, Q&A and audio overviews | Studying, research and briefing packs |
| **Gemini for Google Cloud** | AI assistance inside Google Cloud for coding, cloud operations, BigQuery data analysis and security | Developers, data and ops teams |

**Pitfalls / Gotchas:**
- The **Gemini app** is general-purpose. **Gemini Enterprise** connects to *your company's* data sources with enterprise access controls.
- Gemini Notebook grounds answers in your uploaded sources, so hallucination risk is lower and citations point to your documents.

**Exam Tips:**
- "Employees spend hours searching across Drive, Confluence, Jira and SharePoint" → **Gemini Enterprise**.
- "Help drafting emails and summarizing meetings in existing tools" → **Workspace with Gemini**.

---

## 2.3 Customer Experience Offerings

**Definition / Concept:**
Offerings aimed at **external customers**, not employees.

**Agent Search** (formerly Vertex AI Search)
- Google-quality search, recommendations and conversational answers over your own websites, product catalogs and documents.
- Variants: **Agent Search for Commerce** (product discovery and recommendations) and **Agent Search for Industry** (for example, healthcare and media).
- Value: better self-service, higher conversion, fewer support contacts.

**Gemini Enterprise for Customer Experience (CX)** (formerly Contact Center AI, then Customer Engagement Suite)

| Component | Who it helps | What it does |
|-----------|-------------|--------------|
| **Customer Experience Agent Studio** | Customers | Build virtual agents (chat and voice) that combine generative and deterministic flows for 24/7 self-service |
| **Agent Assist** | Human support agents | Real-time suggestions, knowledge assist, smart replies, summaries and live translation |
| **Customer Experience Insights** | Managers / QA | Analyse every conversation for topics, sentiment, call drivers and KPIs |
| **Cloud contact center platform** | Operations | The omnichannel contact center the components run on |

**Exam Tips:**
- "Website visitors can't find products" → **Agent Search (for Commerce)**.
- "Reduce average handle time for human agents" → **Agent Assist**.
- "Understand why customers are calling" → **CX Insights**.

---

## 2.4 Developer Tools: Agent Platform, RAG and Custom Agents

**Definition / Concept:**
**Gemini Enterprise Agent Platform** is Google Cloud's unified platform to **build, scale, govern and optimize** models and agents.

| Capability | Former name | What it gives you |
|------------|-------------|-------------------|
| **Model Garden** | Vertex AI Model Garden | Catalog of 200+ Google, third-party and open models |
| **Agent Studio** | Vertex AI Studio | Console workspace to test prompts, compare models, tune and build gen AI apps |
| **Model Builder / AutoML** | Vertex AI training / AutoML | Train custom models; AutoML trains with minimal ML expertise |
| **RAG Engine** | Vertex AI RAG Engine | Managed retrieval-augmented generation over your data |
| **Vector Search** | Vertex AI Vector Search | Fast similarity search over embeddings |
| **Agent Search** | Vertex AI Search | Out-of-the-box enterprise search and grounding |
| **Agent Development Kit (ADK)** | — | Open-source framework for code-first agent building |
| **Agent Runtime** | Vertex AI Agent Engine | Managed runtime to deploy and scale agents (with Sessions, Memory Bank) |
| **MLOps tools** | Vertex AI … | Model Registry, Model Monitoring, Pipelines, Feature Store, Experiments |

**Google Cloud RAG options (from least to most effort):**
1. **Grounding with Google Search** for public, fresh information.
2. **Agent Search** for turnkey search and grounding on your data.
3. **RAG Engine** for a managed pipeline with more control.
4. **Vector Search + custom code** for full control.

**Ways to build custom agents:**
- **No-code:** Gemini Enterprise agent designer.
- **Low-code:** Agent Studio.
- **Code-first:** ADK, deployed to Agent Runtime.

**Pitfalls / Gotchas:**
- Agent Platform is the **platform layer**. Gemini Enterprise is the **application layer** for employees.
- RAG does **not** retrain the model. It adds retrieved facts to the prompt at query time.

**Exam Tips:**
- "Compare Gemini against an open model before choosing" → **Model Garden / Agent Studio**.
- "Answers must come from our policy documents" → a **RAG** offering (Agent Search or RAG Engine).

---

## 2.5 Agent Tooling, APIs and Which Studio to Use

**Definition / Concept:**
An **agent** combines a **model** (the brain), **tools** (the hands) and a **reasoning loop** (observe → interpret → reason → act).

**Agent tool types:**

| Tool | Purpose | Example |
|------|---------|---------|
| **Extensions** | Connect to external APIs | Call a weather or shipping API |
| **Functions** | Let the model trigger specific actions you define | `create_ticket()`, `refund_order()` |
| **Data stores** | Give the agent access to information | Product catalog, FAQ documents, databases |
| **Plugins** | Add new skills or capabilities | A calendar or CRM plugin |

**Agent types:**
- **Deterministic:** predefined flows and rules, predictable (for example, a password-reset flow).
- **Generative:** LLM-driven, flexible natural conversation.
- **Hybrid:** a mix of the two. Common in production because it pairs control with flexibility.

**Pre-built AI APIs (no model training needed):**

| API | Use |
|-----|-----|
| Speech-to-Text / Text-to-Speech | Transcription, voice responses |
| Translation / Document Translation | Translate text; Document Translation keeps formatting and layout |
| Document AI | Extract and classify data from forms, invoices and contracts |
| Cloud Vision | Detect labels, text (OCR), objects and faces in images |
| Video Intelligence | Detect objects, scenes and shot changes in video |
| Natural Language | Sentiment, entities, classification |

**Other ways to put Gemini to work:**
- Call the **Gemini API** from **Cloud Run** or **Cloud Run functions**, or from **Apps Script** (Workspace automation) or **AppSheet** (no-code apps).
- **On device:** **Gemini Nano** and **LiteRT** (formerly TensorFlow Lite) for low-latency, offline or privacy-sensitive use.

**Agent Studio vs. Google AI Studio:**

| | **Google AI Studio** | **Agent Studio** (on Agent Platform) |
|---|---|---|
| Audience | Individuals, startups, quick experiments | Enterprises |
| Strength | Free, fast prototyping with the Gemini API | Production-ready: security, governance, IAM, data residency, MLOps, SLAs |
| Use when | "Try an idea in an afternoon" | "Deploy to customers at scale under enterprise controls" |

**Exam Tips:**
- "Extract invoice numbers and totals from PDFs" → **Document AI**.
- "Prototype quickly at no cost" → **Google AI Studio**. "Enterprise security and scale" → **Agent Studio**.
- "Agent must look up order status in our system" → a **function** or **extension** tool.

---

## Quick Check

1. A support team wants real-time suggested answers while they talk to customers. Which product?
   <details><summary>Answer</summary>Agent Assist (part of Gemini Enterprise for CX).</details>
2. What was Vertex AI renamed to in 2026?
   <details><summary>Answer</summary>Gemini Enterprise Agent Platform (Agent Platform).</details>
3. An agent needs to read the company's product FAQ to answer questions. Which tool type provides this?
   <details><summary>Answer</summary>A data store.</details>
