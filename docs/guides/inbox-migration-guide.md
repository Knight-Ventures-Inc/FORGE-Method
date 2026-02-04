# Inbox-First Migration Guide

**Version:** 2.0
**Date:** 2026-02-03

---

## Overview

This guide helps existing projects migrate from legacy `ai_prompts/` workflows to the canonical inbox-driven workflow.

**For new projects:** Inbox-driven workflow is the default. The `ai_prompts/` directory no longer exists in `forge-project-template/`.

**For existing projects:** Migration is recommended but not mandatory. Legacy projects can continue using `ai_prompts/` if already established.

---

## What Changed

As of February 2026, FORGE adopted inbox-driven workflow as the canonical pattern:

| Pattern | Status | Use Case |
|---------|--------|----------|
| `inbox/` | **Canonical** | All new projects |
| `ai_prompts/` | **Deprecated** | Legacy projects only |

Key differences:

| Feature | Legacy (ai_prompts) | Canonical (inbox) |
|---------|---------------------|-------------------|
| Discovery input | Task briefs | `inbox/00_drop/` folders |
| Planning | Task briefs | Product Intent + Architecture Packets |
| Agent flow | CC → Cursor | Product Strategist → Project Architect → CC |
| Artifacts | Single task brief | Structured folder with multiple artifacts |

---

## When to Migrate

**Migrate if:**
- Starting new feature work
- Discovery phase is upcoming
- Team wants structured intake
- Project needs clearer Frame → Execute handoff

**Don't migrate if:**
- Mid-sprint with active work
- Small bug fixes only
- Project is near completion
- Legacy workflow is working well

---

## Migration Steps

### Step 1: Add Inbox Structure

```bash
cd your-project
mkdir -p inbox/{00_drop,10_product-intent,20_architecture-plan}
```

Copy README.md from forge-project-template:
```bash
cp /path/to/forge-project-template/inbox/README.md inbox/
```

### Step 2: Update CLAUDE.md

Replace any `ai_prompts/` references with inbox workflow:

```markdown
## Inbox-Driven Workflow

Discovery flows through structured phases:

| Phase | Location | Agent |
|-------|----------|-------|
| Discovery | `inbox/00_drop/<slug>/` | Human |
| Product Intent | `inbox/10_product-intent/<slug>/` | Product Strategist |
| Architecture | `inbox/20_architecture-plan/<slug>/` | Project Architect |

See `inbox/README.md` for detailed workflow.
```

### Step 3: Update Cursor Rules

Replace `forge-cc.mdc` and `forge-sd.mdc` with current versions from forge-project-template:

```bash
cp /path/to/forge-project-template/.cursor/rules/*.mdc .cursor/rules/
```

### Step 4: Migrate Active Work

For any work-in-progress:

1. Complete current task brief cycle
2. Archive completed briefs
3. Start new features in `inbox/00_drop/`

### Step 5: Archive Legacy Directory (Optional)

Once all active work is complete:

```bash
# Keep for reference but mark as legacy
mv ai_prompts ai_prompts_legacy
echo "# Legacy - Use inbox/ for new work" > ai_prompts_legacy/README.md
```

Or remove entirely:
```bash
rm -rf ai_prompts
```

---

## Coexistence Period

During transition, both patterns can run:

| New work | Use `inbox/` → Product Strategist → Project Architect |
| Active briefs | Complete via legacy `ai_prompts/` pattern |
| Bug fixes | Can use either pattern |

**Goal:** All new features start in `inbox/` even if some legacy work continues.

---

## Verification Checklist

After migration:

- [ ] `inbox/` directory exists with correct structure
- [ ] `CLAUDE.md` references inbox workflow
- [ ] Cursor rules updated to current version
- [ ] Team understands new workflow
- [ ] First discovery packet created as test

---

## Relationship to Constitutional Docs

| Artifact | Phase | Location |
|----------|-------|----------|
| Discovery materials | Frame | `inbox/00_drop/` |
| Product Intent Packet | Frame | `inbox/10_product-intent/` |
| Architecture Packet | Orchestrate | `inbox/20_architecture-plan/` |
| PRODUCT.md | Refine | `docs/constitution/` |

Packets **precede and inform** constitutional docs:
- Packets are Frame/Orchestrate phase artifacts
- Constitutional docs are refined from packet insights
- Both are preserved as historical record

---

## Questions?

See:
- `forge-project-template/inbox/README.md` — Detailed inbox workflow
- `FORGE-Method/core/forge-operations.md` — Part 7: Inbox-Driven Workflow
- `FORGE/CLAUDE.md` — Umbrella governance

---

*This guide is part of The FORGE Method™*
