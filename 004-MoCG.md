---
title: "MoCG - Mother of Card Game"
author: "Huan Li"
date: 2025-09-02
tags:
  - game
---

**MoCG (Mother of Card Game)**: *The Jackbox + GitHub for card games, where AI turns your friend list into a hilarious, fully playable deck in seconds.*

---

## 🚀 30-second Elevator Pitch

Imagine you’re at a party, a team offsite, or even a flight. You upload a list of names—your classmates, coworkers, or fellow travelers. In under a minute, MoCG’s AI transforms that list into a customized card game. Each person becomes a card with funny, unique abilities inspired by their background. Share the link, and everyone joins instantly from their phone. It’s like UNO, but personalized—every game is different, and every laugh is shared. Create, play, and discover endless AI-generated party games with your friends.

---

## 💡 Original Idea

The original seed was simple: *Can we make a card game that adapts to any group of people, instantly?* Instead of a fixed deck, we thought: what if a game could be built dynamically from the players themselves? Like a “UNO generator” powered by AI, where each participant’s background feeds into the mechanics.

---

## 🔄 Idea Evolution

* **Step 1: UNO Inspiration** → We wanted an easy-to-learn format. UNO’s colored-number cards and action cards (skip, reverse, draw) are universally familiar and intuitive.
* **Step 2: Personalization via Lists** → We realized most social settings have a ready-made roster: LinkedIn profiles for corporate events, class rosters for reunions, or flight manifests for spontaneous play. Importing these lists makes setup frictionless.
* **Step 3: AI-Generated Flavor** → Instead of generic action cards, special cards are generated from real traits (e.g., “The Architect’s Code Review = skip 1,” “The Growth Hacker’s Viral Move = draw 2”). This injects humor and personal context.
* **Step 4: From One-off Game to Platform** → Not just a single game instance, but a system where every user can create, share, and replay games. Over time, MoCG grows into a discoverable ecosystem of community-generated games.
* **Step 5: MVP Boundaries** → To hit hackathon speed, we kept the scope lean: Web-only, Firebase backend, max 8 players, 30s per move, winner = first to play all cards.

---

## 🎯 Final Idea (Hackathon MVP)

### Core Concept

MoCG is an **AI-powered party card game generator**. Upload a list of people → AI generates a playable UNO-style game → Friends join and play online.

### Key Features

* **2–8 players** per game.
* **Game roles**: Host (start/kick), Players, Guests (join, rename), Spectators (watch + send chat/danmaku).
* **Deck setup**: Standard colored-number cards + AI-generated special cards.
* **Turn mechanics**: UNO rules with AI-injected humor; 30s timer per move, auto-play on timeout.
* **Victory**: First to empty their hand wins.
* **Sharing**: Clean GitHub-style link (`/u/{username}/{game}`) to invite friends instantly.
* **Discoverability**: A simple list of created games to explore.

### Tech Stack

* **Frontend**: Next.js + Tailwind.
* **Backend**: Firebase (Firestore, Functions, Realtime DB, Auth, Storage).
* **AI**: Gemini (card text/logic), nano/bunana (images).

### Why It Works

* **Instant fun**: No learning curve—everyone knows UNO.
* **Endlessly fresh**: Each group generates unique cards.
* **Viral by design**: Shareable links make every game easy to spread.
* **Scalable vision**: From MVP party mode → full GitHub-style card game ecosystem.

---

## ✅ Hackathon Goals

* Deliver a functional MVP where **2–3 people can play through a game in <10 minutes**.
* Generate at least **one funny, personalized special card per player**.
* Demo flow: Import names → AI generates → Start game → Show gameplay → Share link.

---

## 📌 Notes for Team

* Focus on **fun factor first**, polish later.
* Ensure AI outputs are **safe + humorous**, not offensive.
* Keep the Firebase schema flexible for fast iteration.
* Timebox: prioritize **game loop completion** over extra features.

---

> MoCG is about turning *any group of people* into *the heroes of their own hilarious party game*. That’s the magic we want to show at the hackathon.

## Credit

Huan Li <https://github.com/huan>
