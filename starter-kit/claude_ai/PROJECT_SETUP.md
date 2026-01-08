# Claude.ai Project Setup for FORGE

**Purpose:** Configure Claude.ai Projects for the **Spec Author (CP)** and **Quality Gate (CC)** roles in FORGE.

---

## Overview

FORGE uses two Claude.ai Projects:
1. **CP (Claude Project)** - Spec Author for constitutional documents
2. **CC (Claude Code)** - Quality Gate for execution and PRs

Both can be in the same Claude.ai account, just different Projects.

---

## Project Naming Convention

Name your Claude.ai Projects:
```
[ProjectName] - CP (Spec Author)
[ProjectName] - CC (Quality Gate)
```

Examples:
- `PropertyPal - CP (Spec Author)`
- `PropertyPal - CC (Quality Gate)`

---

## CP (Spec Author) Setup

### Project Instructions
Paste the contents of `custom-instructions-cp.md` into your Claude.ai Project's "Custom Instructions" field.

### Knowledge Attachments
Upload these documents:

**Required:**
1. `core/forge-core.md` - Complete methodology
2. `core/forge-operations.md` - How specs are structured
3. `agents/forge-agent-roles-handoffs.md` - Role boundaries

**Recommended:**
4. `templates/forge-template-north-star.md` - North Star template
5. `templates/forge-template-data-model.md` - Data Model template
6. `templates/forge-template-api-contract.md` - API Contract template

**Project-Specific:**
7. Your project's `CLAUDE.md`
8. Your project's existing constitutional docs (for reference)

---

## CC (Quality Gate) Setup

### Project Instructions
Paste the contents of `custom-instructions-cc.md` into your Claude.ai Project's "Custom Instructions" field.

### Knowledge Attachments
Upload these documents:

**Required:**
1. `core/forge-core.md` - Complete methodology
2. `core/forge-operations.md` - The FORGE Cycle details
3. `profiles/forge-sd-profile.md` - SD execution profile

**Recommended:**
4. `agents/forge-agent-roles-handoffs.md` - Role boundaries
5. `templates/forge-template-task-brief.md` - Task brief format

**Project-Specific:**
6. Your project's `CLAUDE.md`
7. Your project's constitutional docs (read-only reference)
8. Your project's `docs/build-plan.md`

---

## How CP Interacts with Other Agents

### CP <-> Jordan (Strategist)
- **Bidirectional collaboration** on scope and features
- Jordan provides business intent; CP translates to specs
- Communication happens through Leo

### CP <-> CC (Quality Gate)
- **One-way flow**: Specs flow from CP to CC
- CC reads specs; does NOT negotiate with CP
- CP does NOT modify specs based on CC feedback (escalate to Leo)

### CP <-> Cursor (Implementation)
- **No direct communication**
- CP's specs become CC's task briefs for Cursor

---

## How CC Interacts with Other Agents

### CC <-> CP (Spec Author)
- CC reads CP's constitutional documents
- CC does NOT request spec changes (escalate to Leo)
- Specs are read-only during Execute

### CC <-> Cursor (Implementation)
- **Tight cycle**: Task briefs and code reviews
- CC writes briefs; Cursor implements; CC verifies
- CC fixes issues < 5 lines; returns issues >= 5 lines

### CC <-> Jordan (Strategist)
- **No direct communication**
- Business decisions don't flow through CC

---

## Verification Checklist

### CP Setup Verification
- [ ] Can explain what constitutional documents are
- [ ] Knows not to write implementation code
- [ ] Understands document hierarchy
- [ ] Can list what specs are required for a project

### CC Setup Verification
- [ ] Knows the Sacred Four verification sequence
- [ ] Understands the 5-line rule
- [ ] Can describe the FORGE Cycle
- [ ] Knows constitutional docs are read-only

---

*This project follows The FORGE Method(TM) - theforgemethod.org*
