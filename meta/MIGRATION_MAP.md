# FORGE Method - Migration Map

**Version:** 1.0
**Date:** 2026-01-07
**Purpose:** Map original artifacts to consolidated locations

---

## Overview

This document maps the 30+ original downloaded artifacts to their new canonical locations following the consolidation of 2026-01-07.

---

## Migration Table

| Original File | Action | New Location | Rationale |
|---------------|--------|--------------|-----------|
| `forge-core.md` | COPY | `core/forge-core.md` | Canonical core doc |
| `forge-operations.md` | COPY | `core/forge-operations.md` | Canonical operations doc |
| `forge-orientation.md` | COPY | `core/forge-orientation.md` | Canonical orientation doc |
| `forge-governance.md` | COPY | `core/forge-governance.md` | Canonical governance doc |
| `the-forge-method.md` | ARCHIVE | `archive/historical/the-forge-method.md` | Superseded by forge-core.md |
| `forge-sd-profile.md` | MERGE | `profiles/forge-sd-profile.md` | Merged with addendum |
| `forge-sd-profile-addendum.md` | MERGE | `profiles/forge-sd-profile.md` | Merged into main profile |
| `forge-agent-roles-handoffs.md` | COPY | `agents/forge-agent-roles-handoffs.md` | Agent role definitions |
| `forge-jordan-operating-guide.md` | COPY | `agents/forge-jordan-operating-guide.md` | Jordan-specific guide |
| `forge-core-essentials.md` | COPY | `agents/forge-core-essentials.md` | Jordan condensed reference |
| `forge-template-frame.md` | MERGE | `templates/forge-template-frame.md` | Merged with artifact version |
| `forge-template-frame-artifact.md` | MERGE | `templates/forge-template-frame.md` | Merged into main template |
| `forge-template-kickoff-brief.md` | MERGE | `templates/forge-template-kickoff-brief.md` | Merged with template version |
| `forge-kickoff-brief-template.md` | MERGE | `templates/forge-template-kickoff-brief.md` | Merged into main template |
| `forge-project-template-spec.md` | MERGE | `templates/forge-template-project-spec.md` | Merged specifications |
| `forge-project-template-specification.md` | MERGE | `templates/forge-template-project-spec.md` | Merged into main spec |
| `forge-template-project-identity.md` | COPY+FIX | `templates/forge-template-project-identity.md` | Fixed UTF-8 encoding |
| `forge-template-project-identity copy.md` | DELETE | N/A | Duplicate file |
| `forge-template-repository-scaffold.md` | COPY | `templates/forge-template-repository-scaffold.md` | Repository scaffold spec |
| `forge-template-cp-handoff-packet.md` | COPY | `templates/forge-template-cp-handoff-packet.md` | CP handoff template |
| `forge-templates.md` | COPY | `templates/forge-templates.md` | Template collection |
| `forge-kickoff-brief.md` | ARCHIVE | `archive/instances/forge-kickoff-brief.md` | Filled instance, not template |
| `phase-zero-methodology.md` | ARCHIVE | `archive/historical/phase-zero-methodology.md` | Superseded pre-FORGE |
| `intent-to-execution-method.md` | ARCHIVE | `archive/historical/intent-to-execution-method.md` | Superseded early FORGE |
| `genesis-quick-start.md` | ARCHIVE | `archive/historical/genesis-quick-start.md` | Superseded quick-start |
| `cc-forge-operations-validation-brief.md` | ARCHIVE | `archive/development/cc-forge-operations-validation-brief.md` | Dev task brief |
| `cc-forge-review-task-brief.md` | ARCHIVE | `archive/development/cc-forge-review-task-brief.md` | Dev task brief |
| `cc-review-forge-instantiation-artifacts.md` | ARCHIVE | `archive/development/cc-review-forge-instantiation-artifacts.md` | Dev task brief |
| `jordan-custom-instructions.json` | ARCHIVE | `archive/config/jordan-custom-instructions.json` | Historical config |
| `jordan-custom-instructions-v3.json` | ARCHIVE | `archive/config/jordan-custom-instructions-v3.json` | Current config |

---

## Action Legend

| Action | Meaning |
|--------|---------|
| **COPY** | Direct copy to new location with no changes |
| **COPY+FIX** | Copy with encoding or formatting fixes |
| **MERGE** | Content merged from multiple source files |
| **ARCHIVE** | Moved to archive for historical reference |
| **DELETE** | Removed (duplicate or unnecessary) |

---

## Merge Details

### profiles/forge-sd-profile.md (v1.1)

**Sources:**
- `forge-sd-profile.md` (v1.0)
- `forge-sd-profile-addendum.md` (v1.0)

**Merged Sections:**
- From first: Profile Identity, Authority Boundaries, PR/Repo Expectations, Branch Strategy, Decision Heuristics
- From second: Relationship to FORGE Core, Repo as Source of Truth, CC's SQL Ownership, Cursor Rules File, Quick Reference Cards

---

### templates/forge-template-frame.md (v1.2)

**Sources:**
- `forge-template-frame.md` (v1.1)
- `forge-template-frame-artifact.md` (v1.1)

**Merged Sections:**
- From first: Core template, Failure Modes, Transition guidance
- From second: Project Type & FORGE Adaptation, Quality Checks, Sizing Guidance

---

### templates/forge-template-kickoff-brief.md (v1.1)

**Sources:**
- `forge-template-kickoff-brief.md` (v1.0)
- `forge-kickoff-brief-template.md` (v1.0)

**Merged Sections:**
- From first: Field Definitions, Brief vs Frame comparison, Common Failure Modes
- From second: Authority Confirmation, Amendment Log, Table-based format

---

### templates/forge-template-project-spec.md (v1.1)

**Sources:**
- `forge-project-template-spec.md` (v1.0)
- `forge-project-template-specification.md` (v1.0)

**Merged Sections:**
- From first: CLAUDE.md content template, cursor-rules content
- From second: Instantiation sequence with framework scaffolding, Stack variance handling

---

## Summary Statistics

| Action | Count |
|--------|-------|
| COPY | 10 |
| COPY+FIX | 1 |
| MERGE | 8 (4 output files) |
| ARCHIVE | 10 |
| DELETE | 1 |
| **Total Processed** | **30** |

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-07 | Initial migration map |

---

**(c) 2026 Knight Ventures, Inc. All rights reserved.**

**FORGE(TM)** is a trademark of Knight Ventures, Inc.
