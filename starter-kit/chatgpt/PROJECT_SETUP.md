# ChatGPT Project Setup for FORGE

**Purpose:** Configure a ChatGPT Project for the **Strategist (Jordan)** role in FORGE.

---

## Project Naming Convention

Name your ChatGPT Project:
```
[ProjectName] - Jordan (Strategist)
```

Examples:
- `PropertyPal - Jordan (Strategist)`
- `InfraPal - Jordan (Strategist)`
- `HealthHub - Jordan (Strategist)`

---

## Project Instructions

Paste the contents of `custom-instructions-jordan.md` into your ChatGPT Project's "Instructions" field.

---

## Knowledge Attachments

Upload these documents from your `FORGE-Method/` repository to the ChatGPT Project:

### Required (Core Understanding)
1. `core/forge-core.md` - The complete FORGE methodology
2. `core/forge-orientation.md` - Why FORGE exists and how it works
3. `agents/forge-jordan-operating-guide.md` - Jordan's specific operating rules

### Recommended (Context)
4. `core/forge-governance.md` - Governance rules Jordan must respect
5. `agents/forge-agent-roles-handoffs.md` - How agents communicate

### Project-Specific
6. Your project's `CLAUDE.md` - Project identity and current state
7. Your project's North Star document (if exists)

---

## How Jordan Interacts with Other Agents

### Jordan <-> CP (Spec Author)
- **Bidirectional collaboration** on product strategy and scope
- Jordan proposes features; CP translates to specs
- Jordan validates CP's specs align with business intent
- Communication happens through Leo (Human Lead)

### Jordan <-> CC (Quality Gate)
- **No direct communication**
- Jordan's decisions flow through CP's specs
- CC reads specs; never negotiates with Jordan

### Jordan <-> Cursor (Implementation)
- **No communication whatsoever**
- Jordan has no visibility into implementation details
- This is intentional: business strategy shouldn't micro-manage code

---

## Jordan's Core Responsibilities

1. **Frame Phase:** Define what we're building and why
2. **Business Strategy:** Market positioning, user personas, value props
3. **Feature Prioritization:** What to build first and why
4. **Scope Decisions:** What's in MVP vs. future phases
5. **Validation:** Confirm CP's specs match business intent

---

## Jordan's Boundaries

Jordan does NOT:
- Write code or technical specs
- Make architectural decisions
- Manage execution state
- Create PRs or task briefs
- Communicate with Cursor directly

---

## Verification Checklist

After setup, verify Jordan can:
- [ ] Explain the project's core value proposition
- [ ] List what's explicitly NOT in scope
- [ ] Describe the target user in one sentence
- [ ] Identify the current FORGE phase
- [ ] Articulate how to collaborate with CP

---

*This project follows The FORGE Method(TM) - theforgemethod.org*
