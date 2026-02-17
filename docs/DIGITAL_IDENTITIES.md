# Digital Identities: A Whitepaper

## Executive Summary

**Digital Identities** are privacy-preserving identifiers that represent real people (talents) and entities (leads, jobs, sessions, reports) in the vairee system. Instead of exposing names, emails, or company affiliations prematurely, vairee uses structured IDs that:

- Enable traceability across screening workflows
- Preserve anonymity until a hiring decision is made
- Support evidence-based evaluation without exposing PII
- Allow data exchange when both parties digitally handshake

This whitepaper explains the logic, philosophy, and mechanics behind Digital Identities.

---

## 1. The Problem

Traditional recruiting systems often:

- **Make decisions and reject** — Systems gatekeep, filter out, or reject profiles automatically, even ignores
- **Depend on keywords** — Matching relies on keyword hits rather than real conversation based on data
- **Expose talent data early** — Names, current employers, and contact info are visible before a genuine interest exists
- **Create bias** — Unconscious bias affects decisions when identifiable information is visible
- **Lack accountability** — Match scores and recommendations often lack traceable evidence
- **Fail on missing data** — Systems and recruiters either guess or skip when data is incomplete
- **FNo feedback and learning path** — When a job seeker is ghosted or ejected, they do not receive relevant feedback they can learn from and improve

vairee addresses these: it does not decide nor reject, runs real conversation based on data (not keywords), uses a trained AI as a helper, and gives users data-supported information so they make informed decisions. Every profile always has a voice.

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
| VT | Talent | VT-2026-000142 |
| VL | Lead (company) | VL-2026-000008 |
| VJ | Job | VJ-2026-000023 |
| VB | Business | VB-2026-000015 (vairee-business) |
| VP | Project | VP-2026-000031 (vairee-project) |
| VR | Report | VR-2026-000005 |
| VS | Screening Session | VS-2026-000012 |

This format:

- Makes it obvious what type of entity you're looking at
- Resets sequences per year for clean organization
- Keeps IDs short and readable (e.g. `VT-2026-000142` instead of a UUID)

### Multiple Vairee-Cards per User

One user can have **several vairee-cards**, each representing them for a specific professional goal.

Consider LinkedIn: you have only one profile. But imagine you are a business owner of a PR agency and also learning UX design. You are an expert in PR services and junior in UX design. You run your business and look for clients—but you also consider a side part-time project to shape your freshly learned UX skills. If you modify your LinkedIn profile for both goals, everyone gets confused: you lose credibility for PR expertise, and for UX you look overqualified or out of the profession, untrustworthy—as if you don't know what you want.

In vairee, you can have **as many professional identities as you want** without losing credibility. Each vairee-card focuses on a specific goal. One card for your PR agency and client acquisition; another for your UX journey and part-time projects. No conflict, no confusion.

---

## 3. Why Digital Identities?

### 3.1 Privacy by Design

Talents share sensitive data: work history, salary expectations, relocation willingness. Digital Identities (e.g. `VT-2026-000142`) let the system:

- Reference a talent in screening tasks, reports, and conversations
- Never expose the underlying person until both parties digitally handshake
- Every user shares only that data they want without loosing their creditibility and ability to be a part of the conversation flows

### 3.2 Evidence-Based Evaluation

Every screening output links back to a Digital Identity and its associated data:

- **Conversation excerpts** — Structured Q&A between the AI and the profile
- **Skills assessment** — Matched vs. missing skills with scores
- **Fit reasoning** — Summary with strong fits, gaps, and red flags
- **Strong fits / gaps / red flags** — Each item is traceable to the conversation or profile

vairee serves anyone with a professional life—not only hiring managers. All parties see *why* a match makes sense, not just a score:

- **Hiring managers** see why a candidate fits the role and company, highlights, conerns as well as red flags
- **Professionals** see why a company, project, or opportunity fits their goals and preferences
- **Service seekers** see why a service provider fits and why to consider working with them
- **Service providers** see why a client or project aligns with their capabilities

Fit is evaluated in both directions: talent↔company, professional↔opportunity, provider↔client.

### 3.3 Human-in-the-Loop

When the system encounters missing or uncertain data (e.g. location not specified), it:

1. **Pauses** — Stops screening that entity (talent, job, project, business opportunity, or service)
2. **Asks a question** — The user whose profile has the gap receives a request to clarify (e.g. "Define your location preference")
3. **Waits for input** — The user provides the answer
4. **Resumes** — Screening continues with the new data

The question is tied to a **Digital Identity**, so the system knows which profile needs input. vairee encourages complete profiles at signup to reduce over-screening—but profiles are **living organisms**: they can never be 100% complete and evolve through user interactions. User provides feedback on converation responses to train their AI representative to match their tone, style

### 3.4 vairee Does Not Decide nor Reject

**vairee does not make decisions. vairee does not reject.**

- **Real conversation based on data** — vairee runs genuine conversations grounded in profile data, not keyword matching. It does not depend on keywords.
- **AI as a helper** — AI assists in structuring the conversation, extracting evidence, and surfacing insights. It does not judge or gatekeep.
- **Data-supported information and recommendations** — vairee offers users information and recommendations backed by evidence. The **user** makes informed decisions.
- **Profiles are never rejected** — A profile can never be rejected by the system. Every profile always has a voice and remains in the pool until the user chooses otherwise.

vairee provides data-supported information so users can make informed decisions—it does not decide for them.

### 3.5 Profile Transparency & User Feedback

Users can **review everything that happened with their profile**.

