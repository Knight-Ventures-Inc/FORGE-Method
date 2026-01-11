# Recon Reports

**Validated execution evidence from FORGE testing**

---

## What This Is

Recon reports document **real-world testing** of tools, integrations, and assumptions that affect FORGE execution. They are not canonical doctrine — they are verified evidence.

---

## Why These Exist

FORGE methodology claims to be execution-derived, not theoretical. These documents prove it:

- **Demonstrate rigor** — We test before we prescribe
- **Correct bad assumptions** — Internet research often diverges from reality
- **Prevent repeated mistakes** — Future users learn from our failures
- **Build trust** — Advanced users can verify our claims

---

## What Belongs Here

| Include | Don't Include |
|---------|---------------|
| Environment details (versions) | Step-by-step tutorials |
| Original hypothesis | Marketing language |
| Tests performed | "This will always work" claims |
| What worked | Installation guides |
| What FAILED (critical) | Aspirational features |
| Corrected mental model | Unverified assumptions |
| Recommended patterns | |
| Explicit warnings | |

---

## Document Standard

Each recon follows this structure:

```markdown
# Recon Report: [Topic]

**Date:** YYYY-MM
**Environment:** [Tool version, OS, context]
**Status:** Validated | Needs Re-test
**Audience:** Advanced FORGE users

## Purpose
## Initial Assumptions
## Test Environment
## Tests Performed
## Findings
## Corrected Mental Model
## Recommended Pattern (FORGE)
## Known Limitations & Gotchas
## Status
```

---

## Governance

- **Authored by:** CC (primary investigator) + Jordan (synthesis)
- **Approved by:** Leo (steward authority)
- **Review:** Steward-approved, not crowd-edited
- **Updates:** Version-specific; re-test on major tool updates

---

## Disclaimer

> These documents reflect real-world testing performed by the FORGE maintainers.
> Results are version-specific and may change as tools evolve.
> This is not canonical FORGE doctrine, but validated execution evidence.

---

## Index

| Report | Date | Status |
|--------|------|--------|
| [CP Local Agent Recon](./2026-01-CP-Local-Agent-Recon.md) | 2026-01 | Validated |

---

*This is part of The FORGE Method(TM) — theforgemethod.org*
