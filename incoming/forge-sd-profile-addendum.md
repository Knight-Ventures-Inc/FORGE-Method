# FORGE-SD Profile Addendum

**Software Development Execution Rules**

**Version:** 1.0  
**Status:** Execution Profile  
**Parent:** FORGE Core v1.1

---

## Purpose

FORGE-SD is a **software development execution profile** that layers software-specific rules onto core FORGE methodology.

This document defines:
- Role mappings for software projects
- Repo as source of truth
- CC's ownership of executable SQL and migrations
- Sacred Four verification sequence
- What is canon vs profile-specific

---

## Relationship to FORGE Core

| Aspect | FORGE Core | FORGE-SD Profile |
|--------|------------|------------------|
| **Scope** | Domain-agnostic methodology | Software development only |
| **Authority** | Canonical | Additive (extends, never overrides) |
| **Roles** | Abstract (Human Lead, Strategist, etc.) | Concrete (Leo, Jordan, CP, CC, Cursor) |
| **Artifacts** | Constitutional documents | Repos, PRs, migrations, tests |
| **Verification** | Mechanical checks (abstract) | Sacred Four (typecheck, lint, test, build) |

**Rule:** If FORGE Core and FORGE-SD conflict, FORGE Core wins. FORGE-SD only adds specificity; it never contradicts.

---

## Role Mappings

### FORGE Core → FORGE-SD Mapping

| FORGE Role | FORGE-SD Agent | Platform | Authority |
|------------|----------------|----------|-----------|
| **Human Lead** | Leo | Human | Final decision-maker. Greenlights, merges, resolves disputes. |
| **Strategist** | Jordan | ChatGPT | Ideation, shaping, Kickoff Brief authoring. Does NOT specify or implement. |
| **Spec Author** | CP | Claude Project | Constitutional documents, prompts, ADRs. Does NOT implement or create PRs. |
| **Quality Gate** | CC | Claude Code | Verification, task briefs, PRs, build-plan. Does NOT make architectural decisions. |
| **Implementation Engine** | Cursor | Cursor IDE | Executes task briefs. Does NOT create PRs or make architectural calls. |

### Communication Topology (FORGE-SD)

```
                    ┌─────────────────────────────────┐
                    │             LEO                 │
                    │     (Greenlight & Authority)    │
                    └──────────────┬──────────────────┘
                                   │
         ┌─────────────────────────┼─────────────────────────┐
         │                         │                         │
         ▼                         ▼                         ▼
┌─────────────────┐  ┌─────────────────────┐  ┌─────────────────┐
│     JORDAN      │  │         CP          │  │       CC        │
│   (ChatGPT)     │◄►│  (Claude Project)   │─►│  (Claude Code)  │
│   Strategist    │  │    Spec Author      │  │   Quality Gate  │
└─────────────────┘  └─────────────────────┘  └────────┬────────┘
                                                       │
                                                       ▼
                                             ┌─────────────────┐
                                             │     CURSOR      │
                                             │  Implementation │
                                             │     Engine      │
                                             └─────────────────┘
```

**Key Rules:**
- Leo can engage any agent directly
- Jordan and CP collaborate bidirectionally (ideation ↔ specification)
- CP produces constitutional docs; they flow one-way to CC
- CC and Cursor cycle tightly during Execute
- Cursor never communicates with Jordan or CP directly

---

## Repo as Source of Truth

### The Single Canonical Record (Law 4)

In FORGE-SD, the **Git repository** is the single source of truth.

| Artifact Type | Location | Owner |
|---------------|----------|-------|
| Constitutional documents | `docs/constitution/` | CP authors; CC reads |
| Build state | `docs/build-plan.md` | CC maintains |
| Task briefs | `ai_prompts/active/` | CC authors |
| Archived briefs | `ai_prompts/completed/` | CC archives |
| Application code | `src/` | Cursor implements; CC verifies |
| Migrations | `supabase/migrations/` | CC generates |
| Tests | `tests/` | Cursor implements; CC verifies |

### What This Means

1. **If it's not in the repo, it doesn't exist.** Conversation history, chat logs, and verbal agreements are not authoritative.

2. **Drift is prevented by reference, not duplication.** Task briefs reference constitutional docs by path; they don't copy content.

3. **The repo is always deployable.** Main branch passes Sacred Four at all times.

---

## CC's Ownership: SQL and Migrations

