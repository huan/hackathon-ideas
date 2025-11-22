---
title: "LLM Consensus Oracle / Truth Estimator"
author: "Huan Li"
date: 2025-11-21
tags:
  - deterministic
  - oracle
---

> Working title(s): **Consensus Oracle**, **Priorscope**, **Many Minds**
> Stack: **Next.js** (frontend + backend) + **Firebase Cloud** (hosting + optional persistence)

---

## 1. Origin Story & Motivation

### 1.1. The Chicken Joke Phenomenon

We started from a simple but deep observation about **deterministic decoding** in LLMs:

* When we set decoding to be **deterministic** (e.g., `temperature = 0`, `top_k = 1`), many different LLMs (GPT, Gemini, Claude Sonnet, LLaMA, etc.) will often answer the prompt:

  > "Tell me a joke."

  with the **same joke**:

  > *"Why did the chicken cross the road? To get to the other side."*

This suggests that across massive human training data, there exists a **dominant, universal, statistically highest-probability joke**. In other words, the LLMs have converged on a shared **cultural prior**.

### 1.2. From Joke to Truth Estimation

The key insight:

> If multiple independently-trained LLMs, under deterministic decoding, converge on the same answer, that answer is a strong candidate for a **shared prior** – a kind of **consensus signal** about how “the human internet” usually answers that question.

This is **not** a guarantee of objective truth, but it is:

* A **strong probabilistic signal** of what is widely believed, written, and reinforced.
* Potentially useful for **truth estimation**, hallucination detection, and understanding **where AI models agree or disagree**.

From here, we defined the goal:

> Build a tool that lets users ask short questions and see **how strongly different LLMs agree** under deterministic settings. High agreement ≈ strong shared prior; low agreement ≈ ambiguity, controversy, or underspecification.

We want to capture this idea as a **hackathon project**.

---

## 2. Concept Overview

### 2.1. One-line Pitch

> **"Ask a question. See what the models agree on."**
> A web app that queries multiple LLMs with deterministic decoding and computes a **consensus score** to visualize how strongly they agree on an answer.

### 2.2. What It Is (and Is Not)

**Is:**

* A **consensus / prior estimator** across multiple LLMs.
* A way to visualize **cross-model agreement** on short questions.
* A tool to explore the difference between **facts, norms, and opinions**.

**Is NOT:**

* A philosophical oracle of absolute Truth.
* A guarantee that consensus = correctness (models can agree on hallucinations).
* A replacement for human judgment.

We intentionally frame this as **“consensus / priors”**, not "the one true answer".

---

## 3. High-Level Product Design

### 3.1. User Flow

1. User visits the website.
2. Enters a **short question** (e.g. "What is the capital of France?", "Who wrote 1984?", "Tell me a joke.").
3. The app sends that question to multiple LLM providers, each with **deterministic decoding** settings.
4. The system collects their answers and computes a **consensus score**.
5. The UI displays:

   * Each model’s answer.
   * A **consensus meter** (0–100%).
   * A simple label: **Strong consensus / Partial consensus / Disagreement**.

### 3.2. Example UX Snapshot

* Input box at the top: `"Ask a short question..."`
* Button: **"Check Consensus"**
* Results area:

  * Cards for each model:

    * Model name (e.g., `gpt-4.1-mini`, `gemini-2.0-flash`, `claude-3.5-sonnet`).
    * Text of the answer.
    * Latency / timing (optional).
  * A large **consensus gauge** (progress bar or radial meter):

    * e.g., 95% → **Strong consensus** (green)
    * 75% → **Partial consensus** (yellow)
    * 45% → **Disagreement** (red)

---

## 4. Technical Design (Hackathon Scope)

### 4.1. Stack Choice

