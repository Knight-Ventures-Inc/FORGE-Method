# Inbox-First Migration Guide

**Version:** 1.0
**Date:** 2026-02-03

---

## Overview

This guide helps projects migrate from ai_prompts-only workflows to inbox-first workflows. Migration is **optional** — both patterns can coexist.

---

## When to Migrate

Consider adopting inbox-first if your project has:

- Frequent discovery or pivots requiring structured intake
- Need for external stakeholder visibility into product thinking
- Desire to separate Frame (discovery) from Execute (implementation)
- Multiple features in flight requiring clear handoff points

**You do NOT need to migrate if:**
- Your current ai_prompts workflow is working well
- You primarily do Execute-phase work (bug fixes, features with clear specs)
- Your team prefers task-brief-driven workflows

---

## Prerequisites

Before migrating:

1. [ ] Project uses forge-project-template structure
2. [ ] Team understands Frame vs Execute distinction
3. [ ] Human Lead ready to route Product Strategist output
4. [ ] Current work-in-progress completed or paused

---

## Migration Steps

### Step 1: Copy Inbox Structure

Copy the inbox directory from forge-project-template:

```bash
cp -r /path/to/forge-project-template/inbox /path/to/your-project/
```

This creates:
```
your-project/
└── inbox/
    ├── README.md
    ├── 00_drop/
    │   └── .template/
    └── 10_product-intent/
        └── .template/
```

### Step 2: Update CLAUDE.md

Add inbox workflow references to your project's CLAUDE.md:

```markdown
## Inbox-Driven Workflow (Frame Phase)

The Product Strategist uses an inbox-driven workflow for Frame phase work.

### Structure
- `inbox/00_drop/<slug>/` — Discovery input (human writes here)
- `inbox/10_product-intent/<slug>/` — Product Intent Packets (agent writes here)

### Workflow
1. Human drops discovery materials in `inbox/00_drop/<slug>/`
2. Product Strategist processes and asks clarifying questions
3. Output appears in `inbox/10_product-intent/<slug>/`
4. Human Lead routes to next phase
```

### Step 3: Create First Discovery Packet

Test the workflow with a real feature:

```bash
mkdir -p inbox/00_drop/my-feature/threads inbox/00_drop/my-feature/assets
```

Create `inbox/00_drop/my-feature/README.md`:
```markdown
# Discovery: My Feature

## Summary
Brief description of what you want to build.

## Problem
What problem does this solve?

## Materials
- See `threads/` for notes
- See `assets/` for sketches
```

### Step 4: Process with Product Strategist

Invoke Product Strategist to process the discovery:

```
"Process the discovery packet in inbox/00_drop/my-feature/"
```

The agent will:
1. Read your materials
2. Ask clarifying questions (up to 3 rounds)
3. Produce Product Intent Packet in `inbox/10_product-intent/my-feature/`

### Step 5: Review and Route

Review the output packet, then route to next phase:
- If ready for technical planning → Project Architect
- If needs more discovery → Back to Product Strategist
- If clear enough for immediate implementation → Execute phase

---

## Coexistence Notes

**inbox/ does NOT replace ai_prompts/**

| Workflow | Phase | Use For |
|----------|-------|---------|
| `inbox/` | Frame | Discovery, product intent, feature definition |
| `ai_prompts/` | Execute | Task briefs, implementation instructions |

Both workflows run in the same project:
- New features start in `inbox/00_drop/`
- After Frame phase, implementation continues via `ai_prompts/active/`

---

## Rollback

If inbox-first doesn't work for your project:

1. Simply stop using `inbox/`
2. Continue with `ai_prompts/` workflow
3. Optionally delete `inbox/` directory

No breaking changes to existing workflows.

---

## Relationship to PRODUCT.md

| Artifact | Purpose | Location |
|----------|---------|----------|
| Product Intent Packet | Frame-phase discovery output | `inbox/10_product-intent/` |
| PRODUCT.md | Refined constitutional doc | `docs/constitution/` |

Product Intent Packets **precede and inform** PRODUCT.md:
- Packets are historical discovery record
- PRODUCT.md is current authority
- Multiple packets may exist over project lifecycle

---

## Questions?

See:
- `forge-project-template/inbox/README.md` — Detailed inbox workflow
- `FORGE-Method/agents/forge-product-strategist-guide.md` — Product Strategist operating guide
- `FORGE/CLAUDE.md` — Umbrella governance with lane definitions

---

*This guide is part of The FORGE Method™*
