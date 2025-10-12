---
title: "EvoPM – Minimal Git-Only Specification"
author: "Huan Li (et al.)"
date: 2025-10-12
version: "v0.1-draft"
tags:
  - git
  - multiverse
  - version-control
---

# 🧬 EvoPM — Evolutionary Project Management

## 🌟 One-liner
> **“Projects evolve, not just progress.”**

## 🧠 Concept Summary

**EvoPM** is an **AI-native project management philosophy and framework** that treats every project not as a linear plan, but as a living, branching organism that evolves with each decision.  
It merges **Agile iteration**, **Stage-Gate discipline**, and **Git-style branching** into a unified model:  
> **Evolutionary Project Management.**

---

## ⚙️ Core Meaning
| Element | Meaning |
|----------|----------|
| **Evo** | Evolution, adaptability, emergence, intelligence |
| **PM** | Project Management — or “Process Mind” / “Parallel Multiverse” (depending on tone) |

**Together:** EvoPM = *intelligent, versioned, adaptive project management.*


## 🌌 Taglines
- “Where project management meets evolution.”  
- “Version your decisions. Evolve your outcomes.”  
- “Manage projects like Git — evolve, don’t overwrite.”  
- “From static plans to adaptive realities.”  
- “Evolutionary Project Management for the AI era.”

> **EvoPM** acts as the *managerial layer* orchestrating all others into a coherent ProjectOS ecosystem.

## 🧭 Future Extensions
- **EvoPM Studio** — visual Git-based PM dashboard  
- **EvoPM Protocol** — open spec for multi-agent coordination  
- **EvoPM Agents** — autonomous PM bots trained on PreAngel workflows  
- **EvoPM Manifesto** — open-source philosophy bridging Agile, Stage-Gate, and GitOps

---

## 🧬 Personality Archetype
> **The Adaptive Architect** — observant, calm, evolving, and always learning.

EvoPM doesn’t command; it orchestrates.  
It evolves projects the same way nature evolves life — one branching decision at a time.

## One-liner Introduction

**ProjectOS** — a radical simplification of project management: using only Git branches to model parallel universes of project evolution, where each version is a complete, immutable world of decisions and deliverables.

## 30-Second Elevator Pitch

ProjectOS reimagines how we manage complex, iterative projects by treating every change or feedback cycle as a new **universe**—a branch in Git. Instead of messy merges, conflicting revisions, or hidden metadata, ProjectOS uses the tools every developer already understands: **branches, commits, and fast-forwards**. Each branch (`v1`, `v2`, `v3`...) is a self-contained project timeline; `main` is simply the pointer to the current reality. This model makes project history **immutable**, **transparent**, and **easy to navigate**, while keeping governance and decision-making outside the repo—handled by people or AI agents. The result is the simplest possible multiverse for human–AI collaboration in product development.

## Executive Summary

**ProjectOS** is a minimalist framework for representing and managing project evolution using only native Git mechanics. It introduces a conceptual layer where each branch is treated as a **universe**—a complete snapshot of the project’s state and direction. When feedback or new decisions arise (a "Gate Open" event), a new universe is created from any previous commit, instantly becoming the active one via fast-forwarding `main`. There are no merges, no tags, and no additional metadata: the project’s multiverse lives entirely through standard branches (`v1`, `v2`, `v3`, ...). This design achieves maximal clarity, immutability, and extensibility with minimal operational overhead. All change propagation, reasoning, and decision management remain outside the repo, allowing for flexible integration with human and AI governance tools.

---

# ProjectOS — Minimal Git-Only Specification (Occam Edition)

## Overview

**ProjectOS** defines a minimal, Git-native way to represent and manage **multi-universe project evolution** using only standard Git primitives — branches, commits, and the `main` pointer. It intentionally avoids metadata, automations, or non-Git mechanisms.

The goal: use the simplest possible Git model to describe how projects evolve across multiple versions ("universes") while remaining traceable, immutable, and human-readable.

## Core Principles

1. **Occam’s Razor** — everything unnecessary is removed.
2. **Universes = Branches** — each project evolution is represented by a new Git branch (`v1`, `v2`, ...).
3. **Active Universe = **`` — `main` always points to the latest universe.
4. **No Merges Between Universes** — every universe is an independent immutable timeline.
5. **Immutability** — previous universes (`v1`, `v2`, ...) are preserved forever for historical review.
6. **Human or AI agents handle all change propagation** — Git only stores structural states, not decisions or dependencies.

