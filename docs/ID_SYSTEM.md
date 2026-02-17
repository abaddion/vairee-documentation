# Vairee ID System

Structured identifiers for entities in the vairee platform.

## Format

```
{PREFIX}-{YEAR}-{SEQUENCE}
```

- **PREFIX** — 2 letters, entity type
- **YEAR** — 4 digits (e.g. 2026)
- **SEQUENCE** — Zero-padded, at least 6 digits (000001, 000142, ...) for scale (hundreds of thousands or more users)

### Examples

| ID | Entity |
|----|--------|
| VT-2026-000142 | Talent #142 in 2026 |
| VL-2026-000008 | Lead (company) #8 in 2026 |
| VJ-2026-000023 | Job #23 in 2026 |
| VB-2026-000015 | vairee-business: opportunity/service #15 in 2026 |
| VP-2026-000031 | vairee-project: project #31 in 2026 |
| VR-2026-000005 | Report #5 in 2026 |
| VS-2026-000012 | Screening session #12 in 2026 |

---

## Entity Types

| Prefix | Entity | Use |
|--------|--------|-----|
| **VT** | Talent | Person in the talent pool; one user can have multiple vairee-cards (VT), each for a specific professional goal |
| **VL** | Lead | Company/client |
| **VJ** | Job | Open position (full-time employment) |
| **VB** | Business | vairee-business: professional looking for a business opportunity, offering services, or looking for someone who seeks such a service |
| **VP** | Project | vairee-project: professional not looking for full-time job or employment—side project or any project (can be full-time) |
| **VR** | Report | Screening report |
| **VS** | Session | Screening session |

---

## Properties

### Deterministic

IDs are generated sequentially. Given a prefix and year, the next ID is predictable (e.g. VT-2026-000143 after VT-2026-000142).

### Year-scoped

Sequences reset per year. VT-2027-000001 is the first talent of 2027, independent of 2026 counts.

### Non-reversible

The ID does not reveal the underlying database ID. It is a stable, human-readable reference.

### Parseable

The format can be parsed to extract:

- Entity type (from prefix)
- Year
- Sequence number

---

## Special Cases

### Blind Candidate ID (Reports)

For anonymized report display, a **blind candidate ID** may be used:

- Format: `VRC-XXXXXX` (e.g. VRC-A3K9M2)
- Random, not sequential
- Not traceable to the talent without server-side mapping
- Used when extra anonymity is desired in shared reports

### Display Labels

In reports, candidates may be shown as:

- `Candidate A`, `Candidate B`, ... (for very simple views)
- `VT-2026-000142` (Digital Identity, traceable)
- `VRC-A3K9M2` (blind, non-traceable)

---

## Usage in Workflows

| Workflow | IDs involved |
|----------|--------------|
| Employment screening | VJ, VL, VT, VS |
| vairee-business (services) | VB, VT, VL, VS |
| vairee-project (projects) | VP, VT, VL, VS |
| Pre-filter results | VT (passed/filtered) |
| Screening tasks | VT, VS |
| Human questions | VT, VS |
| Report | VR, VT (or VRC) |
| Handshake | Both parties agree → real contact info (vairee-leads: unlock) |

---

## Summary

The vairee ID system provides:

- **Structured format** — Easy to read and parse
- **Type safety** — Prefix indicates entity type
- **Year-scoped sequences** — Clean organization
- **Privacy** — No PII in the ID itself
