# vairee Documentation

Public documentation and whitepapers for the **vairee** platform—a privacy-preserving, AI-powered talent screening system built around the concept of **Digital Identities**.

## Contents

| Document | Description |
|----------|-------------|
| [**Digital Identities Whitepaper**](./docs/DIGITAL_IDENTITIES.md) | The logic behind Digital Identities: anonymous identifiers, evidence-based evaluation, and human-in-the-loop screening |
| [**Screening Flow**](./docs/SCREENING_FLOW.md) | End-to-end screening workflow: pre-filter → AI conversation → evaluation → report |
| [**ID System**](./docs/ID_SYSTEM.md) | vairee ID format and entity types (VT, VL, VJ, VR, VS) |

## What is vairee?

vairee is a digital identity platform that:

1. **Preserves talent privacy** — Talents and professionals are represented by Digital Identities (anonymous IDs) until a hiring manager or potential business partner commits to a data exchange
2. **Uses evidence-based evaluation** — Every claim in screening reports is backed by structured data from AI-powered conversations, not guesswork
3. **Puts humans in the loop** — When the system encounters missing or uncertain data, it pauses and asks for human input before continuing
4. **Enables fair comparison** — Hiring managers see anonymized "Blind CV" style profiles first, reducing bias

## Publishing to GitHub (Public Repo)

To share this documentation publicly:

1. Create a new **public** repository on GitHub (e.g. `vairee-documentation`)
2. Add the remote and push:

   ```bash
   cd vairee-documentation
   git remote add origin https://github.com/YOUR_USERNAME/vairee-documentation.git
   git branch -M main
   git push -u origin main
   ```

3. The repo will be public; no secrets or proprietary code are included.

## License

This documentation is open for public reference (MIT). The vairee software itself is proprietary.