## Key Concepts

| Concept                | Definition                                                                                                    |
| ---------------------- | ------------------------------------------------------------------------------------------------------------- |
| **Universe**           | A distinct branch (`v1`, `v2`, `v3`, …) representing one full version of the project DAG.                     |
| **Main**               | Fast-forward pointer to the currently active universe.                                                        |
| **Gate**               | Conceptual checkpoint where feedback or revision may fork a new universe. No Git artifact.                    |
| **Gate Open**          | Creation of a new branch (`vN+1`) from any existing commit or branch. `main` fast-forwards to it immediately. |
| **Gate Close**         | Implicitly occurs once work in that universe stabilizes. No explicit Git operation.                           |
| **Change Propagation** | Handled outside Git by agents or humans. Git only tracks resulting universes.                                 |
| **Rollback / Reopen**  | Creating a new universe (`vM+1`) from any past commit.                                                        |

## Operations

### 1. Gate Open

Fork a new universe from any commit or branch.

```bash
git branch v{N+1} <base_ref>
git checkout main
git merge --ff-only v{N+1}
```

**Result:**

- A new branch `v{N+1}` represents a new project universe.
- `main` now points to this universe immediately.

### 2. Work

Make commits on `v{N+1}` as usual. There are no restrictions beyond standard Git practice.

### 3. Gate Close

No Git action is needed. By convention, when work stabilizes in `v{N+1}`, the gate is considered closed.

### 4. Reopen / Rollback

If revision of a past universe is required:

```bash
git branch v{M+1} <old_commit_hash>
git checkout main
git merge --ff-only v{M+1}
```

This creates a new universe from any previous commit and sets it as the new active one.

## Rules

- Universes are **immutable** and **never merged**.
- `main` **always fast-forwards** to the newest open universe.
- Older universes (`v1`, `v2`, ...) are permanent historical states.
- Branch names are the only form of version numbering.
- All governance (feedback, review, rationale) lives **outside Git** (Issues, discussions, documentation, etc.).

## Minimal Traceability (Optional, Git-Native)

- **Branch Naming Convention:** `v7`, or optionally `v7-ux-revision` for clarity.
- **First Commit Message:** include the base commit hash or reason for fork.
- **Commit trailers (optional):**
  ```
  Gate: UX-001
  Universe: v7
  Base: 14f2ab1
  Agent: Pandora-AI
  ```

These optional fields help trace forks without external metadata.

## Example Lifecycle

### 1️⃣ Initial Project

```bash
git branch v1
# main -> v1
```

### 2️⃣ First Gate Open (Feedback from review)

```bash
git branch v2 main
git checkout main
git merge --ff-only v2
```

### 3️⃣ Continue Work in v2

```bash
git checkout v2
# ... commits ...
```

### 4️⃣ Reopen Past Gate (Fork from v1 commit)

```bash
git branch v3 v1~3
git checkout main
git merge --ff-only v3
```

Result:

- `v1`, `v2`, `v3` coexist.
- `main` points to `v3`.
- No merges, tags, or metadata.

## Advantages

✅ **Simple:** only uses standard Git. ✅ **Immutable History:** previous universes are preserved. ✅ **Traceable:** branches clearly represent evolution. ✅ **Compatible:** works with GitHub, GitLab, etc., without plugins. ✅ **Philosophically Clean:** separates product content (inside repo) from meta-governance (outside repo).

## Limitations

⚠️ No built-in change-propagation mechanism (human/AI agents handle it). ⚠️ No automation or CI logic (to preserve purity and simplicity). ⚠️ Governance relies on social/organizational conventions (Issues, review logs, etc.).

---

# Appendix — Design Rationale & Conceptual Background

## A. Why Minimal?

Earlier designs included custom refs, tags, and notes to track gates and metadata. These were powerful but complex. Following **Occam’s Razor**, we removed every element not absolutely required to express universes and transitions.

- Removed: `refs/universes/`, `refs/tags/gates/`, `git notes`.
- Removed: Automation workflows and structured metadata files.
- Kept: only `main` + `vN` branches.

## B. Philosophical Model — “Project as Multiverse”

