# Change Plan: Codex Cloud Integration

**Date:** 2026-01-15
**Status:** PROPOSED — Awaiting PROCEED
**Prerequisite:** Review `2026-01-15-codex-integration-recon.md` first

---

## Summary

This plan implements Codex Cloud integration and CP → project-architect transition across four repos:
1. **forge-project-template** — Template updates (highest priority, affects all future projects)
2. **FORGE-Method** — Tool-agnostic role model + Codex documentation
3. **forge-genesis-vault** — Jordan knowledge refresh
4. **Vantage** — Live project governance refresh

**Execution Order:** 1 → 2 → 3 → 4 (template first, then canon, then vault, then live project)

---

## Repo 1: forge-project-template

### Files to CREATE

| File | Purpose |
|------|---------|
| `docs/recons/README.md` | Recon reports landing zone |
| `ai_prompts/templates/codex-recon-packet.template.md` | Codex handoff packet template |

### Files to UPDATE

| File | Change |
|------|--------|
| `CLAUDE.md` | Update Agent Lanes table: CP → project-architect; add Codex recon role |

### What to Add/Change

**`docs/recons/README.md`:**
- Purpose explanation (recon reports from Codex or other investigation)
- File naming convention: `YYYY-MM-DD-<topic>.md`
- Governance (who authors, who reviews)

**`ai_prompts/templates/codex-recon-packet.template.md`:**
- Frontmatter with `packet_id`, `created_by`, `created_date`, `target_executor`
- `scope_lock` block (recon_only, no_code_changes, docs_only)
- Sections: Objective, Read Paths, Write Paths, Steps, Definition of Done, Verification

**`CLAUDE.md` Agent Lanes table (lines 67-74):**
- Change `Spec Author: CP (Claude Project)` → `Architect: project-architect (local agent)`
- Add row for Codex Cloud: `Recon Agent | Codex Cloud | Remote recon | Does NOT modify code`

### Acceptance Criteria

- [ ] `docs/recons/README.md` exists with purpose, naming convention, governance
- [ ] `ai_prompts/templates/codex-recon-packet.template.md` exists with scope_lock block
- [ ] `CLAUDE.md` Agent Lanes table updated (no CP references)
- [ ] All verification passes (no code, just docs — no verification needed)

### Effort Estimate

**S (Small)** — 3 files, all documentation

### Risks and Mitigation

| Risk | Mitigation |
|------|------------|
| Template changes don't propagate to existing projects | Document in CHANGELOG; create separate Vantage packet |

---

## Repo 2: FORGE-Method

### Files to CREATE

| File | Purpose |
|------|---------|
| `agents/codex-cloud-operating-guide.md` | Codex role definition and constraints |

### Files to UPDATE

| File | Change |
|------|--------|
| `agents/forge-agent-roles-handoffs.md` | Add Codex Cloud role; update CP → project-architect |

### What to Add/Change

**`agents/codex-cloud-operating-guide.md` (NEW):**
- Role definition (recon-only remote agent)
- Capabilities matrix (what Codex can/cannot do)
- Environment fingerprint requirement
- Output locations (docs/recons/, ai_prompts/active/)
- No-write rule and escalation protocol
- Handoff packet schema reference

**`agents/forge-agent-roles-handoffs.md`:**
- Line 19: Change "Specification Author | CP (Claude Project)" → "Architect | project-architect (local)"
- Add new row in The Team table for Codex Cloud
- Update Communication Topology diagram to show Codex → handoff packets → CC
- Add "Supporting Role" entry for Codex Cloud

### Acceptance Criteria

- [ ] `agents/codex-cloud-operating-guide.md` exists with complete role definition
- [ ] `forge-agent-roles-handoffs.md` no longer references "CP (Claude Project)"
- [ ] Communication topology includes Codex Cloud
- [ ] Codex constraints are explicit (recon-only, no writes)

### Effort Estimate

**M (Medium)** — 1 new file, 1 significant update

### Risks and Mitigation

| Risk | Mitigation |
|------|------------|
| Breaking existing documentation links | Search for "CP" references across all files first |
| Diagram update complexity | Keep diagram simple, add Codex as separate branch |

---

## Repo 3: forge-genesis-vault

### Files to CREATE

| File | Purpose |
|------|---------|
| `02_spawn_system/spawn-specs/spawn-codex.md` | Codex operating instructions for Jordan |

### Files to UPDATE

| File | Change |
|------|--------|
| `05_project-genesis/genesis-custom-instructions.md` | Reflect new agent model; add Codex awareness |
| `02_spawn_system/spawn-specs/spawn-cp.md` | Deprecate or redirect to project-architect |
| `00_index/vault-map.md` | Add Codex entry |

