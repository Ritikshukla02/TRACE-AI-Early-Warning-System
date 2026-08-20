# TRACE - Project Overview

## The Idea Behind TRACE

Most content moderation systems analyze individual comments to determine whether they are harmful. However, concerning behavior is not always obvious from a single message.

A comment may appear harmless on its own, but repeated interactions, changes in language, or similar activity across multiple accounts can reveal a more concerning pattern.

TRACE - **Tracking Risk Across Comments and Evaluation** - was developed to look at this broader context.

---

## What TRACE Does

TRACE is an AI-powered early-warning system designed to support Trust & Safety teams in identifying potentially harmful behavioral patterns targeting children.

Rather than relying on a single AI prediction, TRACE combines:

* Comment-level risk classification
* Sender interaction history
* Cross-account behavioral patterns
* Risk escalation over time
* Human review before any final decision

The goal is not to automatically decide whether someone is harmful, but to provide analysts with useful evidence and context for further investigation.

---

## From Comment to Behavioral Pattern

The system first analyzes individual comments using **BERTweet** across eight risk categories:

**Bullying · Coercion · Grooming · Hate · Sextortion · Sexual · Threat · Toxicity**

These results are then combined with broader behavioral information and analyzed using **Gemma**.

Finally, the findings are presented through a **Streamlit dashboard**, where a human analyst can review the evidence and make the final decision.

---

## Hackathon Context

TRACE was developed by **Team Trinetra.ai** for the USAII Global AI Hackathon 2026 in the Graduate & Doctoral **AI for Systems & Society** track, under the **Human Safety & Protection** challenge.

The challenge focused on building responsible AI systems that can help protect people from harm while considering real-world impact and responsible use of AI.

TRACE advanced to the **final round** of the competition.

---

## Human-in-the-Loop by Design

TRACE is designed as a decision-support system rather than an automated enforcement system.

AI helps identify patterns, organize evidence, and highlight potential risks, while the final judgment remains with a human analyst. This keeps human oversight at the center of the system, especially when dealing with sensitive child-safety scenarios.
