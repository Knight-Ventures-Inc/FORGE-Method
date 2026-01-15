<!-- Audience: Public -->

# FORGE-Method Changelog

All notable changes to the FORGE methodology canon.

Format: `[YYYY-MM-DD] Title` with summary, files touched, and impact scope.

---

## [2026-01-15] Standardize project-architect template with retrofit support

**Summary:** Created canonical project-architect template with standardized output contracts, lane separation rules, and retrofit capability for existing repos.

**Files touched:**
- `templates/agents/project-architect.template.md` (created) — New canonical template location
- `templates/forge-template-project-architect.md` (modified) — Marked DEPRECATED, points to new location
- `~/.claude/agents/forge-architect.md` (modified) — Added RETROFIT MODE section
- `~/.claude/agents/forge-maintainer.md` (modified) — Added scoped agent installation capability
- `CHANGELOG.md` (updated)

**Impact:** Public canon — standardized per-project governance agent across all FORGE projects.

**Details:**
- New template at `templates/agents/` establishes single source of truth
- Output contract: plans/FEATURE-*.md, PR breakdowns, recon reports, decision records
- Lane separation: project-architect writes plans/docs only, never code
- Operating sequence: Recon → Clarify → Build Plan → PR Breakdown → Stop
- forge-architect gains RETROFIT MODE for installing into existing repos
- forge-maintainer scoped to `.claude/agents/*` and `docs/parking-lot/*` only during installs

---

## [2026-01-15] Add forge-maintainer global agent

**Summary:** Introduced forge-maintainer agent for maintaining/upgrading existing FORGE repos with controlled cross-repo rollouts.

**Files touched:**
- `~/.claude/agents/forge-maintainer.md` (created)
- `~/.claude/agents/forge-architect.md` (updated — added scope clarification)
- `docs/agents/README.md` (created)
- `docs/forge-architect-explainer.md` (created earlier)
- `CHANGELOG.md` (created)

**Impact:** Public canon — new agent architecture for FORGE operations.

**Details:**
- forge-maintainer handles maintenance/upgrades with mandatory PROCEED gate
- forge-architect remains focused on spawning new projects only
- Added docs/agents/README.md as quickstart reference for all global agents
- Established changelog protocol for future FORGE-Method updates

---
