# FORGE-Method Repository

> **Canonical FORGE Methodology — Public Documentation**
> Last Updated: 2026-01-23

---

## 0. Quick Start

### If You Are an Agent Landing Here:

1. **This is PUBLIC CANON** — Everything here is the source of truth for FORGE methodology
2. **This is NOT a workspace** — Active R&D happens in `../_workspace/`, not here
3. **Read the umbrella CLAUDE.md first** — `../CLAUDE.md` governs the meta-workspace
4. **Identify your task type** — See Section 2 for what requires approval
5. **Do NOT edit core/ without explicit approval** — Hard stop
6. **Run recon before proposing any changes** — Read affected files first

### Hard Stops (Non-Negotiable)

| Action | Rule |
|--------|------|
| Edit `core/*.md` | **REQUIRES Human Lead approval** |
| Delete any file | **REQUIRES Human Lead approval** |
| Restructure folders | **REQUIRES Human Lead approval** |
| Version bump | **REQUIRES Human Lead approval** |
| Merge to main | **REQUIRES Human Lead approval** |

---

## 1. Repository Map

> **Note:** This repo contains finalized canon. For active R&D, see `../_workspace/`.

```
FORGE-Method/
├── CLAUDE.md              ← YOU ARE HERE
├── README.md              ← Public landing page
├── CHANGELOG.md           ← Version history (update with changes)
│
├── core/                  ← [CANON] Core methodology - HIGH STABILITY
│   ├── forge-core.md
│   ├── forge-governance.md
│   ├── forge-operations.md
│   └── forge-orientation.md
│
├── templates/             ← [OPS] Canonical templates - MEDIUM STABILITY
│   ├── agents/            ← Agent templates
│   └── forge-template-*.md
│
├── agents/                ← Agent operating guides
│   └── README.md
│
├── docs/                  ← Extended documentation
│   ├── extensions/        ← Optional FORGE extensions (e.g., FAI)
│   └── agents/
│
├── starter-kit/           ← Drop-in project scaffolding
├── profiles/              ← Domain-specific implementations
├── research/              ← Research staging (NOT active workspace)
├── reports/               ← Generated reports
├── meta/                  ← Migration maps, deprecations
├── archive/               ← Archived/deprecated content
├── 02_execution/          ← Recons, experiments
└── incoming/              ← TRIAGE QUEUE (NOT active workspace)
```

---

## 2. Canon Hierarchy & Change Authority

### Stability Levels

| Location | Stability | Change Frequency | Authority Required |
|----------|-----------|------------------|-------------------|
| `core/` | **HIGH** | Rarely (major insights only) | Human Lead (Leo) only |
| `templates/` | MEDIUM | As better patterns emerge | Human Lead review |
| `agents/` | MEDIUM | As roles evolve | Human Lead review |
| `docs/` | MEDIUM | As capabilities expand | Review for extensions |
| `starter-kit/` | MEDIUM | As scaffolding improves | Review for structure |
| `profiles/` | LOW | Domain-specific | Team discretion |
| `research/` | LOW | Active exploration | No approval needed |
| `incoming/` | TRIAGE | Pending organization | Triage required |
| `archive/` | FROZEN | Historical only | Do not modify |

### What Each Role Can Do

| Role | `core/` | `templates/` | `docs/` | `research/` | `incoming/` |
|------|---------|--------------|---------|-------------|-------------|
| **Human Lead (Leo)** | Edit | Edit | Edit | Edit | Edit |
| **Strategist (Jordan)** | Propose | Edit w/ review | Edit | Edit | Triage |
| **Quality Gate (CC)** | **Read only** | Propose | Propose | Add | Add |
| **Implementation (Cursor)** | **Read only** | Implement approved | Implement approved | Add | Add |

### Change Types Requiring Approval

**Always requires Human Lead approval:**
- [ ] Any modification to `core/*.md`
- [ ] New templates in `templates/`
- [ ] Structural changes to `starter-kit/`
- [ ] New extensions in `docs/extensions/`
- [ ] Version bumps (see SemVer below)
- [ ] CHANGELOG.md entries for significant changes
- [ ] Deprecation of any document
- [ ] Deletion of any file