* **Framework**: Next.js (using both frontend & API routes / app router).
* **Hosting / Infra**: Firebase Cloud (Hosting + optional Firestore / Functions if needed).
* For hackathon simplicity, we can:

  * Use Next.js `app` directory and **server actions** or **API routes** for backend calls.
  * Deploy the Next.js app to Firebase Hosting with rewrites to the Next.js server.

We deliberately keep everything in the **Next.js world**, and treat Firebase as mostly a **deployment + optional database** layer.

### 4.2. Deterministic Model Calls

For each supported model, we will configure **deterministic decoding**:

* `temperature = 0`
* `top_p = 1`
* `top_k = 1` (or the provider’s closest equivalent)
* Disable any extra sampling options (if configurable).

Models to include (initially):

* **OpenAI**: e.g. `gpt-4.1-mini` or similar.
* **Google Gemini**: e.g. `gemini-2.0-flash` or `gemini-1.5-pro`.
* **Anthropic Claude**: e.g. `claude-3.5-sonnet`.

We can start with **2 models** (e.g. GPT + Gemini) for simplicity, and add Claude if time and API keys permit.

### 4.3. Agreement / Similarity Metric

**Baseline approach (hackathon-friendly):**

1. **Normalize** each answer:

   * Lowercase.
   * Strip punctuation.
   * Collapse whitespace.

2. **Exact string match**:

   * If all normalized answers are identical, set consensus score = 1.0 (100%).

3. If not identical, compute **semantic similarity**:

   * Get embeddings for each answer (using a single provider’s embedding API).
   * Compute pairwise cosine similarities between all model answers.
   * Average the pairwise similarities → a consensus score between 0 and 1.

4. Map consensus score to human-friendly labels:

   * ≥ 0.90 → **Strong consensus** (green)
   * 0.70–0.90 → **Partial consensus** (yellow)
   * < 0.70 → **Disagreement** (red)

This gives us a **quick, explainable metric** that’s good enough for a hackathon demo.

### 4.4. API Contract (Internal)

`POST /api/consensus`

Request body:

```json
{
  "question": "Who wrote 1984?"
}
```

Response body (example):

```json
{
  "question": "Who wrote 1984?",
  "models": [
    {
      "name": "gpt-4.1-mini",
      "provider": "openai",
      "answer": "1984 was written by George Orwell.",
      "latencyMs": 820
    },
    {
      "name": "gemini-2.0-flash",
      "provider": "google",
      "answer": "The novel '1984' was written by George Orwell.",
      "latencyMs": 610
    }
  ],
  "consensusScore": 0.97,
  "consensusLabel": "strong_consensus"
}
```

The UI can use this JSON to render the results.

### 4.5. Optional: Persistence

If time allows, we can store results:

* **Firestore** or SQLite-like store (if we run Next.js somewhere with a filesystem).
* Schema idea:

  * `questions` collection:

    * `id`
    * `question`
    * `createdAt`

  * `answers` collection (or subcollection):

    * `questionId`
    * `modelName`
    * `provider`
    * `answer`
    * `latencyMs`

  * `consensus` collection:

    * `questionId`
    * `consensusScore`
    * `consensusLabel`

This would enable a **public leaderboard** of interesting questions later.

---

## 5. Interpretations & Philosophy

### 5.1. Consensus vs Truth

We need to be explicit in messaging:

* **High consensus** means:

  * Multiple large, independently-trained LLMs, all using deterministic decoding, produced **very similar answers**.
  * There is likely a **strong shared prior** in human training data for that question.

* **Low consensus** means:

  * The question is ambiguous, controversial, or under-specified.
  * Different models, with different architectures and alignment strategies, diverge.

This is **probabilistic truth estimation**, not an ultimate arbiter of reality.

### 5.2. The "Global Maximum" Idea

The chicken joke example led to the idea:

> Some questions have a **global maximum** in LLM answer space – a single answer that dominates models trained on human text.

Our tool lets users explore:

* Which questions are like "Tell me a joke" (strong global maximum/consensus).
* Which questions produce **multiple local maxima** (opinions, norms, predictions).

