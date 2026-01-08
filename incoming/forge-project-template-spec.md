# FORGE Project Template Specification

**Structural Blueprint for FORGE Project Instantiation**

**Version:** 1.0  
**Status:** Canonical Specification  
**Implementer:** CC (Quality Gate)

---

## Purpose

This specification defines the **exact structure** CC must create when instantiating a new FORGE project. It is a spec, not a repo — CC implements this mechanically.

**This document answers:** "What does a FORGE project look like on disk before any code is written?"

---

## Assumptions

- Target environment: iMac Pro, Knight Ventures projects directory
- CC has access to create directories and files
- Constitutional documents arrive separately (from CP via Leo)
- This spec covers structure only, not content
- FORGE-SD profile is the default execution profile

---

## Required Directory Structure

```
[project-name]/
│
├── .cursor/
│   └── rules/
│       └── cursor-rules.md          # Cursor IDE configuration
│
├── .github/
│   └── CODEOWNERS                   # (Optional) Code ownership
│
├── ai_prompts/
│   ├── active/                      # Current task briefs (one at a time)
│   │   └── .gitkeep
│   ├── completed/                   # Archived briefs (one per merged PR)
│   │   └── .gitkeep
│   └── templates/                   # Reusable brief templates
│       └── task-brief-template.md
│
├── docs/
│   ├── constitution/                # READ-ONLY during Execute
│   │   ├── north-star.md
│   │   ├── system-architecture.md
│   │   ├── data-model.md
│   │   ├── api-contract.md
│   │   └── engineering-playbook.md
│   ├── decisions/                   # ADRs (Architecture Decision Records)
│   │   └── .gitkeep
│   └── build-plan.md                # Execution state (CC maintains)
│
├── src/                             # Application source (structure varies by stack)
│   └── .gitkeep
│
├── tests/                           # Test files
│   └── .gitkeep
│
├── supabase/                        # Database layer (if using Supabase)
│   ├── migrations/                  # SQL migrations (CC owns)
│   │   └── .gitkeep
│   └── seed/                        # Seed data
│       └── .gitkeep
│
├── .env.example                     # Environment variable template
├── .gitignore                       # Standard ignores
├── CLAUDE.md                        # CC's operating instructions
├── package.json                     # (Created during scaffolding)
└── README.md                        # Project overview (can mirror CLAUDE.md)
```

---

## Required Files: Specifications

### CLAUDE.md

**Location:** Project root  
**Purpose:** CC's operating instructions for this project  
**Maintained by:** CC (initial), then read-only during Execute

**Required Sections:**

```markdown
# [Project Name]

**One-line description:** [From Kickoff Brief]

---

## Project Identity

### What This Is
[From North Star]

### What This Is NOT
[From Kickoff Brief non-goals]

---

## FORGE Context

This project follows **The FORGE Method™**.

**Current Phase:** [Frame | Orchestrate | Refine | Govern | Execute]
**Execution Profile:** FORGE-SD (Software Development)

### Key FORGE Principles
- Constitutional docs are read-only during Execute
- Quality Gate (CC) owns build-plan.md
- Implementation Engine output requires verification
- The 5-line rule: <5 lines = fix locally, >5 lines = send back
- Verification sequence is sacred: typecheck && lint && test && build

---

## Authority & Boundaries

| Role | Agent | Authority |
|------|-------|-----------|
| Human Lead | Leo | Final decisions, greenlight, merge |
| Strategist | Jordan | Ideation, framing, Kickoff Briefs |
| Spec Author | CP | Constitutional documents |
| Quality Gate | CC | Verification, PRs, build-plan |
| Implementation | Cursor | Code per task briefs |

---

## Commands

### Development
```bash
pnpm dev          # Start development server
pnpm build        # Production build
```

### Verification Sequence (Sacred)
```bash
pnpm typecheck && pnpm lint && pnpm test:run && pnpm build
```

### Database
```bash
pnpm db:generate  # Generate migrations
pnpm db:migrate   # Apply migrations
```

---

## Current State

**Current PR:** [PR-XX or "Not started"]
**Build Plan:** `docs/build-plan.md`
**Active Brief:** `ai_prompts/active/[current].md`

---

## Getting Oriented (New Session)

1. Read this file
2. Check `docs/build-plan.md` for current state
3. Run: `git log --oneline -5`
4. Check `ai_prompts/active/` for current brief
5. Ready to proceed (~90 seconds)

---

*This project follows The FORGE Method™ — theforgemethod.org*
```

---

### cursor-rules.md

**Location:** `.cursor/rules/cursor-rules.md`  
**Purpose:** Cursor IDE behavioral configuration  
**Maintained by:** CC (initial), then stable

**Required Content:**

