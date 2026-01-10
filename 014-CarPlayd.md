---
title: "AI‑Native Mileage Tracker — Hackathon Idea"
author: "Huan Li"
date: 2026-91-10
tags:
  - ai
  - agents
---

> **One‑line pitch**
> Mileage tracking for developers: invisible, battery‑safe, CarPlay‑triggered, API‑first, and AI‑classified.

---

## 0. Background Story & One-Liner

### Background Story (Founder / Problem-Driven)

I hate mileage apps.

They drain battery, track too much, and still ask me to classify every trip manually. Even after doing all that work, the data is rarely in a form that my systems—or future AI agents—can actually use.

This idea came from flipping the question:

> *What if mileage tracking behaved like infrastructure instead of paperwork?*

Instead of always-on GPS, we use explicit signals like CarPlay.
Instead of constant syncing, we upload only while charging on Wi-Fi.
Instead of manual labeling, we let AI guess first—and allow the user to correct it once with simple rules like “home” and “office.”

The result is mileage tracking that disappears.

**One-liner (Founder tone):**
*Mileage tracking that disappears—and just gives your systems the data.*

---

## 0.1 30-Second Elevator Pitch (Hackathon / Demo Style)

> This is a mileage tracker built backwards from constraints.
>
> It only records trips when CarPlay is connected, only uploads data while charging on Wi-Fi, and never asks users to manually classify trips unless they want to.
>
> AI handles business vs personal classification using simple user prompts like “home” and “office.”
>
> Developers get an API. Everyone gets clean exports.
>
> Free locally. $1/month for cloud and automation.

---

## 1. Core Insight (The Moat)

The moat is **not mileage tracking**.

The moat is:

* Explicit signals (CarPlay)
* Battery‑aware sync (charging + Wi‑Fi)
* Local‑first data ownership
* API‑first cloud
* AI‑assisted classification (optional, correctable)

This creates a product that is:

* Invisible
* Trustworthy
* Automatable
* Agent‑friendly

---

## 2. Target User (Very Explicit)

**Primary users**:

* Developers
* Solo founders
* Consultants
* Contractors
* Finance automation nerds
* AI agent builders

**Non‑targets**:

* Mass‑market drivers
* Gig drivers (Uber, delivery)
* People who want heavy UI or gamification

---

## 3. MVP Scope (Exact, Minimal)

### 3.1 iOS App (Local‑First)

**Recording rules**:

* Record trips **only when CarPlay is connected**
* Ignore walking / biking / transit
* Store trips locally by default

**Data captured per trip**:

* start_time
* end_time
* distance
* start_location (coarse)
* end_location (coarse)
* carplay_session_id
* inferred_category (business | personal)
* confidence_score

No continuous background GPS polling.

---

### 3.2 AI‑Assisted Classification (Key Feature)

**Goal**: eliminate manual categorization.

#### First‑pass AI guess

The app automatically guesses:

* Business vs Personal

Signals used:

* Time of day
* Day of week
* Location clusters
* Repeated routes
* CarPlay context

#### User‑provided correction prompt (lightweight)

Users can optionally define rules like:

```text
Home: 123 Main St
Office: 456 Market St

Trips between home and office on weekdays are business.
Trips starting or ending at grocery stores are personal.
Trips after 7pm are usually personal unless destination is office.
```

This prompt:

* Is stored locally
* Is fed to the classifier
* Improves future predictions

**User never labels every trip manually.**

---

### 3.3 Cloud Sync (Optional, Paid)

**Free tier**:

* Local‑only
* Manual export (CSV)

**Paid tier (~$1/month)**:

* Cloud sync
* API access
* Webhooks

**Upload conditions**:

* Device is charging
* On Wi‑Fi
* Background batch sync

Battery‑first by design.

---

## 4. API‑First Design (Developer Friendly)

### 4.1 Core API (v1)

```http
GET /v1/trips
GET /v1/trips?from=&to=
GET /v1/summary/monthly
POST /v1/rules
```

**Schema principles**:

* JSON only
* Versioned
* Idempotent
* Stable field names

### 4.2 Automation Targets

Out of the box:

* CSV export
* Webhook push

Future (non‑MVP):

* S3
* Google Drive
* GitHub repo

---

## 5. App Store Feasibility (Reality Check)

### ✅ Allowed / Feasible

* CarPlay detection
* Background tasks (conditional)
* Local‑first storage
* Optional cloud
* AI classification (on‑device or remote)

### ⚠️ Constraints

* Must clearly disclose location usage
* CarPlay cannot present complex UI
* Background execution must be conservative

### Verdict

**Fully App‑Store feasible** if:

* Tracking is explicit
* Battery use is conservative
* Privacy is clear

---

## 6. Privacy & Trust (Critical for Adoption)

Principles:

* Local‑first
* No forced account
* Cloud is optional
* User owns data
* No ads
* No selling telemetry

This is a *trust product*.

---

## 7. Freemium Model

| Tier  | Features                                      |
| ----- | --------------------------------------------- |
| Free  | Local tracking, AI classification, CSV export |
| $1/mo | Cloud sync, API access, webhooks              |

Low price → low friction → high retention.

---

## 8. Branding & Naming (Brainstorm)

### Naming principles

* Developer‑friendly
* Calm
* Infrastructure‑like
* Not cute

### Candidate names

**Signal‑oriented**

* DriveSignal
* TripSignal
* MileSignal

**Infrastructure‑style**

* Odom
* OdometerOS
* Tripd

**AI‑native**

* AutoLog
* DriveLog AI
* MileMind

**Opinionated / sharp**

* CarPlayd
* Telemetry
* RoadTrace

(Brand decision intentionally deferred.)

---

## 9. Why This Is a Good Hackathon Idea

* Small surface area
* Clear MVP
* Strong differentiation
* Developer‑aligned
* AI‑native
* Real personal pain solved

Also:

* Great demo
* Easy to explain
* Easy to extend

---

## 10. Status

📌 **Saved for future continuation**
📌 Not started
📌 Intentionally paused

Future‑me can resume this with any capable AI agent.

---

> *Design philosophy:*
> Invisible software > clever software