This is interesting for:

* AI safety & alignment discussions.
* Epistemology (how AI models encode human beliefs).
* Product teams who want to detect hallucinations or unstable answers.

---

## 6. Hackathon Scope & Stretch Goals

### 6.1. MVP (Must-Haves)

* [ ] Next.js app with a **single input page**.
* [ ] `POST /api/consensus` endpoint.
* [ ] Integration with at least **2 LLM providers** with deterministic settings (e.g., GPT + Gemini).
* [ ] Simple **consensus scoring** based on embeddings.
* [ ] Visual **consensus meter** + model answers.

### 6.2. Nice-to-Have Features

* [ ] **Third LLM** (e.g., Claude Sonnet) for richer consensus.
* [ ] Basic **history list** (recent questions & consensus scores).
* [ ] Simple **leaderboard**:

  * “Strongest consensus questions”
  * “Most disagreement questions”
* [ ] **Explanatory summary**:

  * Use an LLM to generate a short paragraph:

    > "Here’s why the models agree/disagree on this question."

### 6.3. Stretch / Post-Hackathon Ideas

* [ ] User upvotes: allow humans to vote which answer seems most correct.

  * Compare **model consensus vs human consensus**.
* [ ] Tagging questions as **Fact / Opinion / Prediction / Value judgment** using an LLM.
* [ ] Public API (e.g. `/api/consensus?q=...`) for developers.
* [ ] Research mode: export data for analysis (e.g. CSV of questions + answers + scores).

---

## 7. Naming, Branding & Story

### 7.1. Possible Names

* **Consensus Oracle** – emphasizes agreement.
* **Priorscope** – like a “telescope for priors”.
* **Many Minds** – many models, one consensus.
* **Priors Meter** – more technical, focused on probabilities.

### 7.2. Taglines

* "Ask a question. See what the models agree on."
* "Visualize cross-model consensus for any question."
* "Where many AIs converge (or disagree)."
* "Explore the shared priors of the world’s largest language models."

### 7.3. Demo Story (for Judges)

1. Start with the **chicken joke story**:

   * Deterministic settings → multiple models → same classic joke.
   * This reveals a dominant cultural prior encoded across human data.

2. Then show the app:

   * Ask “Tell me a joke” → show consensus.
   * Ask a factual question → show strong consensus (e.g., "Capital of France").
   * Ask a controversial/predictive question → show disagreement.

3. Conclude:

   * This tool helps us see where AI models **strongly agree**, and where the world (and its data) is still **uncertain or divided**.

---

## 8. Open Questions & Future Directions

* How to systematically **evaluate** the correlation between consensus and factual correctness?
* How to handle **model updates** (new model versions changing priors)?
* How to communicate uncertainty responsibly so users don’t over-trust consensus?
* Could this be turned into:

  * A **research platform** for epistemology & AI safety?
  * An internal **hallucination detection** tool for companies?
  * A **teaching tool** about how LLMs learn from human data?

---

## 9. Quick Recap of Key Insights from the Conversation

* Deterministic decoding (`temperature = 0`, `top_k = 1`) pushes LLMs to their **highest-probability answers**.
* Across multiple frontier models, some prompts (like "Tell me a joke") lead to **the same answer**, indicating a **shared global maximum**.
* This suggests we can approximate **shared human priors** by:

  * Querying multiple models deterministically.
  * Measuring how similar their answers are.
* A hackathon-scale product can:

  * Provide a clean UI for asking questions.
  * Call multiple LLMs with deterministic settings.
  * Compute and visualize **consensus**.
* The result is a **Consensus / Prior Estimator** — a step toward practical **truth estimation tools** without over-claiming philosophical certainty.

---

*End of memo – this document is the canonical reference for the “LLM Consensus Oracle / Truth Estimator” hackathon idea, its story, and its initial design.*
 
