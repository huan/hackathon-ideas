---
title: DocWhisper (ScribeFleet) — AI Sub‑Agent Docs Engine for Wechaty (Diátaxis × Docusaurus × Claude Code)
author: "Huan Li"
date: 2025-09-05
tags:
  - documentation
  - branding
---

## TL;DR

**One‑liner:**
**ScribeFleet** auto‑generates, tests, and continuously updates Diátaxis‑structured documentation for Wechaty using Claude Code sub‑agents and publishes it via Docusaurus—kept fresh by PRs on every code change.

**30‑second pitch:**
Docs rot. Contributors are blocked. Newcomers bounce. Wechaty (and most OSS projects) need docs that are accurate, approachable, and always current. **ScribeFleet** is an agent team that turns your codebase and issues into living documentation. Each sub‑agent owns a quadrant of Diátaxis (Tutorials, How‑to, Reference, Explanation). A CI pipeline extracts API facts from the code, writes Reference pages, drafts Tutorials/How‑tos, runs doctests on examples, builds a Docusaurus site, and opens PRs with previews. Humans approve; the fleet sails on. Ship an MVP for Wechaty in a weekend, then template it for every OSS that wants docs that don’t decay.

---

## Background & Motivation (Why This, Why Now)

* I’ve used the **Documentation System** (Diátaxis) before for Wechaty and love it—it helps me understand the whole picture and details. But our current docs still feel **incomplete, inconsistent, and hard to keep updated**.
* In 2021 we socialized the idea; **today’s AI coding agents** can actually execute it: they parse code, enforce styles, and run CI. We can finally **keep docs in sync with code** via automated PRs.
* Personal pain: I often feel **AI can generate better foundations** than humans, especially for large, evolving codebases. Humans then refine and approve. That’s exactly the loop I want.

---

## Problem Statement

* **Drift:** APIs evolve faster than docs; outdated pages mislead users.
* **Blend:** Tutorials, How‑tos, Reference, and Explanation get mixed, raising cognitive load for new readers.
* **Bus factor:** Only a few maintainers understand the architecture; knowledge isn’t codified.
* **Scale:** Multi‑language SDKs (JS/TS, Python, Go, Java, …) multiply the surface area.
* **Maintenance tax:** Humans can’t sustainably regenerate Reference and examples for every change.

**Impact on Wechaty:** Slower onboarding, more repeated questions, stalled contributions, and missed opportunities for growth.

---

## Solution Overview

**ScribeFleet** is a **repo‑native agent team** (Claude Code sub‑agents) that:

1. **Extracts Reference** from code (JSDoc/Type‑stubs/Annotations) → generates one page per public symbol.
2. **Drafts Tutorials/How‑tos** from common tasks and issues → runnable examples with checkpoints.
3. **Writes Explanations** (architecture, Puppets, design tradeoffs) → concept clarity.
4. **Builds and Previews** a Docusaurus site → PRs with screenshots and preview links.
5. **Watches for drift** (git diff on public surfaces) → auto‑opens update PRs.
6. **Enforces Diátaxis boundaries** via a doc linter → prevents style/type mixing.

**Results:** Accurate, approachable, and always‑current docs with human review in the loop.

---

## Product Branding: DocWhisper

### Brand Identity

**DocWhisper** represents a new era of intelligent documentation — one that *listens* to your code, *understands* your system, and *speaks* clearly to your users. It embodies empathy, structure, and fluency, turning complex technical systems into accessible human stories.

DocWhisper is not just a product; it's a **philosophy of communication** between machines and people — a quiet voice that ensures no idea gets lost in translation between engineers and the world.

**Brand Tagline:**  
> *"Your code's quiet storyteller."*

**Core Narrative:**  
> *"Your code speaks. DocWhisper listens."*

---

### Why "DocWhisper" Is the Perfect Name

| Attribute | Why It Fits Perfectly |
|-----------|----------------------|
| **Memorable** | The combination of *Doc* (familiar, utilitarian) and *Whisper* (emotional, soft) creates tension that's easy to remember. |
| **Humanistic** | Unlike industrial names (e.g., DocOps), *Whisper* gives warmth, calm, and subtlety — human qualities that build trust. |
| **AI-Native** | Whisper implies intelligence that listens and interprets context. It perfectly describes LLM-based systems that process code and produce documentation. |
| **Cross-Disciplinary** | Works across technical, creative, and educational markets — developers, technical writers, and startups alike. |
| **Evocative & Poetic** | Feels personal, almost sentient — the AI that *knows* your code and *tells* its story quietly but confidently. |
| **Brandable Globally** | Short, phonetic, pronounceable in most languages, with no negative connotations. |
| **Extensible** | Can easily expand into sub-products (e.g., *WhisperHub*, *WhisperAgent*, *WhisperSync*) or product tiers (*DocWhisper Pro*, *DocWhisper Cloud*). |

