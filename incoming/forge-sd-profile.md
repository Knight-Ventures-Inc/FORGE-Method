# FORGE-SD Profile Addendum

**Software Development Execution Profile**

**Version:** 1.0  
**Status:** Canonical Profile  
**Base:** FORGE Core v1.1 + Operations Manual v1.1

---

## Purpose

FORGE-SD layers software-development-specific execution rules onto core FORGE methodology. This profile governs all Knight Ventures software projects using the standard agent constellation.

**This document explicitly defines:**
- Role mappings for software development
- Sacred Four verification usage
- PR and repository expectations
- What is profile-specific vs inherited from canon

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

### Standard FORGE-SD Agent Constellation

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
| **Leo** | Approve/reject any decision; merge PRs; override specs; resolve disputes | N/A — full authority |
| **Jordan** | Propose features; frame options; draft Kickoff Briefs; synthesize patterns | Implement code; create PRs; modify specs unilaterally |
| **CP** | Author constitutional docs; write task briefs; propose ADRs | Implement code; create PRs; approve own specs |
| **CC** | Run verification; create PRs; fix <5 lines; maintain build-plan | Make architectural decisions; modify constitution; merge |
| **Cursor** | Write code per brief; create/modify files in src/ | Create PRs; modify docs/; make architectural calls |

---

## Communication Topology (FORGE-SD)

```
                         LEO
                    (Human Lead)
                         │
         ┌───────────────┼───────────────┐
         │               │               │
         ▼               ▼               ▼
      JORDAN            CP              CC
    (Strategist)   (Spec Author)   (Quality Gate)
         │               │               │
         └───────┬───────┘               │
                 │                       │
            bidirectional            one-way
            collaboration          specs flow down
                                        │
                                        ▼
                                     CURSOR
                               (Implementation)
```

**Key Rules:**
- Leo can engage any agent directly at any time
- Jordan ↔ CP collaborate bidirectionally on strategy and specs
- CP → CC: Specs flow one-way (CC does not modify)
- CC ↔ Cursor: Tight verification cycle
- Cursor never communicates with Jordan or CP directly

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

1. **All four steps must pass** — No exceptions
2. **Order is fixed** — typecheck → lint → test → build
3. **Build is mandatory** — Tests passing ≠ build passing
4. **CC runs verification** — Not Cursor, not Leo
5. **Run on every PR** — Before PR creation, not after

### Output Handling

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

→ CC diagnoses failure
→ If <5 lines to fix: CC fixes, re-runs verification
→ If >5 lines to fix: Send back to Cursor
→ If unclear: Escalate to Leo
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
`ai_prompts/completed/pr-XX-[name].md`

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
├── .cursor/
│   └── rules/
│       └── project.mdc           # Cursor rules
├── .github/
│   └── CODEOWNERS
├── ai_prompts/
│   ├── active/                   # Current task brief
│   ├── completed/                # Archived briefs
│   └── templates/
├── docs/
│   ├── constitution/             # READ-ONLY during Execute
│   │   ├── 01-north-star.md
│   │   ├── 02-system-architecture.md
│   │   ├── 03-data-model.md
│   │   ├── 04-api-contract.md
│   │   ├── 05-security-policies.md
│   │   └── 06-engineering-playbook.md
│   ├── adrs/                     # Architecture decisions
│   └── build-plan.md             # CC maintains
├── src/                          # Application code
├── tests/                        # Test files
├── .env.example
├── .gitignore
├── CLAUDE.md                     # Project identity
├── LICENSE
├── package.json
├── pnpm-lock.yaml
├── README.md
└── tsconfig.json
```

---

## Decision Heuristics (FORGE-SD)

### The 5-Line Rule

| Lines Changed | Action |
|---------------|--------|
| < 5 lines | CC fixes directly |
| ≥ 5 lines | Send back to Cursor |

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

## What Is Profile-Specific vs Canon

### Inherited from FORGE Canon (DO NOT MODIFY)

These elements come directly from FORGE Core and Operations Manual:

- The Five Laws
- The Five Macro-Steps (F-O-R-G-E)
- The FORGE Cycle structure
- Constitutional document hierarchy
- File-based handoff mechanism
- Human greenlight requirement
- 90% rule for specs
- Escalation principles

### Profile-Specific (FORGE-SD Only)

These elements are specific to software development and may differ in other profiles:

- Agent platform assignments (Jordan=ChatGPT, CP=Claude Project, etc.)
- Sacred Four command syntax
- Branch naming convention
- PR description template
- Commit message convention
- Repository directory structure
- Technology stack assumptions (TypeScript, pnpm, Next.js)

### Adaptable Within FORGE-SD

These elements may vary by project while staying within FORGE-SD:

- Specific package manager (pnpm/npm/yarn)
- Framework (Next.js/Remix/etc.)
- Test runner (Vitest/Jest)
- Database (Supabase/Postgres/etc.)
- Hosting (Vercel/Cloudflare/etc.)
- Status emoji in build-plan

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

---

**© 2026 Knight Ventures, Inc. All rights reserved.**

**FORGE™** is a trademark of Knight Ventures, Inc.
