# Section 1 — Fundamentals of Gen AI (~30%)

## 1.1 Core Concepts and Use Cases

**Definition / Concept:**
The exam expects you to explain the main AI terms in business language and see how they relate to each other.

| Term | Plain-English meaning |
|------|-----------------------|
| **Artificial Intelligence (AI)** | Machines doing tasks that normally need human intelligence (reasoning, perception, language). |
| **Machine Learning (ML)** | A subset of AI where systems learn patterns from data instead of following hand-written rules. |
| **Deep Learning** | ML that uses neural networks with many layers. Powers modern vision, speech and language models. |
| **Generative AI (gen AI)** | AI that **creates new content**: text, images, audio, video and code. |
| **Natural Language Processing (NLP)** | The field that teaches computers to understand and produce human language. |
| **Foundation model** | A large model trained on huge amounts of broad, mostly unlabeled data, which can be adapted to many tasks. |
| **Large Language Model (LLM)** | A foundation model specialized in understanding and generating language. |
| **Diffusion model** | A generative model, used mostly for images and video, that learns to turn random noise step by step into a coherent output. |
| **Multimodal model** | A model that can take in and/or produce several types of data (text, image, audio, video). |
| **Prompt** | The input or instructions you give a model. |
| **Prompt engineering** | Designing prompts so the model gives better, more reliable outputs. |
| **Token** | A chunk of text (part of a word, a word or punctuation) that models read and generate. |
| **Context window** | How much input (in tokens) a model can consider at one time. |

```
AI  ⊃  Machine Learning  ⊃  Deep Learning  ⊃  Generative AI (foundation models, LLMs, diffusion)
```

**Types of machine learning:**

| Approach | Data | Business example |
|----------|------|------------------|
| **Supervised** | Labeled (input + correct answer) | Predict customer churn from past customers marked "churned / stayed" |
| **Unsupervised** | Unlabeled | Group customers into segments nobody defined in advance |
| **Reinforcement** | Rewards and penalties from an environment | Optimize warehouse robot routes or dynamic pricing through trial and feedback |

**The ML lifecycle and Google Cloud tools:**

| Stage | What happens | Google Cloud examples |
|-------|--------------|-----------------------|
| **Data ingestion & preparation** | Collect, clean, label and transform data | BigQuery, Cloud Storage, Dataflow, Dataproc |
| **Model training** | Train, tune or customize a model | Agent Platform (formerly Vertex AI) training, AutoML, Model Garden, tuning |
| **Model deployment** | Serve the model to applications | Agent Platform Endpoints / Inference, Cloud Run |
| **Model management** | Version, monitor and automate | Model Registry, Model Monitoring, Agent Platform Pipelines, Feature Store |

**Choosing a foundation model (business factors):**
- **Modality:** does the task need text, image, audio, video or a mix?
- **Context window:** how much information must the model consider at once (for example, long contracts)?
- **Performance vs. cost:** a larger model may be more capable but slower and more expensive.
- **Latency:** real-time chat needs fast responses, while overnight batch jobs do not.
- **Customization:** do you need fine-tuning, or will prompting and grounding be enough?
- **Security, privacy and compliance:** data residency, governance and enterprise controls.
- **Availability & reliability:** SLAs, regional availability and support.

**Gen AI use-case categories:**

| Category | Examples |
|----------|----------|
| **Create** | Marketing copy, product images, code, email drafts |
| **Summarize** | Meeting notes, long reports, support tickets, legal documents |
| **Discover** | Enterprise search, Q&A over internal documents, research insights |
| **Automate** | Agents that handle workflows: claims processing, onboarding, order status |

**Pitfalls / Gotchas:**
- Gen AI is a *subset* of ML, not a separate field.
- Foundation models are trained mostly on **unlabeled** data. Supervised fine-tuning comes later.
- The "best" model is the one that fits the business need and budget, not always the largest one.

**Exam Tips:**
- Scenario says "labeled historical outcomes" → **supervised**. "Find hidden groups" → **unsupervised**. "Reward/penalty" → **reinforcement**.
- If a question asks which factor matters most for analysing very long documents → **context window**.

---

## 1.2 Data Types in Gen AI

**Definition / Concept:**
A model can only be as good as its data. Leaders must judge whether the organization's data is ready for AI.

**Data quality:** accurate, complete, consistent, relevant and timely.
**Data accessibility:** available to the right systems and people, in a usable format, with the right permissions.

| Structured | Unstructured |
|------------|--------------|
| Fixed schema, rows and columns | No fixed format |
| SQL tables, spreadsheets, CRM records | Emails, PDFs, images, audio, video, chat logs |
| Easy to query and aggregate | Needs AI (NLP, vision) to extract meaning |

