# Rhythm

**Hearing Her Biology, Protecting Her Energy**

Rhythm is a personal AI system that learns a woman's biological baseline — HRV, resting heart rate, sleep, and menstrual cycle phase — and detects compound physiological drift *days before* exhaustion becomes unavoidable. It turns wearable data into one clear, actionable, cycle-aware insight each morning.

> It began with a personal observation: high-performing women around us were burning out, not from weakness or failure, but because the tools they relied on were never built for their biology.

---

## Table of Contents

- [The Problem](#the-problem)
- [Who Rhythm Is For](#who-rhythm-is-for)
- [What Rhythm Provides](#what-rhythm-provides)
- [How Rhythm Is Different](#how-rhythm-is-different)
- [System Architecture](#system-architecture)
- [Why AI, and Why This Pair](#why-ai-and-why-this-pair)
- [Responsible AI, Built In](#responsible-ai-built-in-not-bolted-on)
- [Risk & Trust Model](#risk--trust-model)
- [App Demo](#app-demo)
- [Future Plan](#future-plan)
- [Sources](#sources)

---

## The Problem

**The problem is measurable — the solution is already on her wrist.**

- **The Burnout Gap** — Women burn out far more than men: in 2024, 59% of women reported burnout vs. 46% of men.
- **Physical Cost** — Chronic burnout increases risk for heart, immune, sleep, and fertility problems.
- **Economic Cost** — Burnout costs the economy hundreds of billions and drives most stress-related sick leave.
- **The Biology** — Normal hormonal cycles change HRV and cognition — context that most apps ignore entirely.
- **Market Signal** — Femtech is already a $60B market with strong adoption among wearable users and clear growth potential.

The data already exists on millions of wrists. What's missing is an intelligence layer that interprets it through the lens of female biology.

## Who Rhythm Is For

**Ambitious, self-aware, already tracking health** — but the data she generates (heart rate, sleep, menstrual cycle) doesn't translate into timely, cycle-aware guidance. She wants to perform without burning out.

**Our Vision:** Rhythm is an AI system that learns each woman's biological patterns, detects emotional drift before she feels it, and helps her prepare for stress and burnout before they happen.

> You have always had a rhythm. We're here to help you find it.

## What Rhythm Provides

| Pillar | Description |
|---|---|
| **Prediction** | Rhythm detects compound drift across HRV, RHR, and sleep patterns 2–3 days before exhaustion becomes unavoidable, giving time to act. |
| **Prevention** | Predictions become one specific, low-effort suggestion — a gentle nudge, not a directive — that preserves the user's agency and reduces decision friction. |
| **Personalization** | The model learns an individual's baseline and distinguishes normal cycle-driven changes from genuine drift, improving accuracy the longer a user engages. |

We don't ask women to optimize or push harder. We help them meet life's demands while staying aligned with their biology.

## How Rhythm Is Different

| Product | Strength | Gap |
|---|---|---|
| **Apple Health** | Strong data collection | Lacks cycle-aware interpretation and per-user drift detection |
| **Oura / WHOOP** | Excellent biometrics | Limited cycle context, no consumer-grade predictive intelligence for female biology |
| **Flo / Clue** | Strong cycle-tracking behavior products | No integrated biometric drift detection or personalized baseline learning |
| **Rhythm** | Cycle-aware interpretation + personal baseline model + drift detection + humanized morning language that improves over time | — |

**Summary:** The data exists — the missing piece is an intelligence layer that reads biometrics through the lens of female biology and personalizes over time. That layer is Rhythm.

## System Architecture

Rhythm is built as three stacked models, fed by wearable and calendar inputs:

```
Watch / Calendar Input
        |
        v
+----------------------------+
| Model 1: Check-in          |
| Conversation [LLM based]   |
| Users' text/voice ->       |
| led by GPT/Claude          |
| Aim: collect user data     |
| Output: structured         |
| check-in data              |
+-------------+--------------+
              v
+----------------------------+
| Model 2: Prediction Model  |
| [Base model: XGBoost]      |
| Output: HRV data           |
| prediction (tiredness,     |
| pressure, mood, social     |
| engagement)                |
+-------------+--------------+
              v
+----------------------------+
| Model 3: Explain /         |
| Anticipate / Prepare       |
| [LLM based]                |
| Input: Model 2's forecast  |
| & raw data abstract        |
| Output: NLP explanations,  |
| predictions, suggestions   |
+-------------+--------------+
              |
     (feedback loop refines
      context back to Model 1)
```

- **Model 1 — Check-in Conversation (LLM-based):** Collects structured check-in data from user text/voice, led by GPT/Claude.
- **Model 2 — Prediction Model (XGBoost):** Predicts HRV-related outcomes — tiredness, pressure, mood, social engagement.
- **Model 3 — Explain / Anticipate / Prepare (LLM-based):** Turns Model 2's forecast and raw data into natural-language explanations, predictions, and suggestions.

A feedback loop carries context from Model 3 back to Model 1, refining future check-ins.

## Why AI, and Why This Pair

- **Biometric ML Model:** Detects compound physiological drift (HRV, RHR, sleep) days before subjective awareness.
- **Claude Sonnet (Language Model):** Translates predictions into one warm, concise, human sentence each morning — actionable without anxiety.

**Why not rules?** Fixed thresholds misclassify normal cycle-driven changes. Models personalize; rules generalize. We need nuance to avoid false alarms.

> Together: One model sees the body, the other speaks to the person. Both are required for a humane, effective product.

## Responsible AI, Built In, Not Bolted On

- **Data Ownership** — User data remains on their account. Nothing is sold. No population-level training without explicit consent.
- **Explainability** — Every prediction is explainable; users can see why Rhythm suggested a specific action.
- **Non-pathologizing** — Cycle-phase context prevents normal biology from being labeled a problem. Outputs are insights, not diagnoses.
- **Ethical Engagement** — No urgency-driven engagement loops. When clinical care is needed, Rhythm recommends professionals and steps back.

## Risk & Trust Model

The personal model needs consistent daily data — early predictions (weeks 2–4) are informative but still general. Rhythm uses a transparent onboarding flow (**Onboard -> Daily Use -> Model Maturation**) that sets expectations and invites users into the learning process.

**User Vulnerability:** Design must protect users when they are emotionally or physiologically depleted — constrained prompts, non-alarmist copy, clear referrals to care, and continual tone review.

## App Demo

The Rhythm home screen surfaces a single daily status card:

- **Status badge** (e.g., *Drifting*) summarizing current recovery state
- **Plain-language summary** — e.g., "Your recovery load is higher than usual. HRV has pulled below your luteal baseline for 3 nights. Sleep efficiency is lighter."
- **7-day trend chart** comparing daily HRV against the user's personal baseline
- **Key metrics** — HRV (ms, % from baseline), sleep (%, % from baseline), and current cycle phase/day

## Future Plan

| Phase | Focus |
|---|---|
| **User Study** | Recruit 20 beta users; run a one-month pilot to compare predictions against user-reported experience. |
| **System Refine** | Ship a TestFlight build; use qualitative feedback to retrain models and refine Claude's tone for higher trust and clarity. |
| **Long Term** | Pursue B2B channels — corporate wellness programs and fertility clinics — as early enterprise partners to scale adoption and data partnerships with consent. |

> The critical metric: did the user open Rhythm after her first drift alert — and did the message match what she felt? That recognition is the product.

## Sources

CEPR 2024 - LinkedIn x Fortune 2024 - WHO - SHRM 2023 - AJPM 2025 - PMC 2024 - Grand View Research 2024

---

## Project Status

This repository is in early development. Contributions, issues, and discussion are welcome as the system architecture and model implementations take shape.
