# FORGE System Architecture Report

**To:** Jordan (Strategist)
**From:** CC (Quality Gate)
**Date:** 2026-01-08
**Subject:** How FORGE Works Now — Complete System Overview

---

## Executive Summary

The FORGE ecosystem is now fully wired with a **two-layer architecture**:

1. **FORGE-Method** — The canon (what FORGE *is*)
2. **FORGE-SD** — The template (what you *clone*)

This report explains the complete system: layout, files, cold-start workflow, and how our team (Leo, Jordan, CP, CC, Cursor) launches new projects.

---

## Part 1: The Two-Layer Model

### Layer 1: FORGE-Method (Canon)

**Repository:** `Knight-Ventures-Inc/FORGE-Method`
**Purpose:** Teaches FORGE, defines lanes, provides starter configurations

```
FORGE-Method/
├── core/                    # Canonical methodology
│   ├── forge-core.md        # The Five Laws, Five Macro-Steps
│   ├── forge-operations.md  # The FORGE Cycle, operational procedures
│   ├── forge-orientation.md # New agent onboarding
│   └── forge-governance.md  # Versioning, contribution, licensing
│
├── profiles/                # Domain-specific execution profiles
│   └── forge-sd-profile.md  # Software Development profile
│
├── agents/                  # Agent-specific guides
│   ├── forge-agent-roles-handoffs.md
│   ├── forge-jordan-operating-guide.md
│   └── forge-core-essentials.md
│
├── templates/               # First-class artifact templates
│   ├── forge-template-frame.md
│   ├── forge-template-kickoff-brief.md
│   ├── forge-template-project-spec.md
│   └── ... (7 templates total)
│
├── starter-kit/             # Ready-to-use configurations
│   ├── CLAUDE.md            # Project identity template
│   ├── .cursor/rules/       # Role-specific Cursor rules
│   │   ├── forge-sd.mdc     # Implementation Engine
│   │   ├── forge-cp.mdc     # Spec Author
│   │   └── forge-cc.mdc     # Quality Gate
│   ├── chatgpt/             # Jordan setup
│   │   ├── PROJECT_SETUP.md
│   │   └── custom-instructions-jordan.md
│   └── claude_ai/           # CP and CC setup
│       ├── PROJECT_SETUP.md
│       ├── custom-instructions-cp.md
│       └── custom-instructions-cc.md
│
├── meta/                    # Repository control
│   ├── MANIFEST.md          # Complete document index
│   ├── MIGRATION_MAP.md     # Old → New file mapping
│   └── DEPRECATIONS.md      # Where deprecated files moved
│
└── archive/                 # Historical artifacts
```

**Key Principle:** FORGE-Method is the *specification*. It never contains project-specific code.

---

### Layer 2: FORGE-SD (Template)

**Repository:** `Knight-Ventures-Inc/forge-sd-template`
**Purpose:** Drop-in template you clone to start a new project

```
forge-sd-template/
├── CLAUDE.md                 # Pre-wired for FORGE execution
├── .cursor/rules/
│   ├── forge-sd.mdc          # Implementation Engine rules
│   └── forge-cc.mdc          # Quality Gate rules
│
├── docs/
│   ├── constitution/         # REQUIRED INPUTS
│   │   ├── README.md         # Explains what's needed
│   │   ├── PRODUCT.md        # Product intent (empty placeholder)
│   │   ├── TECH.md           # Technical architecture (empty)
│   │   └── GOVERNANCE.md     # Security, policies (empty)
│   ├── adr/                  # Architecture Decision Records
│   ├── ops/                  # Operational state
│   │   └── state.md
│   └── build-plan.md         # Execution state
│
├── ai_prompts/
│   ├── active/               # Current task brief
│   ├── completed/            # Archived briefs
│   └── templates/            # Task brief templates
│
├── src/                      # Application source (empty)
├── tests/                    # Test files (empty)
└── README.md                 # Drop-in instructions
```

**Key Principle:** FORGE-SD is the *reference implementation*. It consumes FORGE-Method by reference, never redefines it.

---

## Part 2: The Constitutional Documents

The constitution is the **minimum viable input** required before Execute can begin.

### Three Required Documents

| Document | What It Defines | Who Provides It |
|----------|-----------------|-----------------|
| `PRODUCT.md` | Product intent, user value, success criteria, scope | Jordan (via Frame) + CP (refined) |
| `TECH.md` | Stack, architecture, data model overview, constraints | CP (based on Frame) |
| `GOVERNANCE.md` | Auth, RLS, security policies, permissions | CP (based on requirements) |

### Constitution Rules

