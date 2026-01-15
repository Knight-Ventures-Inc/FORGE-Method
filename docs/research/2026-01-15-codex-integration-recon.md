# Recon Report: Codex Cloud Integration into FORGE

**Date:** 2026-01-15
**Environment:** iMac Pro + FORGE ecosystem repos
**Status:** Complete — Ready for Change Plan execution
**Audience:** Leo, Jordan, CC

---

## Executive Summary

1. **Codex Cloud** (OpenAI Codex in ChatGPT) is being added as a **recon-only remote agent** for mobile/web use
2. **CP deprecation** confirmed: Cloud Claude Projects → local `project-architect` agents per repo
3. **Four repos** require updates: FORGE-Method, forge-project-template, forge-genesis-vault, Vantage
4. **No Codex documentation exists** — role, constraints, and handoff packet schema must be created
5. **Role definitions are stale** — still reference "CP (Claude Project)" in multiple locations
6. **docs/recons/** directory missing from forge-project-template and Vantage
7. **Handoff packet schema** needs standardization with `scope_lock` block for Codex
8. **Environment fingerprint** requirement for Codex sessions should be established
9. **Best practices checklist** (landing page, auth, nav, tests) does not exist in template
10. **Parking lot discipline** is consistent across repos — no changes needed

---

## What Exists Today (By Repo)

### FORGE-Method (`~/kv-projects/FORGE-Method/`)

| File | Purpose | Status |
|------|---------|--------|
| `core/forge-core.md` | Tool-agnostic methodology | ✅ Good (generic roles) |
| `core/forge-operations.md` | Execution manual | ✅ Good (generic roles) |
| `agents/forge-agent-roles-handoffs.md` | Agent definitions | ⚠️ **STALE** — references "CP (Claude Project)" |
| `templates/agents/project-architect.template.md` | Per-repo agent template | ✅ Good |
| `02_execution/recons/RECON-TEMPLATE.md` | Recon report template | ✅ Good |
| `docs/agents/README.md` | Agent quick reference | ✅ Good |

**No Codex Cloud documentation exists.**

### forge-project-template (`~/kv-projects/forge-project-template/`)

| File | Purpose | Status |
|------|---------|--------|
| `CLAUDE.md` | Project identity for CC | ⚠️ References "CP" in Agent Lanes |
| `ai_prompts/templates/task-brief-template.md` | Task brief template | ✅ Good |
| `ai_prompts/templates/handoff-template.md` | Cursor handoff template | ✅ Good |
| `docs/parking-lot/README.md` | Parking lot protocol | ✅ Good |
| `docs/recons/` | Recon reports directory | ❌ **MISSING** |
| `AGENTS.md` | Agent definitions | ❌ **MISSING** |

**No Codex Cloud handoff packet template exists.**

### forge-genesis-vault (`~/kv-projects/forge-genesis-vault/`)

| File | Purpose | Status |
|------|---------|--------|
| `05_project-genesis/genesis-custom-instructions.md` | Jordan's instructions | ⚠️ **STALE** — references CP extensively |
| `02_spawn_system/spawn-specs/spawn-cp.md` | CP spawn guide | ⚠️ **STALE** — describes cloud CP, not local agents |
| `02_spawn_system/spawn-specs/spawn-cc.md` | CC spawn guide | ✅ Good |
| `00_index/vault-map.md` | Vault index | May need Codex section |

**No Codex Cloud role or operating instructions exist.**

### Vantage (`~/kv-projects/vantage/`)

| File | Purpose | Status |
|------|---------|--------|
| `CLAUDE.md` | Project identity for CC | ⚠️ References "CP (Claude.ai)" in Team Structure |
| `AGENTS.md` | Agent definitions | ⚠️ **STALE** — lists "CP" as Claude Project |
| `.claude/agents/project-architect.md` | Local architect agent | ✅ Installed and good |
| `docs/parking-lot/` | Parking lot | ✅ Good |
| `docs/recons/` | Recon reports | ❌ **MISSING** |

---

## Gaps and Inconsistencies

### Gap 1: CP → Project-Architect Transition Not Reflected

**Affected Files:**
- `FORGE-Method/agents/forge-agent-roles-handoffs.md` — Line 19 says "Specification Author: CP (Claude Project)"
- `forge-genesis-vault/05_project-genesis/genesis-custom-instructions.md` — Multiple CP references
- `forge-genesis-vault/02_spawn_system/spawn-specs/spawn-cp.md` — Entire file describes cloud CP
- `Vantage/AGENTS.md` — Line 18 says "CP: Claude (Project)"
- `Vantage/CLAUDE.md` — Line 60 says "CP: Specs (Claude.ai)"

**Impact:** New users will be confused about whether to use cloud CP or local project-architect.

### Gap 2: Codex Cloud Role Not Defined Anywhere

**Missing:**
- Role definition in FORGE-Method
- Operating constraints (recon-only, no writes)
- Handoff packet schema
- Environment fingerprint requirement
- Escalation rules

**Impact:** Codex usage will be inconsistent, risk of unauthorized writes.

### Gap 3: docs/recons/ Directory Missing

**Affected Repos:**
- `forge-project-template/` — No `docs/recons/` directory
- `Vantage/` — No `docs/recons/` directory

**Impact:** Nowhere for Codex recon reports to land.

### Gap 4: No Standard App Best Practices Checklist

**Missing items:**
- Landing/home page requirements
- Auth flow basics (sign-in, sign-up, forgot password)
- Navigation structure
- Environment config checklist
- Pre-PR verification sequence

**Impact:** Each project reinvents these basics.

### Gap 5: Handoff Packet Schema Not Standardized for Codex

**Missing:**
- `scope_lock` block (recon_only, no_code_changes, docs_only)
- Environment fingerprint header
- Date verification requirement

---

## Recommended Canonical Definitions

### Tool-Agnostic Roles (FORGE-Method)

Update `agents/forge-agent-roles-handoffs.md` with new agent model:

| Role | Tool-Agnostic Name | Knight Ventures Implementation |
|------|--------------------|-------------------------------|
| Human Lead | Human Lead | Leo |
| Strategist | Strategist | Jordan (ChatGPT) |
| Specification Author | Spec Author / Architect | `project-architect` (local per-repo) |
| Quality Gate | Quality Gate | CC (Claude Code) |
| Implementation Engine | Implementation Engine | Cursor |
| **NEW: Remote Recon** | Recon Agent | Codex Cloud (ChatGPT) |

### Tool-Specific Procedures (forge-project-template)

Add to template:
- `docs/recons/README.md` — Recon reports landing zone
- `ai_prompts/templates/codex-recon-packet.template.md` — Codex handoff packet template
- Update `CLAUDE.md` to reference project-architect instead of CP

### Jordan Memory Refresh (forge-genesis-vault)

Create/update:
- `02_spawn_system/spawn-specs/spawn-codex.md` — Codex operating instructions
- Update `genesis-custom-instructions.md` to reflect new agent model
- Update or deprecate `spawn-cp.md`

---

## Codex Cloud Policy (Canonical)

### Role Definition

**Codex Cloud** is a remote reconnaissance agent operated via ChatGPT (iOS app or web). It performs codebase analysis and produces handoff packets for iMac Pro execution.

### Capabilities

| Capability | Allowed | Notes |
|------------|---------|-------|
| Read GitHub repo contents | ✅ | Core purpose |
| Analyze code and docs | ✅ | Core purpose |
| Produce recon reports | ✅ | Output to `docs/recons/` |
| Create handoff packets | ✅ | Output to `ai_prompts/active/` |
| Commit docs-only to staging | ⚠️ Opt-in | Explicit authorization required |
| Modify source code | ❌ Never | Hard constraint |
| Modify constitutional docs | ❌ Never | Hard constraint |
| Create PRs | ❌ Never | CC only |
| Run builds/tests | ❌ N/A | No execution environment |

### Required Environment Verification

Every Codex session must output at start:

```
---
ENVIRONMENT: Codex Cloud (ChatGPT)
WRITE_PERMISSION: RECON_ONLY
REPO: [repo-name]
DATE: [YYYY-MM-DD - verified]
---
```

### Output Artifacts

| Artifact | Location | Purpose |
|----------|----------|---------|
| Recon Report | `docs/recons/YYYY-MM-DD-<topic>.md` | Investigation findings |
| Handoff Packet | `ai_prompts/active/PACKET-<id>-<topic>.md` | Staged for CC execution |

### No-Write Rule + Escalation

1. Codex must NOT modify any code files (`.ts`, `.tsx`, `.js`, `.py`, etc.)
2. Codex must NOT modify constitutional docs
3. If changes are needed, Codex creates a handoff packet tagged `REQUIRES: CC` or `REQUIRES: forge-maintainer`
4. CC or forge-maintainer executes the changes on iMac Pro

---

## Parking Lot Items (Out of Scope for This Task)

- **Best Practices Checklist:** Creating a standard "always include" checklist for new projects is valuable but separate from Codex integration
- **FORGE-Method CLAUDE.md:** The methodology repo lacks a CLAUDE.md file; could be added but is scope creep for this task
- **docs/governance/ directory:** FORGE-Method has no governance directory; not needed for Codex integration
- **Global Codex agent:** Codex runs in ChatGPT, not as a CC agent — no `~/.claude/agents/codex.md` needed

---

## Authors

- **Primary Investigator:** CC (Claude Code)
- **Task Requester:** Jordan + Leo
- **Approving Authority:** Leo (Human Lead)

---

*This is part of The FORGE Method(TM) — theforgemethod.org*
