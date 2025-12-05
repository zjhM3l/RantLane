# RantLane — Honked Yet?

[English](README.md) | [中文说明](README_zh-CN.md)

> A tongue-in-cheek CarPlay-friendly experiment for talking **around** other drivers, not **at** them.

RantLane started from a very specific moment:  
our friend did an *insane* highway cut-in near Austin, the car behind flashed lights and gave us the middle finger, and everyone in our car just burst out laughing.

On the way home we thought:

> “What if cars had a **push-to-talk, slightly cursed walkie-talkie**, with translation, achievements and cooldowns, so you can vent or compliment without actually rolling down the window?”

This repository is an attempt to turn that shower thought into a real app demo.

---

## What is this?

RantLane is an experimental, not-for-production project that aims to:

- Explore **location-based, low-latency voice chat** between nearby cars
- Learn how to build a **CarPlay-integrated communication app**
- Have some fun with **road-rage-but-make-it-safe** game mechanics  
  (cooldowns, “masochist” points, silly achievements, etc.)

Think of it as a hybrid of:

- A walkie-talkie for drivers and passengers  
- A tiny anonymous radio station around your car  
- A place to say “nice overtake” or “that lane change was… ambitious”

---

## Core ideas (work-in-progress)

Nothing here is final; this is a brainstorming list turned into a backlog.

### 1. Nearby Vehicle Voice Links

- Phone reports coarse location → server groups devices into **local “bubbles”**
- Each bubble behaves like a lightweight audio room:
  - Push-to-talk, short clips or low-latency streams
  - Option to stay **anonymous** (only a fun avatar / car emoji is shown)
- You can:
  - Join the default “Around Me” channel
  - Invite friends into a **team/convoy channel** when road-tripping

### 2. Opt-in “Open Intercom” Switch

- Big master switch: `Open Around-Me Intercom [ON/OFF]`
- If you turn it **off**, your car becomes invisible to random chatter
- If you turn it **on**, you accept:
  - Short, rate-limited voice snippets from nearby users
  - System-enforced cooldowns (you cannot spam 24/7)

### 3. Voice + Translation

Because not everyone speaks the same language:

- Incoming voice → speech-to-text → machine translation → TTS
- Goal: **English / Spanish / Chinese** first, more later
- So yes, you can technically “compliment in Mandarin” and have it read out in Spanish

### 4. “Dō-M Points” & Achievements

This is the joke/gamification layer:

- **Dō-M points** (working name):  
  - Gain points for *taking* feedback calmly (positive or negative)
  - Lose points if you rage too hard or get blocked by many users
- Achievements like:
  - `Chased but Praised` – followed someone only to say something nice  
  - `Zen Master` – received 10 salty comments, never replied
  - `Too Salty to Drive` – temporary mute for over-venting

All of this is meant to **reward de-escalation and humour**, not harassment.

### 5. “Pass It Forward” Chain

- If someone behind you sends a (polite) message like:  
  *“The guy ahead of you forgot his turn signal…”*  
- You can *optionally* forward a cleaned-up version further forward,
  so the original context is preserved without direct flaming.

This is more of a social experiment than a core feature.

---

## CarPlay & Safety

The long-term target is to ship a **CarPlay-enabled communication app** demo:

- Implemented using Apple’s **CarPlay + SiriKit / CallKit** patterns for communication apps
- UI focused on:
  - Large, template-driven components
  - Siri / voice control first
  - Minimal driver distraction

Because of safety and App Store review rules, the project will:

- **Not** encourage harassment or unsafe driving
- Provide:
  - Block / mute / report tools
  - Rate limiting & cooldowns
  - Optional passenger-only modes (e.g. limited when moving above X km/h)
- Be explicitly labelled as:
  > “For entertainment and experimentation.  
  > Do not use this app in any way that distracts you from driving.”

This is a playground to learn and prototype — not legal advice, not a production safety system.

---

## High-level tech stack (tentative)

This will likely evolve, but the rough plan is:

- **Client**
  - iOS (Swift / SwiftUI) with CarPlay support
  - Optional Android client later
- **Backend**
  - Realtime signalling: WebSocket / gRPC
  - Audio: WebRTC or a PTT-style streaming service
  - Storage for profiles, scores, basic logs
- **ML / speech**
  - Off-the-shelf cloud speech-to-text & translation
  - Lightweight profanity / toxicity filters

PRs with alternative architectures / stack ideas are very welcome.

---

## Project status

> **Status: Pre-alpha / in active design.**

Right now this repo is mostly:

- Brainstormed feature list
- Architecture sketches
- Early Swift prototypes and CarPlay experiments

Nothing is stable. Expect breaking changes every other commit.

---

## Contributing

This is a just-for-fun side project maintained in spare time by a few developers who:

- Like cars and road trips  
- Have strong opinions about terrible lane changes  
- Want an excuse to play with CarPlay, realtime audio and translation

If you:

- Enjoy building weird social experiments
- Know CarPlay / iOS / Android / WebRTC / backend realtime infra
- Or just want to bully TypeScript / Swift code into behaving

…feel free to:

1. ⭐ Star the repo  
2. Open an issue with ideas / concerns (especially about safety & abuse)  
3. Send a PR with:
   - docs
   - mockups
   - small features
   - test improvements

Please be respectful in issues and PRs.  
Ironically, this project is about dealing with road rage — not recreating it in GitHub comments.

---

## License

TBD. Most likely MIT once things are a bit more organized.

---

## Disclaimer

RantLane is **not** an official product of any automaker or platform.  
Use at your own risk. Always obey local traffic laws.  
If you are driving, **focus on the road first** — jokes come second.