1. **Empty constitution = CC stops** — No scaffolding, no implementation
2. **Read-only during Execute** — Changes require Leo approval
3. **Hierarchy matters** — PRODUCT.md constrains TECH.md constrains all code

---

## Part 3: Cold Start Workflow (New FORGE User)

### Step 1: Learn FORGE (30 minutes)

New user reads in order:
1. `FORGE-Method/core/forge-orientation.md` — Why FORGE exists
2. `FORGE-Method/core/forge-core.md` — The Five Laws, Five Macro-Steps
3. `FORGE-Method/core/forge-operations.md` — The FORGE Cycle

### Step 2: Set Up Agents (15 minutes each)

**Jordan (ChatGPT):**
1. Create ChatGPT Project: `[ProjectName] - Jordan (Strategist)`
2. Paste `starter-kit/chatgpt/custom-instructions-jordan.md` into Instructions
3. Upload core docs as Knowledge

**CP (Claude.ai):**
1. Create Claude Project: `[ProjectName] - CP (Spec Author)`
2. Paste `starter-kit/claude_ai/custom-instructions-cp.md` into Instructions
3. Upload core docs + templates as Knowledge

**CC (Claude Code):**
1. Clone FORGE-SD template
2. Cursor rules are already wired
3. CC reads CLAUDE.md and operates

**Cursor:**
1. Open project in Cursor IDE
2. Cursor rules auto-load from `.cursor/rules/`
3. Cursor reads task briefs and implements

### Step 3: Clone Template (2 minutes)

```bash
git clone https://github.com/Knight-Ventures-Inc/forge-sd-template.git my-project
cd my-project
rm -rf .git
git init
```

### Step 4: Customize (5 minutes)

Edit `CLAUDE.md`:
- Replace `[CUSTOMIZE]` markers with project values
- Set current phase
- Identify Human Lead

### Step 5: Provide Constitution

Populate `docs/constitution/`:
- `PRODUCT.md` — From Jordan's Frame Artifact
- `TECH.md` — From CP's technical spec
- `GOVERNANCE.md` — From security requirements

### Step 6: Begin Execution

CC reads CLAUDE.md, sees constitution exists, begins The FORGE Cycle.

---

## Part 4: Team Workflow (Leo, Jordan, CP, CC, Cursor)

### Phase: Frame

```
Leo: "I want to build [product idea]"
     ↓
Jordan: Produces Frame Artifact
     - What problem we're solving
     - Who it's for
     - What's in/out of scope
     - Success criteria
     ↓
Leo: Reviews and approves Frame
```

**Output:** Frame Artifact (business intent locked)

---

### Phase: Orchestrate

```
Leo: Assigns agent roles
     ↓
     - Jordan = ChatGPT Project
     - CP = Claude.ai Project
     - CC = Claude Code
     - Cursor = Cursor IDE
     ↓
Leo: Clones FORGE-SD template
Leo: Customizes CLAUDE.md
```

**Output:** Repository scaffolded, agents assigned

---

### Phase: Refine

```
Jordan + CP: Collaborate on specs
     ↓
CP: Produces constitutional documents
     - PRODUCT.md (from Frame)
     - TECH.md (technical decisions)
     - GOVERNANCE.md (security/policies)
     ↓
Leo: Reviews and approves constitution
Leo: Places docs in docs/constitution/
```

**Output:** Constitution complete (specs locked)

---

### Phase: Govern

```
Leo: Defines quality gates
     ↓
     - Sacred Four must pass
     - 5-line rule enforced
     - Escalation triggers documented
     ↓
Leo: Greenlights Execute
Leo: Removes PROJECT SHELL banner
```

**Output:** Execute authorized

---

### Phase: Execute (The FORGE Cycle)

```
┌─────────────────────────────────────────────────┐
│                 THE FORGE CYCLE                  │
│                 (runs dozens of times)           │
└─────────────────────────────────────────────────┘

1. Leo: "Start PR-01"
     ↓
2. CC: Creates branch feat/pr-01-[name]
     ↓
3. CC: Writes task brief → ai_prompts/active/
     ↓
4. Leo: Hands brief to Cursor
     ↓
5. Cursor: Implements per brief
     ↓
6. Cursor: Runs Sacred Four, hands off to CC
     ↓
7. CC: Verifies implementation
     ↓
8. CC: Fixes <5 lines OR returns >5 lines
     ↓
9. CC: Creates PR
     ↓
10. Leo: Reviews, approves, merges
     ↓
11. CC: Archives brief → ai_prompts/completed/
     ↓
12. CC: Updates build-plan.md
     ↓
[Repeat for PR-02, PR-03, ...]
```

