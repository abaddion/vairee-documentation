# Screening Flow

This document describes the end-to-end screening workflow in vairee: from job selection to shareable report.

## Overview

```
┌─────────────────┐
│ CREATE vairee   │  Users data, profile
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ 1. PRE-FILTER   │  Location, experience, skills, role category
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ 2. AI SCREENING │  Structured Q&A with talent, job, professional profile
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

## 1. Pre-Filter: Light Preselection

vairee **preselects lightly** to maximize the potential pool. Filtering happens at **minimum data**—only location, some experience, and skills are checked—with a low bar to keep options broad, so we really do not screen a cleaner for a sw engineering job

| Criterion | Logic |
|-----------|-------|
| **Location** | If defined: must be in required cities, or remote-allowed, or willing to relocate. **If missing**: user receives a request to define it; until then, considered available for *any* location |
| **Experience** | Years must meet minimum (when specified) | This is not strict; however to avoid screening a junior for senior opportunities
| **Skills** | Must-have skills checked (presence/absence) | Only three mandatory
| **Role category** | Job role matched / find similarities (thus a Creative Director is not ignored for an Art Lead role just because of the title mismatch) to experience (when available) |

### Example: Missing Location: Request, Don’t Exclude

If a talent has not defined their location:

1. **Request clarification** — The user receives a request to define their location preference.
2. **Include in pool** — Until they answer, they are treated as available for any location (not excluded).
3. **Hold before recommending** — If match is high but location is still missing, vairee **holds** and does not recommend this talent. This avoids the bias of referring someone with undefined location.
4. **Complete profiles at signup** — vairee encourages users to provide as much data as possible when creating their profile to avoid over-screening.

Talents who clearly fail (e.g. experience far below minimum, role mismatch) are **excluded** with a reason, however are considered for more relevant screening. Others—including those with missing location—enter the AI screening phase.

---

## 2. AI Trained Screening (Conversation)

For each entity that passes the pre-filter:

1. **Load profile** — Resume, skills, location, preferences
2. **Structured Q&A** — AI asks questions based on requirements and profile gaps
3. **Evidence extraction** — Each answer is parsed for evidence (skills found, concerns raised)
4. **Minimum depth** — At least N exchanges to ensure sufficient coverage

Questions clarify missing details *with the users* whose profiles are incomplete:

- **Missing data** — "Define your location preference" (sent to the user)
- **Verification** — "Profile says 5 years, but resume suggests 3. Can you confirm?"
- **Clarification** — "Role title is ambiguous. What is your actual responsibility level?"

When the AI cannot proceed (e.g. location missing), it **pauses** and creates a clarification request. The user receives it; until they answer, vairee holds before recommending. Profiles are **living organisms**—they can never be 100% complete and evolve through user interactions.

---

## 3. Evaluation

After the conversation, the AI produces a structured evaluation:

| Field | Description |
|-------|-------------|
| **Overall fit** | Strong / Good / Potential / Weak / No fit |
| **Fit reasoning** | Summary paragraph explaining the assessment |
| **Skills assessment** | Must-have score (%), matched vs. missing skills |
| **Strong fits** | Points that support the match |
| **Potential gaps** | Areas of concern with severity |
| **Red flags** | Deal-breakers or risks |

Fit is evaluated in **both directions**: why the candidate fits the company *and* why the company fits the candidate; why the professional fits the opportunity *and* vice versa; why the service provider fits *and* why to work with them. Each claim is tied to evidence from the conversation or profile. No generic statements—everything is traceable.

---

## 4. Report Generation

When screening is complete:

1. **Sort by fit** — Strong → Good → Potential (configurable minimum)
2. **Limit candidates** — e.g. top 5
3. **Build report** — Job info, stats (profiles scanned, conversations held, duration), candidate cards
4. **Anonymize** — All candidates shown as Digital Identities; company names scrubbed
5. **Candidate reports** — Every candidate can generate their own report to see how vairee represented them
6. **Shareable link** — Optional: token-based URL for hiring managers or other parties to view a report

Every **candidate can generate their own report** to see how vairee represented them—included/excluded, why, conversation excerpts, evaluation.

Reports can also be shared (e.g. via link) so hiring managers or other parties can:

- Expand cards to see full evaluation
- Read conversation excerpts
- Digital Handshake (both parties agree) to reveal contact info—or unlock in vairee-leads (presentation version)

---

## 5. Human-in-the-Loop

When the system pauses on missing or uncertain data:

1. **User receives request** — The person whose profile has the gap gets a request to clarify (e.g. "Define your location preference")
2. **User provides answer** — e.g. "San Jose, California, USA"
3. **Screening resumes** — Continues automatically with the new data
4. **Operator option** — In some flows, a recruiter or operator can answer on behalf of the user (e.g. when data is in another system)

Questions have:

- **Priority** — Blocking / Important / Optional
- **Type** — Missing data / Verification / Clarification
- **Target** — The user whose profile needs the update

This flow ensures every missing detail is clarified with the users who did not complete their profile. vairee encourages complete profiles at signup to reduce over-screening—but profiles are living organisms, never 100% complete, shaped by interactions.

---

## 6. Key Metrics

| Metric | Description |
|--------|-------------|
| Profiles scanned | Total talents in pool (or inflated for demo) |
| Conversations held | Number of talents screened (completed) |
| Avg. exchange depth | Mean Q&A rounds per conversation |
| Screening duration | Wall-clock time from start to completion |

---

## 7. Profile Reports & User Feedback

Users can **review everything that happened with their profile**:

- **Reports** — How many conversations they were included in and how many excluded from; *why* they were included or excluded in each case
- **Own opinion** — Users can provide their own feedback; if valid and supported by evidence, it is taken into account
- **No force-evaluation** — Users cannot force-evaluate their profile for a role that does not fit the data (e.g. a maintainer cannot claim validation as senior architect)
- **New vairee-card** — To pursue a different professional goal, users create another vairee-card; one user can have multiple vairee-cards, each focused on a specific path

---

## Summary

The screening flow is:

1. **Pre-filter** — Light preselection at minimum data to maximize pool; missing location → request clarification, not exclusion; hold before recommending when critical data is missing
2. **AI screening** — Structured Q&A; clarify gaps with users whose profiles are incomplete
3. **Evaluation** — Evidence-based fit in both directions (talent↔company, provider↔client)
4. **Report** — Shareable, anonymized; data revealed when both parties digitally handshake (vairee-leads uses unlock for presentation)

This keeps data private, decisions evidence-based, and users in control. vairee does not decide nor reject: it runs real conversation based on data (not keywords), uses AI as a helper, and offers data-supported information and recommendations—users make informed decisions. Every profile always has a voice and can never be rejected by the system. Users can review all activity (included/excluded, why), provide feedback, and have multiple vairee-cards for different professional goals.
