# FORGE-SD Profile

**Software Development Execution Profile**

**Version:** 1.1
**Status:** Canonical Profile
**Base:** FORGE Core v1.1 + Operations Manual v1.1

---

## Purpose

FORGE-SD is a **software development execution profile** that layers software-specific execution rules onto core FORGE methodology. This profile governs all Knight Ventures software projects using the standard agent constellation.

**This document explicitly defines:**
- Role mappings for software development
- Repo as source of truth
- CC's ownership of executable SQL and migrations
- Sacred Four verification sequence
- PR and repository expectations
- What is profile-specific vs inherited from canon

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

## Profile Identity

| Field | Value |
|-------|-------|
| **Profile Name** | FORGE-SD |
| **Full Name** | FORGE Software Development |
| **Domain** | Production software systems |
| **Typical Output** | Deployed web applications, APIs, services |
| **Cycle Duration** | 30-90 minutes per PR |

---

## Role Mappings

### FORGE Core to FORGE-SD Mapping

| FORGE Role | FORGE-SD Agent | Platform | Authority |
|------------|----------------|----------|-----------|
| **Human Lead** | Leo | Human | Final decisions, greenlights, merges, disputes |
| **Strategist** | Jordan | ChatGPT | Business strategy, feature ideation, option framing |
| **Spec Author** | CP | Claude Project | Constitutional docs, task briefs, ADRs |
| **Quality Gate** | CC | Claude Code | Verification, PRs, build-plan, minor fixes |
| **Implementation Engine** | Cursor | Cursor IDE | Code production per task briefs |

### Authority Boundaries (FORGE-SD Specific)

| Agent | CAN | CANNOT |
|-------|-----|--------|
| **Leo** | Approve/reject any decision; merge PRs; override specs; resolve disputes | N/A - full authority |
| **Jordan** | Propose features; frame options; draft Kickoff Briefs; synthesize patterns | Implement code; create PRs; modify specs unilaterally |
| **CP** | Author constitutional docs; write task briefs; propose ADRs | Implement code; create PRs; approve own specs |
| **CC** | Run verification; create PRs; fix <5 lines; maintain build-plan | Make architectural decisions; modify constitution; merge |
| **Cursor** | Write code per brief; create/modify files in src/ | Create PRs; modify docs/; make architectural calls |

---

## Communication Topology (FORGE-SD)

```
                         LEO
                    (Human Lead)
                         |
         +---------------+---------------+
         |               |               |
         v               v               v
      JORDAN            CP              CC
    (Strategist)   (Spec Author)   (Quality Gate)
         |               |               |
         +-------+-------+               |
                 |                       |
            bidirectional            one-way
            collaboration          specs flow down
                                        |
                                        v
                                     CURSOR
                               (Implementation)
```

**Key Rules:**
- Leo can engage any agent directly at any time
- Jordan and CP collaborate bidirectionally (ideation <-> specification)
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
| Task briefs | `inbox/active/` | CC authors |
| Archived briefs | `inbox/completed/` | CC archives |
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

## The Sacred Four (FORGE-SD Implementation)

### Canonical Pattern

```bash
typecheck && lint && test && build
```

### Standard Commands (Next.js / TypeScript / pnpm)

```bash
pnpm typecheck && pnpm lint && pnpm test:run && pnpm build
```

### Step Definitions

| Step | Command | Purpose | Failure Meaning |
|------|---------|---------|-----------------|
| **typecheck** | `pnpm typecheck` | Type safety validation | Code has TypeScript errors |
| **lint** | `pnpm lint` | Code standards enforcement | ESLint rule violations |
| **test** | `pnpm test:run` | Functionality verification | Logic errors or regressions |
| **build** | `pnpm build` | Production readiness | Bundle/compilation issues |

### Verification Rules (Profile-Specific)

1. **All four steps must pass** - No exceptions
2. **Order is fixed** - typecheck -> lint -> test -> build
3. **Build is mandatory** - Tests passing != build passing
4. **CC runs verification** - Not Cursor, not Leo
5. **Run on every PR** - Before PR creation, not after

