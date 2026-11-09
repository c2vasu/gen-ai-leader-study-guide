# Section 3 — Techniques to Improve Gen AI Model Output (~20%)

## 3.1 Overcoming Model Limitations

**Definition / Concept:**
Foundation models are powerful but imperfect. Leaders must recognize the limits and choose the right fix.

| Limitation | What it looks like | Typical mitigation |
|------------|--------------------|--------------------|
| **Data dependency** | Output quality depends on training data quality | Better data, grounding, fine-tuning |
| **Knowledge cutoff** | Model doesn't know recent events or your private data | **Grounding / RAG** |
| **Bias & fairness** | Skewed or unfair outputs reflecting training data | Diverse data, evaluation, HITL review, responsible AI practices |
| **Hallucinations** | Confident but false or made-up answers | **Grounding**, RAG, citations, lower temperature, HITL |
| **Edge cases** | Fails on rare or unusual inputs | Testing, few-shot examples, fine-tuning, human fallback |

**Recommended practices:**
- **Grounding & RAG:** connect outputs to trusted, current sources.
- **Prompt engineering:** clearer instructions, examples, constraints.
- **Fine-tuning:** adapt a model to a specialized domain, style or task using your own examples.
- **Human-in-the-loop (HITL):** humans review, correct or approve outputs. This is essential in high-stakes areas (healthcare, finance, legal, content moderation).
  - *Pre-generation / pre-deployment:* humans curate data, design prompts, test.
  - *Post-generation:* humans review outputs and give feedback.

**Monitoring and managing models on Google Cloud:**

| Practice | Tool |
|----------|------|
| **Versioning** and lineage | Agent Platform **Model Registry** |
| **Drift monitoring** (input data or predictions change over time) | **Model Monitoring** |
| **Performance tracking** | Evaluation metrics, dashboards, Cloud Monitoring |
| Reusable features | **Feature Store** |
| **Automation** of retraining and deployment | Agent Platform **Pipelines** |

**Choosing a fix (from cheapest and fastest to most expensive):**
```
Prompt engineering  →  Grounding / RAG  →  Fine-tuning  →  Train a custom model
```

**Pitfalls / Gotchas:**
- Fine-tuning teaches **style, format or domain behaviour**. It is not the best way to add **frequently changing facts**. Use RAG for that.
- Drift means the world changed after deployment. A model that was accurate at launch can degrade.

**Exam Tips:**
- "Model doesn't know last week's pricing changes" → **grounding / RAG**, not retraining.
- "Must review AI-drafted medical summaries before sending" → **human-in-the-loop**.

---

## 3.2 Prompt Engineering Techniques

**Definition / Concept:**
**Prompt engineering** is the practice of designing inputs that guide a model to useful, accurate and consistent outputs. It is the fastest, cheapest lever to improve results.

| Technique | Description | Example |
|-----------|-------------|---------|
| **Zero-shot** | Task with no examples | "Classify this review as positive or negative: …" |
| **One-shot** | One example included | "Review: 'Loved it' → Positive. Now classify: …" |
| **Few-shot** | Several examples to show pattern and format | 3–5 labeled examples, then the new input |
| **Role prompting** | Give the model a persona | "You are a senior supply-chain analyst. Explain …" |
| **Prompt chaining** | Break a task into steps; each output feeds the next prompt | Summarize → extract action items → draft email |
| **Chain-of-thought (CoT)** | Ask for step-by-step reasoning | "Think through this step by step before answering." |
| **ReAct (Reason + Act)** | The model alternates reasoning with actions (tool calls), observing results | An agent reasons, calls a search tool, reads the result, reasons again |
| **Metaprompting** | Use a prompt to create or improve other prompts | "Write a better prompt for summarizing contracts." |

**Prompting workflow habits:**
- Save **prompt templates** for repeated tasks.
- Use **Gems** to store instructions for a reusable assistant.
- Be specific: task, context, format, constraints, audience, tone.

**When to use which:**
- **CoT:** math, logic, multi-step reasoning or analysis.
- **ReAct:** tasks that need **external information or actions** (agents).
- **Few-shot:** when output **format or style** must be consistent.

**Pitfalls / Gotchas:**
- ReAct includes *acting* with tools. CoT is only reasoning.
- Prompt chaining (several separate prompts) is different from chain-of-thought (reasoning inside one answer).

**Exam Tips:**
- "Output format keeps varying" → **few-shot** examples.
- "Agent must look things up and decide next steps" → **ReAct**.

---

## 3.3 Grounding, RAG and Sampling Settings

**Definition / Concept:**
**Grounding** connects model output to **verifiable sources of information**, which reduces hallucinations and adds freshness and relevance.

**Types of grounding data:**

| Type | Source | Example |
|------|--------|---------|
| **First-party** | Your own enterprise data | Internal policies, CRM, product docs |
| **Third-party** | Data from partners or licensed providers | Market data, industry databases |
| **World data** | Public information on the web | **Grounding with Google Search** |

**Retrieval-Augmented Generation (RAG):**
1. **Retrieve** the relevant information (usually via semantic/vector search over your data).
2. **Augment** the prompt with that information.
3. **Generate** a response based on it, ideally with citations.
4. *(Optional)* **Iterate:** refine the retrieval and repeat.

**Effect on output:** more accurate, current and specific answers, traceable to sources, without retraining the model.

**Google grounding offerings:** Grounding with Google Search, Agent Search, RAG Engine, Vector Search, Gemini Enterprise connectors, and Gemini Notebook for personal research.

**Sampling and generation settings:**

| Setting | What it controls | Lower value → | Higher value → |
|---------|------------------|---------------|----------------|
| **Temperature** | Randomness / creativity | Focused, predictable, factual | Varied, creative |
| **Top-p** (nucleus sampling) | Picks from the smallest set of tokens whose combined probability reaches *p* | Narrower word choice | Wider word choice |
| **Top-k** | Picks from the *k* most likely tokens | Safer | More diverse |
| **Max output tokens / output length** | Maximum response length | Short, cheaper | Longer, costlier |
| **Safety settings** | Thresholds for blocking harmful content categories | — | — |

**Pitfalls / Gotchas:**
- Temperature changes **creativity**, not **knowledge**. A low temperature won't fix missing facts; grounding will.
- A token is not exactly a word. Token limits affect both **cost** and **truncation**.

**Exam Tips:**
- "Legal summaries must be consistent and factual" → **low temperature** + grounding.
- "Brainstorm many slogan ideas" → **higher temperature**.
- "Needs today's news" → **Grounding with Google Search** (world data).

---

## Quick Check

1. A chatbot invents return-policy details. What is the best first fix?
   <details><summary>Answer</summary>Ground it in the official return-policy documents (RAG / grounding).</details>
2. Which technique gives the model several worked examples to copy a format?
   <details><summary>Answer</summary>Few-shot prompting.</details>
3. Which parameter should you lower to get more deterministic answers?
   <details><summary>Answer</summary>Temperature.</details>