**Does NOT require approval:**
- Adding recon reports to `02_execution/`
- Adding research to `research/`
- Adding items to `incoming/` for triage
- Fixing typos (patch-level, must note in commit)
- Adding examples that don't change behavior

---

## 3. Versioning Rules (SemVer)

FORGE uses semantic versioning: `MAJOR.MINOR.PATCH`

### What Constitutes Each Level

| Bump | Trigger | Examples |
|------|---------|----------|
| **MAJOR** (2.0, 3.0) | Breaking changes to core | Changes to Five Laws, F-O-R-G-E sequence, fundamental restructuring |
| **MINOR** (1.1, 1.2) | New capabilities | New templates, new sections, significant clarifications |
| **PATCH** (1.1.1) | Corrections | Typos, minor clarifications, formatting, example updates |

### Version Bump Workflow

```
1. IDENTIFY  → Determine change scope
2. CLASSIFY  → MAJOR / MINOR / PATCH
3. DOCUMENT  → Write CHANGELOG.md entry
4. APPROVE   → Get Human Lead sign-off
5. TAG       → Create git tag (e.g., v1.2.0)
6. ANNOUNCE  → Update README if needed
```

---

## 4. Standard Workflows

### Workflow: Edit Core Document

**This is the highest-friction workflow intentionally.**

```
1. RECON
   - Read the entire file you want to edit
   - Read related files for context
   - Understand current version

2. PROPOSE
   - Create proposal document
   - Explain: what changes, why, impact
   - Place in incoming/ or flag [PROPOSAL]

3. REVIEW
   - Request Human Lead review
   - Address feedback

4. APPROVE
   - Get explicit written approval
   - "Approved to edit core/forge-X.md" from Leo

5. IMPLEMENT
   - Make the edit
   - Keep changes minimal

6. VERIFY
   - Check markdown formatting
   - Verify all links work
   - Ensure consistency with other docs

7. CHANGELOG
   - Add entry to CHANGELOG.md
   - Include: date, summary, files touched, impact

8. VERSION
   - Bump version per SemVer rules
   - Tag release if MINOR or MAJOR
```

### Workflow: Add New Template

```
1. RECON     → Review existing templates in templates/
2. DRAFT     → Create draft in incoming/
3. REVIEW    → Request review
4. APPROVE   → Get Human Lead approval
5. PLACE     → Move to templates/ with proper naming
6. UPDATE    → Update any indexes or READMEs
7. CHANGELOG → Document the addition
```

### Workflow: Add Research/Recon

```
1. CREATE    → Write your research/recon document
2. NAME      → Use pattern: recon-<topic>-YYYY-MM-DD.md
3. PLACE     → Put in research/ or 02_execution/recons/
4. INDEX     → No approval needed, but update index if exists
```

### Workflow: Triage Incoming

```
1. REVIEW    → Read item in incoming/
2. CLASSIFY  → Determine: canon candidate, archive, delete, needs work
3. ROUTE     → Move to appropriate location OR flag for decision
4. TRACK     → Note in commit message what was triaged
```

---

## 5. File Naming Conventions

| Type | Pattern | Example |
|------|---------|---------|
| Core doc | `forge-<topic>.md` | `forge-core.md` |
| Template | `forge-template-<name>.md` | `forge-template-kickoff-brief.md` |
| Agent guide | `forge-<agent>-operating-guide.md` | `forge-jordan-operating-guide.md` |
| Recon | `recon-<topic>-YYYY-MM-DD.md` | `recon-api-layer-2026-01-20.md` |
| Profile | `forge-<domain>-profile.md` | `forge-sd-profile.md` |
| Extension | `<extension>-overview.md` | `fai-overview.md` |

---

## 6. Quality Standards (Public Repo)

### All Content Must Be:

- [ ] **Professional** — No internal jargon without explanation
- [ ] **Clear** — Scannable with headers, lists, tables
- [ ] **Complete** — No dangling references or TODOs in canon
- [ ] **Consistent** — Follows existing patterns
- [ ] **Linked** — Cross-references work

### Before Committing:

- [ ] Markdown renders correctly
- [ ] All internal links valid
- [ ] No sensitive/internal-only content
- [ ] Consistent with FORGE voice
- [ ] Spell-checked

### Flagging Incomplete Work

Use these labels in document headers:

| Label | Meaning |
|-------|---------|
| `[CANON]` | Approved, stable, authoritative |
| `[OPS]` | Operational, can evolve |
| `[PROPOSAL]` | Draft, not yet approved |
| `[EXPERIMENTAL]` | Exploratory, may change |
| `[DEPRECATED]` | Being phased out, see replacement |

---

## 7. The `incoming/` Triage Queue

The `incoming/` folder contains unprocessed artifacts. Rules:

### What Goes Here:
- New documents pending review
- Migrated content needing organization
- Proposals awaiting triage
- Duplicates needing resolution

### What Does NOT Go Here:
- Canonical content (goes to appropriate folder)
- Research (goes to `research/`)
- Archives (goes to `archive/`)

### Triage Protocol:
1. Each item should be triaged within one session
2. Move to correct location or flag for decision
3. Delete obvious duplicates (with approval if significant)
4. Track triage actions in commits

---

## 8. CHANGELOG Format

Location: `/CHANGELOG.md`

```markdown
## [YYYY-MM-DD] Title

**Summary:** One-line description

**Files touched:**
- `path/file.md` (created | modified | deleted) — brief note

**Impact:** Public canon | Internal ops | Templates | etc.

**Details:** (optional)
- Bullet points with specifics
```

---

## 9. Integration with Umbrella

This repo is part of the FORGE™ meta-workspace.

### This Repo Is Canon Only

**FORGE-Method contains finalized, governed methodology.** It is NOT a workspace for active development.

| What Happens Here | What Does NOT Happen Here |
|-------------------|---------------------------|
| Finalized methodology | Active R&D |
| Approved templates | Exploratory work |
| Governed extensions | Proposals-in-progress |
| Versioned releases | Cross-repo coordination |

### Where Active Development Happens

**Active R&D on FORGE itself happens in `../_workspace/`** — the umbrella workspace.

```
_workspace/04_proposals/  →  [APPROVAL]  →  FORGE-Method/
```

Changes arrive here via **promotion** after being:
1. Developed in `_workspace/`
2. Reviewed as proposals
3. Approved by Human Lead
4. Promoted with decision record

### Clarification: `research/` and `incoming/`

These folders exist within FORGE-Method but serve limited purposes:

| Folder | Purpose | NOT For |
|--------|---------|---------|
| `research/` | Staging area for materials that may inform canon | Active R&D workspace |
| `incoming/` | Triage queue for artifacts needing organization | Exploratory work |

**If you're doing exploratory work on FORGE features, use `../_workspace/` instead.**

### Cross-Repo Rules:

1. **Method is canon** — Other repos reference Method, not vice versa
2. **Changes here propagate** — forge-project-template should align with Method templates
3. **Vault may propose** — Genesis vault can propose changes that land here after approval
4. **Workspace feeds Method** — `_workspace/` is where changes are developed before promotion
5. **Sync on release** — Major releases should trigger template repo review

### Related Locations:
- Umbrella governance: `../CLAUDE.md`
- R&D workspace: `../_workspace/`
- Template repo: `../forge-project-template/`
- Genesis vault: `../forge-genesis-vault/`

---

## 10. Emergency Procedures

### If You Break Something:

1. **STOP** — Do not make additional changes
2. **REVERT** — `git checkout -- <file>` for uncommitted changes
3. **REPORT** — Note what happened
4. **ESCALATE** — Notify Human Lead if committed

### If Unsure:

1. **Do NOT guess** — Ask rather than assume
2. **Read more** — There's probably documentation
3. **Propose** — Write a proposal rather than making the change
4. **Escalate** — When in doubt, get Human Lead input

---

## Quick Reference

### Paths Cheat Sheet

```
core/forge-core.md           ← Core methodology (DO NOT EDIT without approval)
core/forge-governance.md     ← Versioning rules
templates/                   ← Canonical templates
agents/README.md             ← Agent quickstart
docs/extensions/             ← Optional extensions (FAI, etc.)
CHANGELOG.md                 ← Version history
incoming/                    ← Triage queue
```

### Approval Checklist

Before editing canon:
- [ ] I have read the file completely
- [ ] I have Human Lead approval
- [ ] I will update CHANGELOG.md
- [ ] I will keep changes minimal
- [ ] I will verify after editing

---

*This document governs all agent activity within the FORGE-Method repository. Canon edits without approval are hard stops.*