---

### Technical Code Name: ScribeFleet

While **DocWhisper** is the public brand, **ScribeFleet** serves as the technical implementation name:

* **ScribeFleet** evokes a **coordinated crew of writers** (sub‑agents) working in parallel.
* Signals **movement and continuity** (docs that sail forward with the code).
* Memorable, brandable, works beyond Wechaty.

**Alternates:** *QuadraScribe*, *DocFoundry*, *DocWeaver*, *DX‑Atlas*. (Keep **ScribeFleet** for technical MVP.)

**Relationship:** DocWhisper is the product brand; ScribeFleet is the underlying multi-agent orchestration engine.

---

### Brand Personality

DocWhisper's brand tone is **empathetic, intelligent, and trustworthy.** It should feel like a quiet expert — not flashy or corporate, but confident and clear.

| Trait | Description |
|-------|-------------|
| **Tone** | Calm, concise, encouraging — speaks with clarity, not noise. |
| **Voice** | First-person plural ("we") when guiding, second-person ("you") when empowering the user. |
| **Emotion** | Serene confidence — users should *feel safe* relying on the product. |
| **Aesthetic** | Minimalist, typographic, soft gradient tones; emphasis on whitespace and breathing room. |
| **Symbolism** | Sound waves, breath, or flowing lines — evoking communication and clarity. |

---

### Elevator Pitch

**30-second pitch:**  
Modern codebases evolve faster than humans can document them. DocWhisper is an AI-native documentation system that listens to your codebase, understands its patterns, and writes clear, human-quality documentation — automatically, continuously, and contextually.

It's your code's quiet storyteller.

**One-Liner:**  
**DocWhisper: Your code's quiet storyteller.**

---

### Product Positioning

**Market Category:**  
AI Developer Tools → Documentation Automation → "AI Docs-as-Code" Platform.

**Problem It Solves:**

* Documentation drift: code changes, docs don't.  
* Context overload: newcomers can't see the full picture.  
* Time sink: maintainers hate writing docs manually.  

**Solution:**  
DocWhisper uses AI agents to:

* Parse codebases (APIs, configs, commits)
* Generate Diátaxis-structured documentation (Tutorials, How-Tos, Reference, Explanations)
* Continuously update and open PRs in sync with the repo.

**Differentiation:**

| Feature | Competitors | DocWhisper Advantage |
|---------|-------------|---------------------|
| **LLM-driven doc generation** | Common | Whispering metaphor emphasizes *understanding tone & context*, not just output. |
| **Diátaxis-aligned structure** | Rare | Built-in structural discipline for clarity & maintainability. |
| **Multi-agent orchestration** | Emerging | Fleet model (Architect, Writer, Linter, Publisher) unique in AI-doc ecosystem. |
| **CI integration (Docs-as-Code)** | Standard | Seamless PR loop keeps humans in control. |

---

### Visual Identity

| Element | Recommendation |
|---------|---------------|
| **Logo** | Stylized wave or breath mark (soft gradient line pattern forming a "D"). Symbolizes clarity and subtle communication. |
| **Colors** | Calm neutrals + one accent: `#4B9CD3` (soft blue) or `#7C3AED` (violet whisper). Avoid loud reds/oranges. |
| **Typography** | Inter, Nunito Sans, or Söhne — approachable sans-serifs. Medium weights only. |
| **Imagery** | Abstract waves, flowing gradients, subtle noise textures. No mascots or hard shadows. |
| **UI Language** | Rounded corners, motion easing ("ease-in-out"), generous padding; evokes comfort and intelligence. |

---

### Voice & Copy Guidelines

**Voice Pillars:**

1. **Clarity Over Cleverness** — prioritize understanding over jargon.  
2. **Empathy Over Authority** — speak like a mentor, not a manual.  
3. **Whisper, Don't Shout** — tone should guide users calmly to insight.  

**Example Copy:**

| Context | Example |
|---------|---------|
| **Landing Hero** | "Your code speaks. DocWhisper listens." |
| **Feature Card** | "Generates docs that read like they were written by your team — because they are." |
| **CTA Button** | "Start Listening" or "Let's Whisper Together." |
| **Error Message** | "We didn't quite catch that — mind rephrasing?" |

---

### Ecosystem Alignment

DocWhisper fits elegantly within the **Ship.Fail** and **PreAngel** brand family:

