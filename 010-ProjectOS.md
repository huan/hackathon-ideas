---
title: "ProjectOS – Minimal Git-Only Specification"
author: "Huan Li (et al.)"
date: 2025-10-12
version: "v0.1-draft"
tags:
  - git
  - multiverse
  - version-control
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