```markdown
# Cursor Rules — [Project Name]

## Context

This project uses **The FORGE Method™** with the **FORGE-SD** execution profile.

You are the **Implementation Engine**. Your role is to execute task briefs precisely.

## Your Boundaries

### You DO:
- Read task briefs from `ai_prompts/active/`
- Implement exactly what the brief specifies
- Follow patterns established in existing code
- Report completion status clearly

### You DO NOT:
- Create PRs (CC does this)
- Make architectural decisions
- Modify constitutional documents
- Expand scope beyond the task brief
- Communicate directly with Strategist or Spec Author

## Before You Code

1. Read the active task brief completely
2. Check referenced constitutional docs if specified
3. Understand acceptance criteria before starting
4. Note any "Do NOT" constraints

## Code Standards

- Follow patterns in `docs/constitution/engineering-playbook.md`
- TypeScript strict mode
- Explicit types over inference for function signatures
- Handle errors explicitly, no silent swallowing

## When You're Done

Report:
- What was built
- Files created/modified
- Any deviations from brief (with rationale)
- Verification status if you ran checks

Then hand off to CC via Leo.
```

---

### task-brief-template.md

**Location:** `ai_prompts/templates/task-brief-template.md`  
**Purpose:** Template for task briefs (CC creates these)

**Content:** Use the template from FORGE Operations Manual Appendix A.

---

### build-plan.md

**Location:** `docs/build-plan.md`  
**Purpose:** Execution state machine  
**Maintained by:** CC only

**Initial Content:**

```markdown
# Build Plan — [Project Name]

**Last Updated:** [YYYY-MM-DD]
**Current PR:** Not started

## Changelog

| Date | PR | Status | Notes |
|------|-----|--------|-------|
| [Date] | — | 🚀 | Project instantiated |

## PR Sequence

| PR | Name | Status | Dependencies | Notes |
|----|------|--------|--------------|-------|
| 01 | [First PR from Execution Plan] | ➡️ | None | Next |

## Current Focus

Awaiting first task brief.

## Blocked Items

None.

## Backlog

[Items not yet scheduled]
```

---

### .env.example

**Location:** Project root  
**Purpose:** Document required environment variables

**Initial Content:**

```bash
# [Project Name] Environment Variables
# Copy to .env.local and fill in values

# App
NEXT_PUBLIC_APP_URL=http://localhost:3000

# Supabase
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=

# Add project-specific variables below
```

---

### .gitignore

**Location:** Project root  
**Purpose:** Standard ignores

**Content:**

```gitignore
# Dependencies
node_modules/
.pnpm-store/

# Environment
.env
.env.local
.env.*.local

# Build
.next/
out/
dist/
build/

# IDE
.idea/
.vscode/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db

# Logs
*.log
npm-debug.log*

# Testing
coverage/

# Misc
*.tsbuildinfo
```

---

## Constitutional Documents: Placement

Constitutional documents are created by CP, downloaded by Leo, and placed by CC.

| Document | Location | Source |
|----------|----------|--------|
| North Star | `docs/constitution/north-star.md` | CP |
| System Architecture | `docs/constitution/system-architecture.md` | CP |
| Data Model | `docs/constitution/data-model.md` | CP |
| API Contract | `docs/constitution/api-contract.md` | CP |
| Engineering Playbook | `docs/constitution/engineering-playbook.md` | CP |

**CC's responsibility:** Place these files. Do not modify content.

---

## Instantiation Sequence

When CC receives a project instantiation request:

1. **Create directory structure** per this spec
2. **Generate placeholder files** (all `.gitkeep` files, templates)
3. **Generate CLAUDE.md** using Kickoff Brief data
4. **Generate cursor-rules.md** using project name
5. **Generate build-plan.md** with empty initial state
6. **Generate .env.example** with standard variables
7. **Generate .gitignore** with standard ignores
8. **Initialize git repository** (`git init`)
9. **Await constitutional documents** from Leo
10. **Place constitutional documents** in `docs/constitution/`
11. **Update build-plan.md** with PR sequence from Execution Plan
12. **Report ready status** to Leo

---

## Validation Checklist

Before reporting "ready":

- [ ] All directories exist
- [ ] CLAUDE.md is complete and accurate
- [ ] cursor-rules.md is in place
- [ ] Constitutional documents are in `docs/constitution/`
- [ ] build-plan.md reflects the Execution Plan
- [ ] .env.example lists required variables
- [ ] git is initialized
- [ ] No placeholder content remains in committed files

---

## What This Spec Does NOT Cover

- Application scaffolding (Next.js init, etc.) — that's PR-01
- Database setup — that's in the Execution Plan
- Deployment configuration — that's in System Architecture
- Actual code — that's Execute phase

This spec covers **structure only**.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-04 | Initial specification |

---

**© 2026 Knight Ventures, Inc. All rights reserved.**

**FORGE™** is a trademark of Knight Ventures, Inc.