### The Intent-to-Execution Boundary

**CP (Spec Author)** defines data model *intent* in `docs/constitution/data-model.md`:
- Tables and relationships
- Field names, types, constraints
- Business rules and validation
- RLS policy requirements

**CC (Quality Gate)** translates intent into *executable SQL*:
- Migration files in `supabase/migrations/`
- Exact SQL syntax
- Migration ordering
- Seed data scripts

### Why This Separation Matters

| Agent | Produces | Does NOT Produce |
|-------|----------|------------------|
| CP | Data model specification (what tables, what fields, what rules) | SQL syntax, migration files |
| CC | SQL migrations, seed scripts | Schema design decisions |

**Rule:** CP never writes SQL intended to be run directly. CP specifies *what* the schema should be. CC implements *how* it becomes real.

**Rule:** CC never invents schema. CC translates CP's specification exactly. If the spec is ambiguous, CC escalates to Leo.

### Migration Generation Flow

```
1. CP writes data-model.md (specification)
2. Leo approves data-model.md (greenlight)
3. CC reads data-model.md
4. CC generates migration SQL
5. CC runs migration locally to verify
6. CC commits migration file
7. CC updates build-plan.md
```

---

## Sacred Four Verification Sequence

### The Invariant Pattern

Every PR runs this exact sequence before merge:

```bash
typecheck && lint && test && build
```

**All four must pass. No exceptions. No "it works on my machine."**

### FORGE-SD Commands (Default Stack)

For Next.js / TypeScript / pnpm:

```bash
pnpm typecheck && pnpm lint && pnpm test:run && pnpm build
```

| Step | Command | Purpose | Failure Meaning |
|------|---------|---------|-----------------|
| **typecheck** | `pnpm typecheck` | Type safety | Code has type errors |
| **lint** | `pnpm lint` | Code standards | Style or pattern violations |
| **test** | `pnpm test:run` | Functionality | Logic errors or regressions |
| **build** | `pnpm build` | Production readiness | Bundle/compilation issues |

### Why All Four Matter

| Mistake | Which Step Catches It |
|---------|----------------------|
| Type mismatch | typecheck |
| Unused import | lint |
| Wrong calculation | test |
| Missing export | build |
| Route conflict | build |
| Circular dependency | build |

**Tests passing ≠ Build passing.** Build catches route conflicts, missing exports, and bundle issues that tests miss.

### Verification Output Protocol

**On Success:**
```
✓ typecheck passed
✓ lint passed
✓ test passed (N tests)
✓ build passed

→ Proceed to PR creation
```

**On Failure:**
```
✗ [step] failed

→ Diagnose failure
→ If <5 lines to fix: fix and re-verify
→ If >5 lines to fix: send back to Cursor
→ If unclear: escalate to Leo
```

---

## What Is Canon vs Profile-Specific

### Canon (FORGE Core) — Universal to All FORGE Projects

| Element | Status |
|---------|--------|
| Five macro-steps (F-O-R-G-E) | **Canon** |
| Five Laws | **Canon** |
| Agent roles (Human Lead, Strategist, Spec Author, Quality Gate, Implementation Engine) | **Canon** |
| Constitutional document hierarchy | **Canon** |
| The FORGE Cycle (16-step loop) | **Canon** |
| Human greenlight requirement | **Canon** |
| File-based handoffs | **Canon** |
| 5-line rule | **Canon** |
| Fix / Escalate / Abandon heuristics | **Canon** |

*Note: The FORGE Cycle is defined in FORGE Core v1.1 and detailed in the FORGE Operations Manual.*

### Profile-Specific (FORGE-SD) — Software Development Only

| Element | Status |
|---------|--------|
| Role mappings (Jordan, CP, CC, Cursor) | **FORGE-SD** |
| Repo as source of truth | **FORGE-SD** |
| Git workflow (branches, PRs, merges) | **FORGE-SD** |
| Sacred Four (typecheck, lint, test, build) | **FORGE-SD** |
| Directory structure (`src/`, `supabase/`, etc.) | **FORGE-SD** |
| CC ownership of SQL/migrations | **FORGE-SD** |
| Cursor rules file (`.cursor/rules/`) | **FORGE-SD** |
| pnpm / npm commands | **FORGE-SD** |

### Future Profiles (Not Yet Defined)