Each branch (`vN`) is a self-contained **universe** representing one consistent state of the project. When a “Gate” (review point) reopens, a new universe forks — just like a new timeline in a multiverse.

- **Forks** represent design or decision divergence.
- **Universes** evolve independently.
- `` represents the timeline we’re currently living in.

Git becomes the multiverse database.

## C. Why Fast-Forward `main` Immediately?

This eliminates the distinction between “current” and “future” branches. As soon as a new universe is created, we exist within it. This makes mental modeling simpler: there is no staging period between proposal and active evolution.

## D. Why No Merges?

Merging creates conflicts and hybrid histories, contradicting the multiverse model. Each universe must remain a pure timeline of its own evolution.

## E. Why Keep Change Propagation Out of Git?

Because change propagation (deciding what to revise and how) is a human/AI process, not a data structure problem. Git is best used as immutable storage of results — not as a dynamic dependency engine.

## F. Relation to Previous Research & Concepts

- **Stage-Gate Model** → Gates correspond to universe forks.
- **Agile / Scrum** → Sprints happen *within* universes.
- **Digital Twin / MBSE** → Each universe = one consistent system configuration.
- **Git / Immutable DAG** → Perfect substrate for multiverse history.
- **EvoPM (Evolutionary Project Management)** → ProjectOS is its minimal, practical incarnation.

## G. Naming Philosophy

We dropped decorative prefixes like `universes/` and `refs/…` because Git’s native `vN` branches already express the versioning concept clearly and ergonomically. Simple names = simple understanding.

## H. The BMAD Method Integration

When applied to BMAD (Brainstorm → Make → Analyze → Decide):

- Each phase can trigger a Gate (new universe) if decisions change.
- Each universe records one full cycle of BMAD.
- Forking from earlier BMAD decisions naturally creates a new universe (`vN`).

## I. Future Extensions (Optional for Hackathon)

If future complexity is needed, extensions can be layered *without* breaking the core model:

- **GitHub Issues** to document gates.
- **GitHub Actions** to automate branch creation.
- **Graph visualizer** to show universe lineage (`git log --graph`).
- **AI Agent Integration:** Each node (commit/agent) could emit structured metadata externally.

## J. Summary of Simplified Design

| Concept            | Purpose              | Git Representation                           |
| ------------------ | -------------------- | -------------------------------------------- |
| Universe           | Versioned timeline   | Branch `vN`                                  |
| Current Universe   | Active branch        | `main` (fast-forward pointer)                |
| Gate Open          | New revision fork    | `git branch vN+1 <base>` + `merge --ff-only` |
| Gate Close         | End of work          | No-op                                        |
| Rollback / Reopen  | Fork from old commit | `git branch vM+1 <old_commit>`               |
| Change Propagation | Out-of-band          | Human/AI driven                              |

---

# ✅ Conclusion

**ProjectOS (Occam Edition)** defines the simplest possible framework to represent project evolution as a multiverse using only Git branches. It is:

- **Clean** (no metadata pollution)
- **Traceable** (via branches)
- **Immutable** (no merges)
- **Extensible** (compatible with external governance)

This specification can serve as the foundation for future hackathon development — from manual experiments to fully agentic, AI-assisted evolutionary project systems.

---

**Purpose:** Define a lightweight, Git-native convention for representing multi-universe project evolution using nothing more than standard Git branches and fast-forward operations.

---

## 1. Scope

ProjectOS formalizes how projects fork and evolve as universes (v1, v2, …) without introducing extra refs, tags, or metadata.
It treats Git as a temporal-multiverse ledger: every universe is a branch; the active universe is tracked by main.

---

## 2. Concepts & Terminology

| Term | Definition |
|------|------------|
| Universe | A self-consistent project timeline represented by a Git branch named vN (v1, v2, …). |
| Active Universe | The branch currently "lived in"; symbolized by main, which always fast-forwards to the newest universe. |
| Gate | A conceptual decision point whose reopening triggers the creation of a new universe. Not stored in Git; it exists as a human or agent event. |
| Gate Open | The act of forking a new universe from any commit (git branch v{N+1} <base>). |
| Gate Close | Conventionally achieved once work in that universe is complete. No Git action required. |
| Rollback / Re-evolution | Forking a new universe from an earlier commit to explore an alternate history. |
| Immutable Universes | Once a universe branch is created, it is never force-pushed, rebased, or merged. |
| Fast-Forward Pointer | main moves only via --ff-only merges to point to the currently active universe. |

