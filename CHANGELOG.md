<!-- Audience: Public -->

# FORGE-Method Changelog

All notable changes to the FORGE methodology canon.

Format: `[YYYY-MM-DD] Title` with summary, files touched, and impact scope.

---

## [2026-01-24] Platform-Level Stakeholder Model (v1.1.0)

**Summary:** Clarified the platform vs tenant plane distinction for stakeholders in the FORGE identity model. Stakeholder is now explicitly defined as a platform-level actor, not a tenant role.

**Files touched:**
- `docs/extensions/auth-rbac.md` (modified) — Added platform vs tenant planes; moved stakeholder to platform level
- `docs/extensions/stakeholder-interface.md` (modified) — Added supra-tenant context; clarified platform plane operation
- `CHANGELOG.md` (updated)

**Impact:** Public canon — clarifies identity model for all FORGE software projects.

**Details:**

### Added
- Platform vs tenant plane distinction in auth-rbac.md
- Platform memberships concept (separate from tenant memberships)
- Dual-Plane Human Identity Pattern documentation
- Supra-tenant context clarification in stakeholder-interface.md
- Session invariant: one plane per session, no cross-visibility

### Changed
- Stakeholder clarified as platform-level actor, not tenant role
- Four tenant roles reduced to three (Owner, Admin, Member)
- Stakeholder Interface scoping clarified as platform-level
- Shared Visibility section updated for platform-wide scope

### Key Concepts
- **Platform Plane:** System-wide context for stakeholders (Stakeholder Portal, AI)
- **Tenant Plane:** Per-organization context for business operations
- **Session Invariant:** Switching planes requires logout/login
- **Dual-Plane Human Identity Pattern:** Separate emails for platform vs tenant identities

---

## [2026-01-23] Add Core Extensions: Auth/RBAC, Stakeholder Interface, Discovery Pack

**Summary:** Introduced three foundational FORGE extensions that establish identity, stakeholder visibility, and structured discovery as standard capabilities. These extensions transform FORGE from a development methodology into a complete project operating system.

**Files touched:**
- `docs/extensions/auth-rbac.md` (created) — Identity and permission foundation
- `docs/extensions/stakeholder-interface.md` (created) — First-party visibility and AI assistance
- `docs/extensions/discovery-pack.md` (created) — Structured discovery-to-spec methodology
- `docs/extensions/README.md` (modified) — Added extension index with categories
- `core/forge-core.md` (modified) — Added Extensions section (v1.1 → v1.2)
- `CHANGELOG.md` (updated)

**Impact:** Public canon — new required extensions for software projects; Discovery Pack required for ALL projects.

**Details:**

### Auth/RBAC
- Org-centric identity model (users belong to orgs via memberships)
- Four standard roles: Owner, Admin, Member, Stakeholder
- Stakeholder is first-class role, not a flag
- Multi-role users supported (roles are additive)
- Two-phase auth: identity then context
- Required for all software projects

### Stakeholder Interface
- First-party visibility and feedback system
- Stakeholder Interface AI (Foundational) ships Day One
- AI explains, answers, captures feedback — does NOT execute
- Upvote-only voting; humans triage and prioritize
- All stakeholders see all submissions (within org)
- Required for all software projects

### Discovery Pack
- Structured discovery-to-spec methodology
- Applies to ALL project types (software, book, coaching, research)
- "Every project has discovery; not every project has software"
- Four stages: Intake → Structure → Iterate → Handoff
- Agent-assisted, human-gated
- Explicit handoff moment with spec pack

### Key Distinctions
- Stakeholder Interface AI (Foundational) = Day One, required, explanatory + intake
- FAI-for-execution = Optional, maturity-gated, deferred
- Same AI identity, different capability surfaces

---

## [2026-01-16] Add FORGE AI Interface (FAI) extension

**Summary:** Introduced FAI as the first optional FORGE extension, providing a first-class AI interface layer for projects that need user-facing Q&A, action execution, feedback capture, and multimodal intake.

**Files touched:**
- `docs/extensions/README.md` (created) — Extensions index
- `docs/extensions/fai-overview.md` (created) — FAI capability definition
- `core/forge-governance.md` (modified) — Added Extensions section
- `docs/agents/README.md` (modified) — Added FAI reference
- `CHANGELOG.md` (updated)

**Impact:** Public canon — new optional extension capability.

**Details:**
- FAI is explicitly OPTIONAL — no project requires it for FORGE compliance
- FAI is an interface layer, not an autonomous agent
- Four capability tiers: Read-Only Q&A, Action Execution, Feedback Capture, Multimodal Intake
- Hard boundaries: no code modification, no PR creation, no auto-merge
- GitHub Apps required (no PATs); RBAC mirroring with confirm-before-act
- Integration points: docs/constitution/FAI.md, parking-lot, task briefs
- Research basis: ~/kv-projects/FORGE-Method/research/ai-interface/

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