| Profile | Domain | Key Differences |
|---------|--------|-----------------|
| **FORGE-BOOK** | Book/content creation | Chapters instead of PRs; editorial review instead of Sacred Four |
| **FORGE-SVC** | Service business | Deliverables instead of deployments; client approval gates |
| **FORGE-RE** | Real estate | Deal stages instead of PRs; due diligence gates |

These profiles will follow the same pattern: layer domain-specific execution rules onto FORGE Core without modifying the methodology itself.

---

## Cursor Rules File

### Location

`.cursor/rules/forge-sd.mdc`

### Content

```markdown
# Cursor Rules — FORGE-SD Project

## Identity

You are the **Implementation Engine** in a FORGE-SD project.

Your role: Execute task briefs exactly as specified. Produce code. Hand off to Quality Gate (CC).

## Before Any Work

1. Read `CLAUDE.md` in project root
2. Read the active task brief in `ai_prompts/active/`
3. Understand what you are building before writing code

## During Implementation

1. Follow the task brief exactly
2. Do not add features not in the brief
3. Do not refactor unrelated code
4. Do not make architectural decisions
5. Reference constitutional docs in `docs/constitution/` when unclear

## What You Do NOT Do

- Create pull requests (CC does this)
- Modify `docs/constitution/` (read-only)
- Modify `docs/build-plan.md` (CC maintains)
- Make architectural decisions
- Expand scope beyond the task brief
- Communicate with Jordan or CP directly

## Before Handoff

Run all verification steps:
```bash
pnpm typecheck && pnpm lint && pnpm test:run && pnpm build
```

Report results honestly. Do not claim "all tests pass" unless they actually do.

## Handoff Format

When complete, provide:
- What was built
- Files created/modified
- Verification results (actual output)
- Any issues or concerns

## The 5-Line Rule

If CC identifies issues:
- <5 lines to fix: CC fixes directly
- >5 lines to fix: Returns to you with updated brief

## Non-Negotiables

1. Task briefs are authoritative
2. Constitutional docs are read-only
3. Sacred Four must pass before handoff
4. Honesty over optimism in status reports
5. When unclear, ask — don't guess

---

*This project follows The FORGE Method™ — theforgemethod.org*
```

---

## Transition Between Phases

### Pre-Execute (Frame → Orchestrate → Refine → Govern)

| Phase | Primary Agents | Artifacts Produced |
|-------|---------------|-------------------|
| Frame | Leo + Jordan | Kickoff Brief |
| Orchestrate | Leo + Jordan + CP | Role assignments, CLAUDE.md draft |
| Refine | CP (with Leo approval) | Constitutional documents |
| Govern | CP + CC | Verification sequence, escalation rules |

### Execute (The FORGE Cycle)

| Step | Agent | Action |
|------|-------|--------|
| Trigger | Leo | "Start PR-XX" |
| Brief | CC | Write task brief |
| Implement | Cursor | Build per brief |
| Verify | CC | Run Sacred Four |
| Fix/Escalate | CC | <5 lines fix; >5 lines rework; unclear → Leo |
| PR | CC | Create PR with description |
| Merge | Leo | Review and merge |
| Repeat | — | Back to Trigger |

---

## Quick Reference Card

### For CC (Quality Gate)

```
START OF SESSION:
1. Read CLAUDE.md
2. Check docs/build-plan.md
3. git log --oneline -5
4. Check ai_prompts/active/

EVERY PR:
1. Archive previous brief → completed/
2. Update build-plan.md
3. Write new task brief → active/
4. Hand to Cursor
5. Receive implementation
6. Run Sacred Four
7. Fix (<5 lines) or return (>5 lines)
8. Create PR
9. Notify Leo

SACRED FOUR:
pnpm typecheck && pnpm lint && pnpm test:run && pnpm build
```

### For Cursor (Implementation Engine)

```
START OF TASK:
1. Read CLAUDE.md
2. Read ai_prompts/active/[current-brief].md
3. Reference docs/constitution/ as needed

DURING IMPLEMENTATION:
- Follow brief exactly
- Don't expand scope
- Don't modify constitution

BEFORE HANDOFF:
- Run Sacred Four
- Report actual results
- Note any concerns
```

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-04 | Initial FORGE-SD profile |

---

**[FORGE-SD PROFILE]**

**© 2026 Knight Ventures, Inc. All rights reserved.**

**FORGE™** is a trademark of Knight Ventures, Inc.