---

## 3. Repository Layout

```text
main         → active universe (fast-forward pointer)
v1, v2, ...  → immutable universe branches
```

No other refs, tags, or notes are introduced.
All standard Git tools remain compatible.

---

## 4. State Machine

```text
        ┌──────────────┐
        │   GateOpen   │
        └──────┬───────┘
               │ creates new vN
               ▼
        ┌──────────────┐
        │ Work(commits)│
        └──────┬───────┘
               │ optional GateClose (no-op)
               ▼
        ┌──────────────┐
        │ Next GateOpen│  ← fork from any past or current commit
        └──────────────┘
```

---

## 5. Operations / Procedures

### 5.1 Initialize ProjectOS

```bash
git init
git checkout -b v1
git branch -f main v1
```

### 5.2 GateOpen (base_ref)

Create a new universe and immediately make it active.

```bash
git branch v$((N+1)) <base_ref>
git checkout main
git merge --ff-only v$((N+1))
```

### 5.3 Commit Work (in universe)

```bash
git checkout v$((N+1))
# edit files
git add .
git commit -m "feat: implement feature X [v$((N+1))]"
```

### 5.4 GateClose

No special command.
Completion is defined by convention when the required commits are done.

### 5.5 Rollback / Re-evolution

Fork a new universe from any earlier commit.

```bash
git branch v$((M+1)) <old_commit_hash>
git checkout main
git merge --ff-only v$((M+1))
```

---

## 6. Rules of Discipline

1. **No merges between universe branches.**
   Each branch is an immutable history.

2. **Fast-forward only for main.**
   main never diverges; it always represents the current universe.

3. **Never delete or rebase v* branches.**
   They are immutable audit records.

4. **All discussions, feedback, and propagation occur outside the repo**
   (issues, wikis, agents, humans). Git remains pure history.

5. **Branch naming: v1, v2, v3, …** (optional suffixes like v3-ux allowed).

6. First commit in each universe may optionally reference its base commit hash for human traceability.

---

## 7. Minimal Traceability (Recommended Conventions)

* **Branch Name** encodes universe identity (v7 or v7-title).
* **Commit Message** may include trailers:

```text
Universe: v7
Base: 7a3c4f9
Description: Re-evolve from UX gate
```

* **External Tracking** (Issues, etc.) may refer to branches by name; no coupling to Git internals required.

---

## 8. Example Timeline

```text
main → v1  (initial)
GateOpen → v2 (from v1)
  commits → v2 timeline
GateOpen → v3 (from v2)
  commits → v3 timeline
GateOpen → v4 (from commit on v2)
  commits → v4 (parallel universe)

v1 ────────●───────────────┐
            \              \
v2           ●──────────────●─────▶
              \              \
v3              ●────────────●────▶ (main)
v4               ●──────▶  (alternate)
```

---

## 9. Persistence and Archival

* Every universe branch is retained indefinitely.
* main indicates which one is current.
* Backups can be done with standard git clone --mirror; no special tooling required.

---

## 10. Philosophical Principles

| Principle | Interpretation |
|-----------|----------------|
| Occam's Razor | Nothing beyond native Git needed. |
| Immutability | Universes are never rewritten. |
| Transparency | Git history = truth; all else is commentary. |
| Separation of Concerns | Universe mechanics in Git; reasoning & propagation outside. |
| Composability | Works with any Git host (local, GitHub, GitLab, etc.). |
| Extensibility | Agents or tools may later automate GateOpen/Close via Issues or CI, but this spec imposes none. |

---

## 11. Reference Implementation Checklist

| Element | Mandatory | Description |
|---------|-----------|-------------|
| Branch naming vN | ✓ | Represents universe version |
| main fast-forward pointer | ✓ | Indicates current universe |
| No merges between universes | ✓ | Ensures immutability |
| External tracking of gates | optional | Issues, notes, etc. |
| Commit trailers for traceability | optional | Human-readable history aid |

---

## 12. Future Extensions (out of scope for v0.1)

* Formal event schema (GateOpen, GateClose) in structured logs.
* Visualization tools for universe graphs.
* Integration with BMAD-method agent frameworks.
* Automated CPG (Change Propagation Graph) analysis.

---

## End of Specification

ProjectOS v0.1 (Minimal Git-Only)