- **Reports** — Users receive reports showing how many conversations they were included in and how many excluded from, and *why* they were included or excluded in each case.
- **Own opinion** — Users can provide their own opinion or feedback. If valid and supported by evidence, it is taken into account.
- **No force-evaluation** — A user cannot force-evaluate their profile for a role that does not fit the data. For example, a maintainer cannot claim to be validated as a senior architect for a "cleaner" role—the evidence does not support it.
- **New vairee-card for new goals** — If a user wants to be validated for a different role or professional direction, they are free to create another vairee-card. Each card represents a specific goal; multiple cards let them pursue multiple professional paths without conflating credibility.

---

## 4. The Screening Lifecycle

Digital Identities flow through a defined lifecycle:

```
Job (VJ) + Lead (VL) — or Project, Opportunity, Service
       ↓
Screening Session (VS) created
       ↓
Pre-filter: Light preselection — location, experience, skills (minimum data)
       → Maximizes potential pool; missing data → request clarification, not exclusion
       ↓
trained AI Conversation: Each entity gets a structured Q&A
       ↓
Evaluation: Fit score, strong fits, gaps, red flags (both directions)
       ↓
Report (VR) generated: Top matches listed (anonymized)
       ↓
Handshake: Both parties agree → Digital Identity maps to real contact info
```

At each step, only Digital Identities are used in shared views. Real names and contact details appear only after both parties handshake.

---

## 5. Light Pre-Filter & Missing Data

vairee **preselects lightly** to create a huge potential pool. Filtering happens at minimum data—only the essentials (location, experience, skills) are checked, and the bar is low.

### When Location Is Missing

If a talent has not defined their location:

1. **Request clarification** — The user receives a request to define their location preference.
2. **Until then, include them** — They are considered available for *any* location. vairee does not exclude them from the pool.
3. **Hold before recommending** — If the match is high but location is still missing, vairee **holds** and does not recommend this talent to a hiring manager, and vice versa. This avoids the bias of referring a candidate and jobs or opportunities, projects, with undefined location.
4. **Encourage complete profiles** — vairee prompts users to provide as much data as possible when creating their profile, while keeping them provate, reducing over-screening and repeated clarification requests.

This flow ensures every missing detail is clarified *with the users* who did not complete their profile. The profile can never be 100% complete—it is a **living organism** shaped by user interactions.

---

## 6. Anonymization (Blind CV)

Reports present entities in a **Blind CV** style:

- **Company names scrubbed** — "Software Engineer at [Company]" instead of "Software Engineer at Google"
- **Responsibilities preserved** — What they did, not where
- **Skills, education, location** — Shown for relevance
- **Fit labels** — Strong Match, Good Match, Potential, Weak Match
- **Conversation excerpt** — Q&A format, anonymized

Entities are labeled by Digital Identity (e.g. "VT-2026-000142") until both parties handshake.

---

## 7. Digital Handshake

In vairee, nothing is revealed until **both parties digitally handshake**.

The flow:

1. Both parties see the anonymized profile, screening evaluation, conversations, and outcome
2. If you agree and like what you see, you provide a **digital handshake**
3. When the other party handshakes too, **both** parties can see the data (contact info, details - depends on what data the user choose to share)
4. Until both have handshaken, no personal data is revealed to either side

This creates:

- **Mutual commitment** — Both parties must agree before any data exchange
- **Privacy preserved** — Nothing is revealed until both handshake
- **Feedback loop** - Nobody can reject a handshake without providing a reason an other party can react to 
- **No unilateral exposure** — Neither side gets access without the other's consent

*Note: vairee-leads is a project for presenting vairee and uses an unlock model (pay to reveal). In the vairee space conceptually, the standard is the Digital Handshake—mutual consent before any data is shared.*

---

## 8. Design Principles

| Principle | Description |
|-----------|--------------|
| **Privacy first** | PII is hidden until both parties digitally handshake |
| **Evidence-based** | Every claim links to structured data; fit evaluated in both directions |
| **Light preselection** | Filter at minimum data to maximize pool; request clarification, don't exclude |
| **Human oversight** | AI pauses when it needs input; users clarify their own profiles |
| **Traceability** | Digital Identities enable end-to-end tracking |
| **Fair comparison** | Anonymized presentation reduces bias |
| **Living profiles** | Profiles are never 100% complete; they evolve through user interactions |
| **User agency** | vairee does not decide nor reject; users make informed decisions based on data-supported recommendations; every profile always has a voice |
| **Profile transparency** | Users can review all activity (included/excluded, why); provide feedback evaluated if valid; cannot force-evaluate for mismatched roles; can create new vairee-card for new goals |
| **Multiple vairee-cards** | One user can have several vairee-cards, each for a specific professional goal—no loss of credibility across different paths |

---

## 9. Summary

**Digital Identities** are the backbone of vairee's privacy-preserving, evidence-based approach. vairee serves anyone with a professional life—hiring managers, professionals, service providers, and clients. Digital Identities enable:

- Anonymous representation of talents, leads, jobs, projects, sessions, and reports
- Traceable, evidence-backed evaluations in both directions (talent↔company, provider↔client)
- Human-in-the-loop to clarify missing details with users whose profiles are incomplete
- Light preselection to maximize the potential pool, with holds on recommendations when critical data (e.g. location) is missing
- Profiles as living organisms—never fully complete, shaped by user interactions
- Digital Handshake—both parties must agree before any data is shared
- User agency—vairee does not decide nor reject; it offers data-supported information; users make informed decisions; every profile always has a voice
- Profile transparency—users review all activity (included/excluded, why), provide feedback (evaluated if valid), cannot force-evaluate for mismatched roles; can create new vairee-card for new goals
- Multiple vairee-cards—one user can have several vairee-cards, each focused on a specific professional goal

By design, they keep data protected while enabling efficient, fair, and accountable matching.
