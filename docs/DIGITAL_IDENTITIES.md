# Digital Identities: A Whitepaper

## Executive Summary

**Digital Identities** are privacy-preserving identifiers that represent real people (talents) and entities (leads, jobs, sessions, reports) in the vairee system. Instead of exposing names, emails, or company affiliations prematurely, vairee uses structured IDs that:

- Enable traceability across screening workflows
- Preserve anonymity until a hiring decision is made
- Support evidence-based evaluation without exposing PII
- Allow controlled unlock when a hiring manager commits

This whitepaper explains the logic, philosophy, and mechanics behind Digital Identities.

---

## 1. The Problem

Traditional recruiting systems often:

- **Expose talent data early** — Names, current employers, and contact info are visible before a genuine interest exists
- **Create bias** — Unconscious bias affects decisions when identifiable information is visible
- **Lack accountability** — Match scores and recommendations often lack traceable evidence
- **Fail on missing data** — Systems either guess or skip when data is incomplete

vairee addresses these with Digital Identities.

---

## 2. What is a Digital Identity?

A **Digital Identity** in vairee is a unique, structured identifier that:

1. **Refers to a real entity** (person, company, job, session, or report)
2. **Does not reveal PII** — No names, emails, or employers in the ID itself
3. **Is deterministic and traceable** — The same ID is used consistently across workflows
4. **Follows a typed format** — Different entity types have different prefixes

### ID Format

```
{PREFIX}-{YEAR}-{SEQUENCE}
```

| Prefix | Entity | Example |
|--------|--------|---------|
| VT | Talent | VT-2024-0142 |
| VL | Lead (company) | VL-2024-0008 |
| VJ | Job | VJ-2024-0023 |
| VR | Report | VR-2024-0005 |
| VS | Screening Session | VS-2024-0012 |

This format:

- Makes it obvious what type of entity you're looking at
- Resets sequences per year for clean organization
- Keeps IDs short and readable (e.g. `VT-2024-0142` instead of a UUID)

---

## 3. Why Digital Identities?

### 3.1 Privacy by Design

Talents share sensitive data: work history, salary expectations, relocation willingness. Digital Identities (e.g. `VT-2024-0142`) let the system:

- Reference a talent in screening tasks, reports, and conversations
- Never expose the underlying person until an explicit unlock

### 3.2 Evidence-Based Evaluation

Every screening output links back to a Digital Identity and its associated data:

- **Conversation excerpts** — Structured Q&A between the AI and the talent profile
- **Skills assessment** — Matched vs. missing skills with scores
- **Fit reasoning** — Summary with strong fits, gaps, and red flags
- **Strong fits / gaps / red flags** — Each item is traceable to the conversation or profile

Hiring managers see *why* a candidate fits, not just a score.

### 3.3 Human-in-the-Loop

When the AI encounters missing or uncertain data (e.g. location not specified), it:

1. **Pauses** — Stops screening that talent
2. **Asks a question** — "What is this talent's city and country?"
3. **Waits for human input** — A recruiter or operator provides the answer
4. **Resumes** — Screening continues with the new data

The question is tied to a **talent Digital Identity** (`VT-2024-0142`), so the human knows which profile needs input without seeing the person's name.

---

## 4. The Screening Lifecycle

Digital Identities flow through a defined lifecycle:

```
Job (VJ) + Lead (VL)
       ↓
Screening Session (VS) created
       ↓
Pre-filter: Talents (VT) passed/filtered by location, experience, skills
       ↓
AI Conversation: Each VT gets a structured Q&A
       ↓
Evaluation: Fit score, strong fits, gaps, red flags
       ↓
Report (VR) generated: Top candidates listed by VT (anonymized)
       ↓
Unlock: Hiring manager pays → VT maps to real contact info
```

At each step, only Digital Identities are used in shared views. Real names and contact details appear only after unlock.

---

## 5. Anonymization (Blind CV)

Reports present talents in a **Blind CV** style:

- **Company names scrubbed** — "Software Engineer at [Company]" instead of "Software Engineer at Google"
- **Responsibilities preserved** — What they did, not where
- **Skills, education, location** — Shown for relevance
- **Fit labels** — Strong Match, Good Match, Potential, Weak Match
- **Conversation excerpt** — Q&A format, anonymized

Candidates are labeled by Digital Identity (e.g. "Candidate VT-2024-0142") until unlock.

---

## 6. Unlock Model

When a hiring manager wants to contact a candidate:

1. They see the anonymized profile and screening evaluation
2. They click **Unlock** (typically a fee, e.g. $99)
3. The system maps the talent Digital Identity to the real person
4. Contact info (name, email, phone, LinkedIn) is revealed

This creates:

- **Commitment signal** — Paying to unlock shows real interest
- **Revenue for the platform** — Sustainable model
- **Privacy for talent** — Only serious employers get their details

---

## 7. Design Principles

| Principle | Description |
|-----------|--------------|
| **Privacy first** | PII is hidden until explicit unlock |
| **Evidence-based** | Every claim links to structured data |
| **Human oversight** | AI pauses when it needs human input |
| **Traceability** | Digital Identities enable end-to-end tracking |
| **Fair comparison** | Anonymized presentation reduces bias |

---

## 8. Summary

**Digital Identities** are the backbone of vairee's privacy-preserving, evidence-based recruiting approach. They enable:

- Anonymous representation of talents, leads, jobs, sessions, and reports
- Traceable, evidence-backed evaluations
- Human-in-the-loop when data is missing
- Controlled unlock when hiring managers commit

By design, they keep talent data protected while enabling efficient, fair, and accountable screening.
