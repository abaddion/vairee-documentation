# Screening Flow

This document describes the end-to-end screening workflow in vairee: from job selection to shareable report.

## Overview

```
┌─────────────────┐
│ 1. PRE-FILTER   │  Location, experience, skills, role category
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ 2. AI SCREENING │  Structured Q&A with talent profile
└────────┬────────┘
         │
         ▼
┌─────────────────┐     ┌──────────────────┐
│ 3. EVALUATION   │◄────│ Human-in-Loop    │  When data missing
└────────┬────────┘     │ (Answer Q)       │
         │              └──────────────────┘
         ▼
┌─────────────────┐
│ 4. REPORT       │  Shareable, anonymized, evidence-based
└─────────────────┘
```

---

## 1. Pre-Filter

Before any AI interaction, talents are filtered by deterministic rules:

| Criterion | Logic |
|-----------|-------|
| **Location** | Must be in required cities, or remote-allowed, or willing to relocate |
| **Experience** | Years must meet job minimum |
| **Skills** | Must-have skills checked (presence/absence) |
| **Role category** | Job role (engineering, design, sales, etc.) matched to talent's experience |

Talents that fail the pre-filter are **excluded** with a clear reason (e.g. "Location mismatch", "Experience below minimum"). Only those who pass enter the AI screening phase.

---

## 2. AI Screening (Conversation)

For each talent that passes the pre-filter:

1. **Load talent profile** — Resume, skills, location, preferences
2. **Structured Q&A** — AI asks questions based on job requirements and profile gaps
3. **Evidence extraction** — Each answer is parsed for evidence (skills found, concerns raised)
4. **Minimum depth** — At least N exchanges to ensure sufficient coverage

Questions can be:

- **Missing data** — "Talent has no location specified. What is their city and country?"
- **Verification** — "Profile says 5 years, but resume suggests 3. Can you confirm?"
- **Clarification** — "Role title is ambiguous. What is their actual responsibility level?"

When the AI cannot proceed (e.g. location missing), it **pauses** and creates a **human question** with a 5-minute timeout. The talent is skipped if no answer is given.

---

## 3. Evaluation

After the conversation, the AI produces a structured evaluation:

| Field | Description |
|-------|-------------|
| **Overall fit** | Strong / Good / Potential / Weak / No fit |
| **Fit reasoning** | Summary paragraph explaining the assessment |
| **Skills assessment** | Must-have score (%), matched vs. missing skills |
| **Strong fits** | Points that support the candidate |
| **Potential gaps** | Areas of concern with severity |
| **Red flags** | Deal-breakers or risks |

Each claim is tied to evidence from the conversation or profile. No generic statements—everything is traceable.

---

## 4. Report Generation

When screening is complete:

1. **Sort by fit** — Strong → Good → Potential (configurable minimum)
2. **Limit candidates** — e.g. top 5
3. **Build report** — Job info, stats (profiles scanned, conversations held, duration), candidate cards
4. **Generate shareable link** — Token-based URL for hiring managers
5. **Anonymize** — All candidates shown as Digital Identities; company names scrubbed

The report is **public** (no login) via the shareable link. Hiring managers can:

- Expand candidate cards to see full evaluation
- Read conversation excerpts
- Unlock a candidate (pay fee) to get contact info

---

## 5. Human-in-the-Loop

When the system pauses on a question:

1. **Recruiter sees alert** — "2 questions waiting"
2. **Opens Questions page** — Sees question, context, talent ID
3. **Provides answer** — e.g. "San Jose, California, USA"
4. **Submits** — Screening continues automatically

Questions have:

- **Priority** — Blocking / Important / Optional
- **Type** — Missing data / Verification / Clarification
- **Timeout** — 5 minutes; talent skipped if unanswered

---

## 6. Key Metrics

| Metric | Description |
|--------|-------------|
| Profiles scanned | Total talents in pool (or inflated for demo) |
| Conversations held | Number of talents screened (completed) |
| Avg. exchange depth | Mean Q&A rounds per conversation |
| Screening duration | Wall-clock time from start to completion |

---

## Summary

The screening flow is:

1. **Pre-filter** — Rule-based exclusion
2. **AI screening** — Structured Q&A with human-in-the-loop
3. **Evaluation** — Evidence-based fit assessment
4. **Report** — Shareable, anonymized, with unlock option

This keeps talent data private, decisions evidence-based, and humans in control when the AI needs help.