### Why All Four Matter

| Mistake | Which Step Catches It |
|---------|----------------------|
| Type mismatch | typecheck |
| Unused import | lint |
| Wrong calculation | test |
| Missing export | build |
| Route conflict | build |
| Circular dependency | build |

**Tests passing != Build passing.** Build catches route conflicts, missing exports, and bundle issues that tests miss.

### Output Handling

**On Success:**
```
- typecheck passed
- lint passed
- test passed (N tests)
- build passed

-> Proceed to PR creation
```

**On Failure:**
```
x [step] failed

-> CC diagnoses failure
-> If <5 lines to fix: CC fixes, re-runs verification
-> If >5 lines to fix: Send back to Cursor
-> If unclear: Escalate to Leo
```

---

## PR and Repository Expectations

### Branch Strategy

| Branch | Purpose | Who Creates | Who Merges |
|--------|---------|-------------|------------|
| `main` | Production-ready code | N/A (exists) | Leo only |
| `feat/pr-XX-[name]` | Feature work | CC | Leo merges to main |
| `fix/pr-XX-[name]` | Bug fixes | CC | Leo merges to main |

### Branch Naming Convention

```
feat/pr-01-project-scaffold
feat/pr-02-auth-setup
feat/pr-03-database-schema
fix/pr-04-login-redirect
```

### PR Lifecycle

```
1. CC creates branch from latest main
2. CC writes task brief, commits
3. Cursor implements per brief
4. CC pulls Cursor's commits
5. CC runs Sacred Four
6. CC fixes minor issues OR sends back
7. CC creates PR with description
8. Leo reviews and merges
9. CC updates build-plan
10. Loop to next PR
```

### PR Description Template

```markdown
## PR-[XX]: [Name]

### What This PR Does
[One paragraph summary]

### Changes
- [Change 1]
- [Change 2]
- [Change 3]

### Verification
- [x] typecheck passed
- [x] lint passed
- [x] test passed (N tests)
- [x] build passed

### HAT (Human Acceptance Test)
1. [Step to verify]
2. [Expected result]

### Task Brief
`inbox/completed/pr-XX-[name].md`

### Related
- Spec: `docs/constitution/[relevant-doc].md`
- Previous: PR-[XX-1]
```

### Commit Message Convention

```
type(scope): description

# Types: feat, fix, docs, style, refactor, test, chore
# Scope: component or area affected

# Examples:
feat(auth): implement login flow
fix(api): correct rate limit handling
docs(readme): update setup instructions
chore(deps): upgrade Next.js to 15.1
```

---

## Repository Structure (FORGE-SD)

```
[project-name]/
+-- .cursor/
|   +-- rules/
|       +-- project.mdc           # Cursor rules
+-- .github/
|   +-- CODEOWNERS
+-- inbox/
|   +-- active/                   # Current task brief
|   +-- completed/                # Archived briefs
|   +-- templates/
+-- docs/
|   +-- constitution/             # READ-ONLY during Execute
|   |   +-- 01-north-star.md
|   |   +-- 02-system-architecture.md
|   |   +-- 03-data-model.md
|   |   +-- 04-api-contract.md
|   |   +-- 05-security-policies.md
|   |   +-- 06-engineering-playbook.md
|   +-- adrs/                     # Architecture decisions
|   +-- build-plan.md             # CC maintains
+-- src/                          # Application code
+-- tests/                        # Test files
+-- .env.example
+-- .gitignore
+-- CLAUDE.md                     # Project identity
+-- LICENSE
+-- package.json
+-- pnpm-lock.yaml
+-- README.md
+-- tsconfig.json
```

---

## Decision Heuristics (FORGE-SD)

### The 5-Line Rule

| Lines Changed | Action |
|---------------|--------|
| < 5 lines | CC fixes directly |
| >= 5 lines | Send back to Cursor |

### Fix vs Escalate vs Abandon

**CC fixes directly:**
- Import/export corrections
- Missing TypeScript types
- Typos in variable names
- Route path corrections
- Single-line type mismatches

