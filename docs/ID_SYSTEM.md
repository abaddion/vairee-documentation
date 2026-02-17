# Vairee ID System

Structured identifiers for entities in the vairee platform.

## Format

```
{PREFIX}-{YEAR}-{SEQUENCE}
```

- **PREFIX** — 2 letters, entity type
- **YEAR** — 4 digits (e.g. 2024)
- **SEQUENCE** — Zero-padded, typically 4 digits (0001, 0002, ...)

### Examples

| ID | Entity |
|----|--------|
| VT-2024-0142 | Talent #142 in 2024 |
| VL-2024-0008 | Lead (company) #8 in 2024 |
| VJ-2024-0023 | Job #23 in 2024 |
| VR-2024-0005 | Report #5 in 2024 |
| VS-2024-0012 | Screening session #12 in 2024 |

---

## Entity Types

| Prefix | Entity | Use |
|--------|--------|-----|
| **VT** | Talent | Person in the talent pool |
| **VL** | Lead | Company/client |
| **VJ** | Job | Open position |
| **VR** | Report | Screening report |
| **VS** | Session | Screening session |

---

## Properties

### Deterministic

IDs are generated sequentially. Given a prefix and year, the next ID is predictable (e.g. VT-2024-0143 after VT-2024-0142).

### Year-scoped

Sequences reset per year. VT-2025-0001 is the first talent of 2025, independent of 2024 counts.

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
- `VT-2024-0142` (Digital Identity, traceable)
- `VRC-A3K9M2` (blind, non-traceable)

---

## Usage in Workflows

| Workflow | IDs involved |
|----------|--------------|
| Start screening | VJ, VL, VS |
| Pre-filter results | VT (passed/filtered) |
| Screening tasks | VT, VS |
| Human questions | VT, VS |
| Report | VR, VT (or VRC) |
| Unlock | VT → real contact info |

---

## Summary

The vairee ID system provides:

- **Structured format** — Easy to read and parse
- **Type safety** — Prefix indicates entity type
- **Year-scoped sequences** — Clean organization
- **Privacy** — No PII in the ID itself
