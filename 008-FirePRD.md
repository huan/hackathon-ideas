---
title: FirePRD is an AI-powered documentation framework that transforms finished applications into clear, product-focused documentation.  
author: "Huan Li"
date: 2025-10-07
tags:
  - docs
  - prd
---

# 🔥 FirePRD — Hackathon Idea Memo

**Tagline:** *Ignite your product vision — automatic, human-centered PRD generation from real code.*

---

## 🚀 Overview

**FirePRD** is an **AI-powered documentation framework** that transforms *finished applications* into **clear, product-focused documentation**.  
Unlike traditional documentation tools that focus on technical details, FirePRD focuses on **product purpose, user experience, and storytelling** — automatically generating a **Product Requirements Document (PRD)** directly from your codebase.

**In short:** FirePRD helps teams *understand and communicate what their product *is*, not just how it works.*

---

## 💡 Problem

Most developers write docs that are:  
- Technical, low-level, and unreadable for designers or PMs  
- Written *before* the product is finalized, quickly outdated  
- Missing the *why*, *who*, and *what experience* parts of the story

**FirePRD flips that workflow:** it reads the *final shipped codebase* and creates living, product-centric documentation that reflects the *actual* product — from the user’s point of view.

---

## ✨ Solution

FirePRD analyzes the final codebase and UX components (routes, labels, structure, UI metadata) and auto-generates a **human-readable, product-first PRD skeleton** in a `docs/` folder.

It combines ideas from **Docs-as-Code** and **Code-as-Docs** to produce a living, version-controlled documentation system.

### Core Features
- **Docs-as-Code integration:** stores everything in your repo (`docs/` folder, Markdown, CI/CD).  
- **Hybrid PRD structure:**  
  - 2 layers by default: `Part/Chapter.md`  
  - Auto-splits large chapters (> 5 pages) into 3 layers: `Part/Chapter/Section.md`  
- **AI-driven narrative generation:** derives product purpose, user journey, and UX flow directly from the app code.  
- **Zero technical jargon:** focuses purely on product logic and user experience.  
- **Auto-generated metadata:** every chapter has a `meta.yaml` with title, status, related sections, and last update.  
- **SUMMARY.md + CrossRefs.md:** automatically managed by CLI to maintain structure and cross-links.  
- **Prompt-ready:** integrates seamlessly with Claude Code / Gemini CLI / Copilot prompts for iterative refinement.

---

## 🧠 Workflow

1. **Scan** the repo → FirePRD detects app features, UI routes, labels, and flows.  
2. **Generate** initial PRD outline → Parts (Vision, UX, Growth, etc.).  
3. **Apply split policy** → if a chapter exceeds ~5 pages, create sections.  
4. **Scaffold** folder structure + placeholder files with breadcrumbs and meta.  
5. **Iterate** using AI prompts to fill each section (Claude Code / Gemini CLI).  
6. **Publish** via Docs-as-Code pipelines (MkDocs, Docusaurus).

---

## 🎯 Example Output

```
docs/
 ├── SUMMARY.md
 ├── Part-I_Vision/
 │    ├── product-overview.md
 │    ├── problem-statement.md
 │    └── business-goals.md
 ├── Part-II_Experience/
 │    ├── design-principles.md
 │    ├── core-features/
 │    │    ├── 2.1_feature-dashboard.md
 │    │    ├── 2.2_feature-authentication.md
 │    │    └── meta.yaml
 ├── Part-III_Growth/
 │    ├── pricing-model.md
 │    ├── retention-loops.md
 │    └── feedback-channels.md
 └── Glossary.md
```

---

## 🧩 Tech & Tools

- **Language:** Python or TypeScript (CLI)  
- **AI models:** Claude Code, Gemini CLI, or OpenAI GPTs for structured generation  
- **Docs platform:** MkDocs Material / Docusaurus (Docs-as-Code compatible)  
- **Version control:** GitHub / GitLab for PR reviews and live previews  
- **Integration:** BMAD-METHOD or custom AI pipelines for product analysis  

---

## 🧠 Inspiration

- **Docs-as-Code** → treat docs like versioned software  
- **BMAD-METHOD** → multi-agent planning and documentation generation  
- **Literate Programming** → code tells the story of product logic  
- **Product Design Thinking** → document the *why* behind every feature  

---

## 🧰 Hackathon Deliverables

| Milestone | Deliverable |
|------------|-------------|
| **Day 1** | CLI prototype: scan repo → create hybrid PRD skeleton |
| **Day 2** | AI integration: generate section placeholders with product-centric summaries |
| **Day 3** | Demo site: live MkDocs or Docusaurus site showing FirePRD outputs |
| **Day 3+** | Optional BMAD integration & open-source release |

---

## 💬 Tagline Ideas

- *“Ignite your product vision.”*  
- *“From code to clarity.”*  
- *“Docs that feel, not just explain.”*  
- *“The human side of product documentation.”*  

---

## 🧭 Future Roadmap

- Integrate with **BMAD Foundry** as a “Docs Agent.”  
- Support **AI collaboration mode**: multiple LLMs draft and review PRD sections.  
- Add **FirePRD Cloud** for hosting and auto-sync.  
- Support **multilingual product documentation.**

---

## 💥 Why It’ll Win a Hackathon

- Novel twist on “Docs-as-Code”: focuses on *Code-as-Docs* from a **product perspective**.  
- Bridges the gap between developers, designers, and PMs.  
- Produces visually clear, AI-ready documentation that can scale.  
- Instant wow factor: “We generated a PRD from your repo — no setup needed.”  

---

## ❤️ Created by

**Huan Li (@huan)** — Founding Human & Architect @ PreAngel LLC  
Inspired by the BMAD-METHOD, Docs-as-Code philosophy, and the power of human-centered design.

## Credit

Huan Li <https://github.com/huan>
