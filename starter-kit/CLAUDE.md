# [CUSTOMIZE: Project Name]

**[CUSTOMIZE: One-line description]**

---

## Project Identity

### What This Is
[CUSTOMIZE: 2-3 sentences describing what this project does]

### What This Is NOT
- [CUSTOMIZE: Explicit non-goal 1]
- [CUSTOMIZE: Explicit non-goal 2]
- [CUSTOMIZE: Explicit non-goal 3]

---

## FORGE Context

This project follows **The FORGE Method(TM)**.

**Current Phase:** [CUSTOMIZE: Frame | Orchestrate | Refine | Govern | Execute]
**Execution Profile:** FORGE-SD (Software Development)

### Canonical Authority

| Source | Location |
|--------|----------|
| FORGE Core | `FORGE-Method/core/forge-core.md` |
| Operations Manual | `FORGE-Method/core/forge-operations.md` |
| SD Profile | `FORGE-Method/profiles/forge-sd-profile.md` |
| Document Index | `FORGE-Method/meta/MANIFEST.md` |

---

## Agent Lanes

| Role | Agent | Platform | Authority |
|------|-------|----------|-----------|
| **Human Lead** | Leo | Human | Final decisions, greenlight, merge |
| **Strategist** | Jordan | ChatGPT | Business strategy, feature framing |
| **Spec Author** | CP | Claude Project | Constitutional docs, specs |
| **Quality Gate** | CC | Claude Code | Verification, PRs, build-plan |
| **Implementation** | Cursor | Cursor IDE | Code per task briefs |

### Lane Boundaries

**CC (Quality Gate) CAN:**
- Run verification sequence
- Create PRs and branches
- Fix issues < 5 lines
- Maintain `docs/build-plan.md`
- Write task briefs

**CC (Quality Gate) CANNOT:**
- Make architectural decisions
- Modify `docs/constitution/`
- Merge PRs (Leo does this)
- Expand scope beyond spec

---

## Artifact Flow

```
Jordan (ideation) --> CP (specs) --> CC (execution) --> Cursor (code)
                                          |
                                          v
                              docs/build-plan.md (state)
                              ai_prompts/active/ (current brief)
                              ai_prompts/completed/ (archive)
```

---

## Commands

### Verification Sequence (Sacred)
```bash
pnpm typecheck && pnpm lint && pnpm test:run && pnpm build
```

### Development
```bash
pnpm dev          # Start dev server
pnpm build        # Production build
```

### Database [CUSTOMIZE: if using Supabase]
```bash
pnpm db:generate  # Generate migrations
pnpm db:migrate   # Apply migrations
```

---

## Current State

**Current PR:** [CUSTOMIZE: PR-XX or "Not started"]
**Build Plan:** `docs/build-plan.md`
**Active Brief:** `ai_prompts/active/`

---

## Getting Oriented (New Session)

```
1. Read this file (you're doing it)
2. Check docs/build-plan.md for current status
3. Run: git log --oneline -5
4. Check ai_prompts/active/ for current brief
5. Ready to proceed (~90 seconds)
```

---

## Non-Negotiables

1. **Verification runs before every PR** - All four steps must pass
2. **Constitutional docs are read-only** - Suggest changes, don't modify
3. **5-line rule** - < 5 lines: fix locally; >= 5 lines: send back to Cursor
4. **File-based handoffs** - Everything through `ai_prompts/`
5. **Archive before starting** - Each PR archives the previous brief

---

## Key Locations

| What | Where |
|------|-------|
| Constitutional docs | `docs/constitution/` |
| Build plan | `docs/build-plan.md` |
| Current task | `ai_prompts/active/` |
| Completed tasks | `ai_prompts/completed/` |
| Task templates | `ai_prompts/templates/` |
| Parking lot | `docs/parking-lot/` |

---

## Parking Lot Protocol

The parking lot (`docs/parking-lot/`) captures issues and ideas discovered during development that shouldn't derail current PR scope.

### Files

| File | What Goes Here |
|------|----------------|
| `known-issues.md` | Bugs, broken things, security risks, technical debt |
| `future-work.md` | Feature ideas, enhancements, optimizations, nice-to-haves |

### When to Log

Log to parking lot **immediately** when you discover:
- A bug unrelated to your current PR
- A missing feature that would be nice but isn't in scope
- Technical debt worth addressing later
- A security concern that needs follow-up
- An optimization opportunity
- Ideas from debugging that could improve the system

### Entry Format

```markdown
## [YYYY-MM-DD] Short Title

**Source:** PR-XX or context | **Severity:** Low/Medium/High | **Effort:** X hrs

One-paragraph description of the issue or idea.

**Workaround:** (if applicable for known-issues)

**Fix:** Proposed solution or next steps.
```

### Workflow

1. **Discover** an issue or idea during PR work
2. **Log immediately** to the appropriate parking-lot file
3. **Continue** with current PR scope
4. **Review** parking lot when planning future PRs
5. **Graduate** items to GitHub Issues when prioritized for a specific PR

**Golden Rule:** Don't let discoveries get lost in conversation history. If it's not in scope, park it.

---

*This project follows The FORGE Method(TM) - theforgemethod.org*