### What to Add/Change

**`02_spawn_system/spawn-specs/spawn-codex.md` (NEW):**
- What Codex is (OpenAI Codex in ChatGPT)
- When to use (mobile, remote, Leo away from iMac Pro)
- What Codex produces (recon reports, handoff packets)
- What Codex cannot do (modify code, create PRs)
- Sample prompts for Jordan to give Codex
- Handoff flow (Codex → GitHub → iMac Pro → CC)

**`genesis-custom-instructions.md`:**
- Update agent table: Add Codex Cloud role
- Update domain/agents section to reflect project-architect
- Add "Codex Invocation" spawn type or note
- Keep CP references only for legacy context or remove entirely

**`spawn-cp.md`:**
- Add deprecation notice at top
- Redirect to `project-architect.template.md` in FORGE-Method
- Or rename/repurpose to "spawn-project-architect.md"

**`vault-map.md`:**
- Add entry for `spawn-codex.md`

### Acceptance Criteria

- [ ] `spawn-codex.md` exists with complete operating instructions
- [ ] `genesis-custom-instructions.md` reflects new agent model
- [ ] `spawn-cp.md` marked deprecated or converted
- [ ] Vault map updated

### Effort Estimate

**M (Medium)** — 1 new file, 3 updates

### Risks and Mitigation

| Risk | Mitigation |
|------|------------|
| Jordan's knowledge base needs refresh | Clear deprecation notices; Jordan reads new docs first |
| Breaking Jordan's workflows | Test with Jordan before finalizing |

---

## Repo 4: Vantage

### Files to CREATE

| File | Purpose |
|------|---------|
| `docs/recons/README.md` | Recon reports landing zone |

### Files to UPDATE

| File | Change |
|------|--------|
| `CLAUDE.md` | Update Team Structure table; remove CP references |
| `AGENTS.md` | Update agent definitions; add Codex; remove CP |

### What to Add/Change

**`docs/recons/README.md` (NEW):**
- Same structure as forge-project-template version
- Project-specific: reference Vantage governance

**`CLAUDE.md` Team Structure table (lines 55-60):**
- Remove or update "CP | Specs (Claude.ai)" row
- Add "project-architect | Local governance agent"
- Optionally add "Codex Cloud | Remote recon (when used)"

**`AGENTS.md` (lines 14-20):**
- Change "CP | Claude (Project)" → "project-architect | Local (.claude/agents/)"
- Update Governance section approval chain
- Add Codex Cloud role if appropriate

### Acceptance Criteria

- [ ] `docs/recons/README.md` exists
- [ ] `CLAUDE.md` no longer references "CP (Claude.ai)"
- [ ] `AGENTS.md` reflects local project-architect
- [ ] Consistency between CLAUDE.md and AGENTS.md

### Effort Estimate

**S (Small)** — 1 new file (small), 2 updates

### Risks and Mitigation

| Risk | Mitigation |
|------|------------|
| Vantage has open PR work | Coordinate timing with Leo; don't disrupt active PR |
| Existing workflows reference CP | Search and update any references in ai_prompts/ |

---

## Execution Summary

| Order | Repo | Effort | Files Changed |
|-------|------|--------|---------------|
| 1 | forge-project-template | S | 3 (2 create, 1 update) |
| 2 | FORGE-Method | M | 2 (1 create, 1 update) |
| 3 | forge-genesis-vault | M | 4 (1 create, 3 update) |
| 4 | Vantage | S | 3 (1 create, 2 update) |

**Total:** 12 file operations across 4 repos

---

## Verification Steps

After all changes:

1. **Search for "CP" references:**
   ```bash
   grep -r "CP" ~/kv-projects/FORGE-Method --include="*.md" | grep -v "archive"
   grep -r "CP" ~/kv-projects/forge-project-template --include="*.md"
   grep -r "Claude Project" ~/kv-projects/forge-genesis-vault --include="*.md"
   grep -r "CP" ~/kv-projects/vantage --include="*.md" | grep -v node_modules
   ```

2. **Verify new files exist:**
   ```bash
   ls ~/kv-projects/forge-project-template/docs/recons/README.md
   ls ~/kv-projects/FORGE-Method/agents/codex-cloud-operating-guide.md
   ls ~/kv-projects/forge-genesis-vault/02_spawn_system/spawn-specs/spawn-codex.md
   ls ~/kv-projects/vantage/docs/recons/README.md
   ```

3. **Test Jordan refresh:** Ask Jordan to describe the current agent model — should mention project-architect and Codex, not CP.

---

*Change Plan for Codex Cloud Integration — FORGE Method*