**CC sends back to Cursor:**
- Logic errors (not syntax)
- Missing functionality from brief
- Multi-file changes needed
- Test failures from wrong implementation

**CC escalates to Leo:**
- Spec ambiguity
- Security-adjacent decisions
- Scope expansion detected
- Build failure not diagnosed in 5 minutes
- Architectural questions

**CC abandons approach:**
- Same error 3 times after fixes
- Cascading failures (fix A breaks B)
- Complexity exploding
- "This should be simple but isn't"

---

## Cursor Rules File

### Location

`.cursor/rules/forge-sd.mdc`

### Content

```markdown
# Cursor Rules - FORGE-SD Project

## Identity

You are the **Implementation Engine** in a FORGE-SD project.

Your role: Execute task briefs exactly as specified. Produce code. Hand off to Quality Gate (CC).

## Before Any Work

1. Read `CLAUDE.md` in project root
2. Read the active task brief in `inbox/active/`
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
pnpm typecheck && pnpm lint && pnpm test:run && pnpm build

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
5. When unclear, ask - don't guess

---

*This project follows The FORGE Method - theforgemethod.org*
```

---

## Transition Between Phases

### Pre-Execute (Frame -> Orchestrate -> Refine -> Govern)

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
| Fix/Escalate | CC | <5 lines fix; >5 lines rework; unclear -> Leo |
| PR | CC | Create PR with description |
| Merge | Leo | Review and merge |
| Repeat | - | Back to Trigger |

---

## What Is Canon vs Profile-Specific

### Canon (FORGE Core) - Universal to All FORGE Projects

| Element | Status |
|---------|--------|
| Five macro-steps (F-O-R-G-E) | **Canon** |
| Five Laws | **Canon** |
| Agent roles (Human Lead, Strategist, Spec Author, Quality Gate, Implementation Engine) | **Canon** |
| Constitutional document hierarchy | **Canon** |
| The FORGE Cycle (16-step loop) | **Canon** |
| Human greenlight requirement | **Canon** |
| Inbox-driven workflow | **Canon** |
| 5-line rule | **Canon** |
| Fix / Escalate / Abandon heuristics | **Canon** |

*Note: The FORGE Cycle is defined in FORGE Core v1.1 and detailed in the FORGE Operations Manual.*

### Profile-Specific (FORGE-SD) - Software Development Only

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

### Adaptable Within FORGE-SD

These elements may vary by project while staying within FORGE-SD:

- Specific package manager (pnpm/npm/yarn)
- Framework (Next.js/Remix/etc.)
- Test runner (Vitest/Jest)
- Database (Supabase/Postgres/etc.)
- Hosting (Vercel/Cloudflare/etc.)
- Status emoji in build-plan

---

## Quick Reference Card

### For CC (Quality Gate)

```
START OF SESSION:
1. Read CLAUDE.md
2. Check docs/build-plan.md
3. git log --oneline -5
4. Check inbox/active/

EVERY PR:
1. Archive previous brief -> completed/
2. Update build-plan.md
3. Write new task brief -> active/
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
2. Read inbox/active/[current-brief].md
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

## Profile Activation

To use FORGE-SD on a new project:

1. **Kickoff Brief** specifies `Profile: FORGE-SD`
2. **Repository** created per FORGE Project Template Spec
3. **CLAUDE.md** references this profile
4. **All agents** operate per this addendum

---

## Profile Governance

| Change Type | Authority |
|-------------|-----------|
| Agent platform assignments | Leo (Human Lead) |
| Sacred Four command syntax | CP (Spec Author) with Leo approval |
| Branch/PR conventions | CP (Spec Author) with Leo approval |
| Core FORGE elements | Requires FORGE Core version change |

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-04 | Initial FORGE-SD profile |
| 1.1 | 2026-01-07 | Consolidated from forge-sd-profile.md and forge-sd-profile-addendum.md; merged unique sections from both sources |

---

**[FORGE-SD PROFILE]**

**(c) 2026 Knight Ventures, Inc. All rights reserved.**

**FORGE(TM)** is a trademark of Knight Ventures, Inc.