| Labeled | Unlabeled |
|---------|-----------|
| Each item tagged with the correct answer ("spam / not spam") | Raw data with no tags |
| Needed for supervised learning; costly and slow to create | Plentiful and cheap; used for pre-training and unsupervised learning |

**Business implications:**
- Most enterprise data (around 80% by common estimates) is **unstructured**, which is where gen AI adds the most new value.
- Poor-quality data leads to poor or biased outputs ("garbage in, garbage out").
- Data silos and missing permissions block AI projects more often than model choice does.
- Labeling costs time and money. Foundation models reduce how much labeled data you need.

**Pitfalls / Gotchas:**
- "More data" does not help if it is inaccurate, outdated or biased.
- Accessibility includes governance: data that is available but not permitted for use is not truly accessible.

**Exam Tips:**
- Customer reviews, call recordings and scanned contracts → **unstructured**.
- When a project is failing because of inconsistent or missing records, the fix is **data quality**, not a bigger model.

---

## 1.3 Gen AI Landscape Layers

**Definition / Concept:**
The gen AI stack is often described in five layers, from hardware at the bottom to the user experience at the top.

| Layer | What it is | Google Cloud examples | Business implication |
|-------|-----------|-----------------------|----------------------|
| **Application** | What end users interact with | Gemini app, Google Workspace with Gemini, Gemini Enterprise | Fastest time to value; least customization |
| **Agent** | Software that pursues a goal by reasoning and using tools | Gemini Enterprise agents, Agent Studio, Agent Development Kit (ADK) | Automates multi-step work, not just answers |
| **Platform** | APIs, data management, tooling and deployment to build and run AI | Gemini Enterprise Agent Platform (formerly Vertex AI) | Governance, security and MLOps in one place |
| **Model** | The trained models that generate content | Gemini, Gemma, Imagen, Veo, plus third-party and open models in Model Garden | Choice of capability, cost and openness |
| **Infrastructure** | Compute, storage and networking that train and serve models | TPUs, GPUs, AI Hypercomputer, Google's global network | Performance, scale and cost efficiency |

```
Application   ← users
Agent         ← goal-driven automation
Platform      ← build, govern, deploy
Model         ← Gemini, Gemma, Imagen, Veo …
Infrastructure← TPUs / GPUs / data centers
```

**Pitfalls / Gotchas:**
- An **agent** is not just a chatbot. It can plan, call tools and take actions.
- Choosing a higher layer (application) means less effort but less control. Lower layers mean more control but more effort.

**Exam Tips:**
- "Company wants employees productive *this week* with no development" → **application layer** (for example, Workspace with Gemini).
- "Company needs to build, tune and govern its own AI solutions" → **platform layer** (Agent Platform).

---

## 1.4 Google's Foundation Models

**Definition / Concept:**
Know what each Google model family is for and when you would pick it.

| Model | What it does | Typical use cases |
|-------|--------------|-------------------|
| **Gemini** | Google's flagship **multimodal** model family (text, code, images, audio, video), offered in sizes such as Pro, Flash and Nano | Chat assistants, document analysis, coding, reasoning, agents |
| **Gemini Nano** | Smallest Gemini, built to run **on device** | Offline or low-latency features on phones and edge devices |
| **Gemma** | Family of lightweight **open models** built from the same research as Gemini | Custom fine-tuning, local or on-premises deployment, cost-sensitive or data-sovereign workloads |
| **Imagen** | **Text-to-image** generation and editing | Marketing visuals, product mock-ups, creative assets |
| **Veo** | **Video generation** from text or image prompts | Ads, social content, storyboards, training videos |

**Pitfalls / Gotchas:**
- Gemma is **open** (you can download and run it yourself). Gemini is accessed as a managed service.
- Imagen = images, Veo = video. These are easy to swap under exam pressure.

**Exam Tips:**
- "Must run on our own hardware / customize model weights / limited budget" → **Gemma**.
- "Analyse a video plus its transcript and answer questions" → **Gemini** (multimodal).
- "Generate a short promotional clip" → **Veo**.

---

## Quick Check

1. A bank wants to flag fraudulent transactions using five years of transactions marked "fraud / legitimate." Which learning approach fits?
   <details><summary>Answer</summary>Supervised learning. The historical data is labeled.</details>
2. Which layer of the gen AI landscape provides TPUs and GPUs?
   <details><summary>Answer</summary>Infrastructure.</details>
3. A retailer needs a model it can fine-tune and host inside its own data center. Which Google model family fits best?
   <details><summary>Answer</summary>Gemma (open models).</details>