* Shares the same conceptual DNA — *human + AI co‑creation*.  
* Extends the "ship fast, explain clearly" philosophy.  
* Works naturally alongside tools like *ReDoc*, *ScribeFleet*, and *ReKey*.

| Ecosystem Partner | Relationship |
|-------------------|--------------|
| **Ship.Fail** | Community & launchpad for hackathon ideas. |
| **ScribeFleet** | Underlying multi-agent orchestration engine powering DocWhisper. |
| **ReDoc** | Visualization and build pipeline component for publishing docs. |
| **PreAngel LLC** | Parent incubator brand; DocWhisper fits "AI-native SaaS for creators." |

---

### Future Extensions

| Sub-Brand | Description |
|-----------|-------------|
| **WhisperSync** | Keeps documentation synchronized across branches and versions. |
| **WhisperHub** | Collaborative cloud platform for doc review & agent feedback. |
| **WhisperCLI** | Local command-line interface for instant doc generation. |
| **WhisperStudio** | Visual interface for editing, comparing, and publishing docs. |

---

### Long-Term Vision

> **To make documentation self-sustaining and emotionally intelligent.**

DocWhisper will redefine how developers interact with knowledge — not as static text but as a living, adaptive conversation. It bridges the gap between **machine understanding** and **human communication**, one whisper at a time.

---

### Brand Keywords

**Core Keywords:** whisper, clarity, empathy, understanding, intelligence, storytelling, flow, structure, calm, evolution.

**Avoided Keywords:** automation, bot, generate, AI‑powered (overused, mechanical tone).

---

## Reader Experience Goals (Diátaxis)

* **Tutorials (learn):** “Happy path” lessons; one per stack (JS/TS → Python → Go → Java). Each step ends with “You should see…”.
* **How‑to guides (solve):** One small outcome per page (e.g., handle QR login, reconnect on error, use Puppet X).
* **Reference (know):** Factual pages per symbol (classes, functions, events). Generated from code. Cross‑links to How‑tos.
* **Explanation (understand):** Concepts and architecture (Wechaty core, Puppet abstraction, adapters, design tradeoffs).

**Rule:** Do not mix types. Linter enforces boundaries.

---

## Architecture (MVP)

```
repo-root/
  .claude/agents/                # Claude Code sub-agent definitions
    doc-architect.md
    reference-extractor.md
    tutorial-chef.md
    howto-writer.md
    explainer.md
    linter-stylekeeper.md
    publisher.md
    changelog-watcher.md
  docs/                          # Docusaurus content root
    tutorials/
    how-to/
    reference/
    explanation/
  website/                       # Docusaurus site (or /)
    docusaurus.config.js
    sidebars.js
  CLAUDE.md                      # House style & Diátaxis rules
  .github/workflows/docs.yml     # CI: generate, lint, build, open PR
```

**Data flows:**