**Output:** Working software, one PR at a time

---

## Part 5: Agent Communication Topology

```
                    ┌─────────────────────────────┐
                    │           LEO               │
                    │     (Human Lead)            │
                    │  Greenlight & Authority     │
                    └──────────┬──────────────────┘
                               │
         ┌─────────────────────┼─────────────────────┐
         │                     │                     │
         ▼                     ▼                     ▼
┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐
│     JORDAN      │  │       CP        │  │       CC        │
│   (Strategist)  │◄►│  (Spec Author)  │─►│  (Quality Gate) │
│    ChatGPT      │  │   Claude.ai     │  │   Claude Code   │
└─────────────────┘  └─────────────────┘  └────────┬────────┘
                                                   │
                                                   ▼
                                         ┌─────────────────┐
                                         │     CURSOR      │
                                         │ (Implementation)│
                                         │   Cursor IDE    │
                                         └─────────────────┘
```

### Communication Rules

| From | To | Allowed? | Notes |
|------|-----|----------|-------|
| Leo | Anyone | YES | Can engage any agent |
| Jordan | CP | YES | Through Leo, bidirectional |
| Jordan | CC | NO | No direct communication |
| Jordan | Cursor | NO | No direct communication |
| CP | CC | ONE-WAY | Specs flow to CC (read-only) |
| CP | Cursor | NO | No direct communication |
| CC | Cursor | YES | Tight cycle (briefs ↔ code) |

---

## Part 6: Key Files Quick Reference

### For Jordan

| Need | Location |
|------|----------|
| FORGE methodology | `FORGE-Method/core/forge-core.md` |
| Your operating guide | `FORGE-Method/agents/forge-jordan-operating-guide.md` |
| Frame template | `FORGE-Method/templates/forge-template-frame.md` |
| Setup instructions | `FORGE-Method/starter-kit/chatgpt/PROJECT_SETUP.md` |

### For CP

| Need | Location |
|------|----------|
| Constitutional templates | `FORGE-Method/templates/forge-template-*.md` |
| Your operating rules | `FORGE-Method/starter-kit/claude_ai/custom-instructions-cp.md` |
| Document hierarchy | `FORGE-Method/core/forge-operations.md` |

### For CC

| Need | Location |
|------|----------|
| Project identity | `[project]/CLAUDE.md` |
| Constitution | `[project]/docs/constitution/` |
| Build plan | `[project]/docs/build-plan.md` |
| Current brief | `[project]/ai_prompts/active/` |
| Cursor rules | `[project]/.cursor/rules/forge-cc.mdc` |

### For Cursor

| Need | Location |
|------|----------|
| Task brief | `[project]/ai_prompts/active/` |
| Specs reference | `[project]/docs/constitution/` |
| Operating rules | `[project]/.cursor/rules/forge-sd.mdc` |

---

## Part 7: What Makes This Work

### The Speed Secret

> "Teams using FORGE report orders-of-magnitude faster implementation — not because agents work faster, but because they never stop to decide."

- All decisions made in Frame/Refine
- Execute is mechanical
- No architectural debates during coding

### The Safety Model

1. **Constitution is locked** — No scope creep
2. **Lanes are enforced** — No role confusion
3. **Human greenlight required** — No autonomous escalation
4. **Sacred Four verification** — No broken builds

### The Handoff Clarity

- Everything through files, not conversation
- One active brief at a time
- Archive before starting new work
- Build plan is single source of truth

---

## Part 8: Repositories Summary

| Repository | URL | Purpose |
|------------|-----|---------|
| FORGE-Method | `Knight-Ventures-Inc/FORGE-Method` | Canon + Starter Kit |
| FORGE-SD Template | `Knight-Ventures-Inc/forge-sd-template` | What you clone |

### Current Status

- **FORGE-Method:** `feat/starter-kit` branch ready for merge
- **FORGE-SD:** Main branch updated and pushed

---

## Conclusion

The system is now wired so that:

1. **New users** can cold-start in ~1 hour (learn + setup + clone)
2. **Existing team** can launch projects in ~15 minutes (clone + customize + constitute)
3. **CC can "just work"** after `git clone` + constitutional docs
4. **No agent redefines FORGE** — all consume by reference

Jordan, this report reflects the architecture you specified. The "two-layer model" is implemented exactly as you described:
- FORGE-Method = specification
- FORGE-SD = reference implementation

The bar is met: `git clone` is enough for CC to immediately operate correctly.

---

*Report generated by CC (Claude Code)*
*2026-01-08*

*This project follows The FORGE Method(TM) — theforgemethod.org*
