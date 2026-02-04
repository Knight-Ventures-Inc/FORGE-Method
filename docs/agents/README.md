<!-- Audience: Public -->

# FORGE Global Agents

Quick reference for the global agents that support FORGE methodology.

---

## Agent Overview

| Agent | Purpose | Location | When to Use |
|-------|---------|----------|-------------|
| **forge-architect** | Spawn new projects | `~/.claude/agents/forge-architect.md` | Creating a new FORGE repo from a project brief |
| **forge-maintainer** | Maintain existing repos | `~/.claude/agents/forge-maintainer.md` | Updating FORGE-Method, templates, or vault |
| **project-architect** | Govern one project | `[project]/.claude/agents/project-architect.md` | Sprint planning, scope enforcement, task briefs |

---

## forge-architect (Spawner)

**Mission:** Create new FORGE projects from scratch.

**Inputs:** Project brief with name, domain, stack, features, constraints.

**Outputs:**
- Complete folder structure
- CLAUDE.md with project identity
- Constitutional doc templates
- Project-specific architect agent
- First task brief

**Invoke:**
```
"Start a new FORGE project called X"
```

**After completion:** Restart Claude Code, cd to project, invoke project-architect.

---

## forge-maintainer (Ops)

**Mission:** Maintain and upgrade existing FORGE infrastructure.

**Scope:**
- `FORGE-Method` (canon)
- `forge-project-template` (scaffold)
- `forge-genesis-vault` (internal ops)
- Additional repos only with explicit authorization

**Modes:**
- `MODE=MAINTAIN` — Plan, approval gate, execute, report
- `MODE=AUDIT` — Read-only drift detection

**Workflow:**
1. Phase 0: Recon + Plan (no writes)
2. Wait for `PROCEED`
3. Phase 1: Execute sequentially
4. Phase 2: Final report

**Invoke:**
```
"Update the parking-lot template across all FORGE repos"
"MODE=AUDIT — Check vantage alignment with template"
```

**Safety:** Requires explicit `PROCEED` before any writes.

---

## project-architect (Per-Project)

**Mission:** Govern a specific project through FORGE phases.

**Location:** Created by forge-architect inside each project at `.claude/agents/project-architect.md`

**Responsibilities:**
- Own constitutional docs (PRODUCT.md, TECH.md, GOVERNANCE.md)
- Plan sprints and create task briefs
- Enforce scope ("that's out of scope")
- Track phase, sprint, and PR state

**Invoke:**
```
cd ~/kv-projects/[project]
"Invoke project-architect to plan the next sprint"
```

---

## Decision Tree

```
Need to create a new project?
  └─> forge-architect

Need to update FORGE-Method / templates / vault?
  └─> forge-maintainer

Need to plan sprints / enforce scope for one project?
  └─> project-architect (inside that project)

Need to execute task briefs / write code?
  └─> CC (Claude Code) or Cursor
```

---

## Quick Commands

| Goal | Command |
|------|---------|
| New project | "Start a new FORGE project" |
| Update templates | "Update X across FORGE repos" |
| Check drift | "MODE=AUDIT — check [project] alignment" |
| Sprint planning | "Invoke project-architect" (from project dir) |

---

## Optional Extensions

Some projects adopt optional FORGE extensions that add specialized capabilities.

### FORGE AI Interface (FAI)

If a project adopts FAI (see `docs/extensions/fai-overview.md`), it adds an AI interface layer for:
- Knowledge-based Q&A about the application
- Action execution with RBAC mirroring
- Structured feedback capture
- Multimodal intake (screenshots)

**FAI is an interface layer, not an autonomous agent.** FAI does not modify code, create PRs, or merge changes.

Projects using FAI will have:
- `docs/constitution/FAI.md` — FAI configuration
- FAI-generated entries in `docs/parking-lot/`
- FAI feedback routed to `inbox/00_drop/` for standard workflow processing

See the [FAI Overview](../extensions/fai-overview.md) for adoption criteria.

---

*FORGE Agents — theforgemethod.org*