1. Code & JSDoc → **Reference Extractor** → `docs/reference/*`
2. Git diff / Issues → **Doc Architect** → task backlog → **Tutorial Chef**/**How‑to Writer** → new/updated pages
3. **Explainer** generates architecture/concepts, links out to Tutorials/How‑tos/Reference
4. **Linter** validates style, headings, links, and doc‑type boundaries
5. **Publisher** builds Docusaurus, uploads preview, opens/updates PR
6. **Changelog Watcher** triggers edits on API surface changes

---

## Sub‑Agent Specs (contracts)

### 1) Doc Architect (planner)

* **Input:** Repo tree, package manifests, git diff, open issues with doc tags.
* **Output:** Backlog YAML (topic, quadrant, owner agent, acceptance criteria, cross‑links).
* **Rules:** No content writing; only planning and routing. Must tag Diátaxis quadrant.

### 2) Reference Extractor (facts only)

* **Input:** Source files + JSDoc/annotations + type info.
* **Output:** One page per public symbol (signature, params, returns, brief description, minimal example). Cross‑link related symbols.
* **Rules:** No opinions, no step‑by‑step. Fail if symbol unresolved. Add `@since`, `@deprecated` where applicable.

### 3) Tutorial Chef (happy path)

* **Input:** Backlog items tagged `tutorial`.
* **Output:** Lesson with goal → prerequisites → steps (each ends with an observable check) → next steps.
* **Rules:** Minimal runnable examples; prefer Codespaces/Docker for setup. Avoid API matrices.

### 4) How‑to Writer (recipes)

* **Input:** Backlog items tagged `how-to`.
* **Output:** Problem, prerequisites, numbered steps, verification, pitfalls, related links.
* **Rules:** One outcome per page. Link to Reference for API details.

### 5) Explainer (concepts)

* **Input:** Architecture notes, design docs, maintainers’ comments.
* **Output:** Concept overview, motivation, alternatives, tradeoffs, related links.
* **Rules:** No step lists or exhaustive APIs.

### 6) Linter / Stylekeeper

* **Input:** Changed docs.
* **Output:** CI annotations; block merge on violations.
* **Rules:** Enforce title case, headings order, front‑matter, link validity, code‑block fences/language tags, **quadrant purity** (regex heuristics).

### 7) Publisher

* **Input:** Built site artifacts.
* **Output:** PR with preview link + screenshots; comment with changed pages.
* **Rules:** Fail fast on build/link errors. Attach artifact.

### 8) Changelog Watcher

* **Input:** Git diff on public API / config / CLI.
* **Output:** Issues + draft PRs to update affected pages.
* **Rules:** Label by quadrant; auto‑assign reviewers.

---

## Prompting Strategy (repo‑native)

* \`\`\*\* (repo root):\*\* House style, glossary, link policy, code‑block conventions, Diátaxis hard rules.
* **Per‑agent prompts (**\`\`**):** Role‑specific system prompts with allowed tools & write paths.
* **CI **\`\`** (optional):** Non‑negotiables (e.g., “Reference pages must not include tutorials”).

**Doc type templates (fragments):**

* **Tutorial:** goal → prerequisites → steps (✔ expected result) → troubleshooting → next steps.
* **How‑to:** problem → prerequisites → steps → verification → pitfalls → related.
* **Reference:** name → signature → params → returns → example → see also.
* **Explanation:** what/why → motivations → alternatives → tradeoffs → links.

---

## Docusaurus Setup

* **Autogenerated sidebars** per folder: `tutorials/`, `how-to/`, `reference/`, `explanation/`.
* **Versioning** after MVP (v1 baseline → vNext branches).
* **Search**: start with default; later add hybrid BM25 + embeddings over docs and code symbols.
* **i18n**: Minimize at MVP; structure for future languages.

**Example **\`\`**:**

```js
module.exports = {
  docs: [
    { type: 'autogenerated', dirName: 'tutorials' },
    { type: 'autogenerated', dirName: 'how-to' },
    { type: 'autogenerated', dirName: 'reference' },
    { type: 'autogenerated', dirName: 'explanation' },
  ],
};
```

---

## CI/CD (GitHub Actions) — `docs.yml`

**Triggers:** `push`, `pull_request`, nightly cron.

**Jobs:**

1. **setup**: checkout, set up Node/PNPM, install deps.
2. **generate-reference**: run Reference Extractor; fail if unresolved symbols.
3. **generate-guides**: Doc Architect computes affected topics; create/update How‑to/Tutorial drafts.
4. **lint**: run Stylekeeper; link check; quadrant purity checks; markdown lint; spellcheck (allowlist for domain terms).
5. **doctest**: execute code blocks (where feasible) to validate examples.
6. **build**: Docusaurus build; upload artifact; capture screenshots.
7. **publish-preview**: comment on PR with preview URL; assign reviewers.
8. **watch-drift** (nightly): diff public surfaces; open/update PRs for drift fixes.

---

## MVP Scope (Hackathon weekend)

* Docusaurus skeleton + autogen sidebars.
* `.claude/agents/*` for 8 roles; `CLAUDE.md` house style.
* Reference generation for **Wechaty core** (Message, Contact, Room, Wechaty, events).
* 3 Tutorials: “Your first bot” (JS/TS), “Run on Docker”, “Run in Codespaces”.
* 5 How‑tos: QR login, reconnect, use Puppet X, webhooks, filter messages.
* 2 Explanations: architecture overview; Puppets & adapters.
* CI pipeline for generate → lint → build → preview PR.

**Deliverables:** PR to `wechaty/wechaty` (or a staging repo) with working site + preview. Screenshots + short demo video.

---

## Success Criteria (MVP)

* **Time‑to‑First‑Success** (TTFS) for a new user with the “first bot” tutorial ≤ **10 minutes**.
* **Reference coverage** for core symbols ≥ **80%**.
* **CI doctest pass rate** ≥ **95%** for runnable snippets.
* **Quadrant purity** linter passes at **100%** on main.
* **PR turnaround** (docs) reduced by **50%** vs. baseline.

---

## Risks & Mitigations

* **Hallucinations:** reference is **code‑sourced only**; fail CI on unresolved symbols; examples run in doctest.
* **Quadrant creep:** linter blocks mixed‑type pages (heuristics & keywo

## Credit

Huan Li <https://github.com/huan>
