# CC Review Request: FORGE Instantiation Artifacts

**Type:** Doability Validation  
**Requested By:** Leo (Human Lead)  
**Date:** 2026-01-06  
**Priority:** High — Blocks repo creation

---

## Context

CP has produced four artifacts that define how new FORGE-SD projects are instantiated:

1. `forge-template-kickoff-brief.md` — The intake document from Jordan → CP
2. `forge-project-template-specification.md` — What you (CC) implement as a repo
3. `forge-sd-profile-addendum.md` — Your operating rules for software projects
4. `forge-template-project-identity.md` — Template for generating `CLAUDE.md`

These documents are intended to be **mechanically executable by you**. Before we create the actual GitHub repo template, we need your ground-truth validation.

---

## Your Task

**Assume you are instantiating a real project tomorrow.**

Answer only: **Where would you hesitate, ask a question, or be forced to guess?**

---

## Allowed Response Categories

You may ONLY use these three categories:

| Category | Meaning |
|----------|---------|
| **Executable as written** | You can do this without interpretation |
| **Ambiguous at runtime** | You would need to ask a question or make a judgment call |
| **Conflicts with real tooling behavior** | The spec says X but the tool actually does Y |

No suggestions. No improvements. No philosophy. Flag gaps only.

---

## Specific Validation Points

### 1. Executability Check

For the **Project Template Specification**, can you:
- [ ] Create the directory structure exactly as specified?
- [ ] Follow the instantiation sequence (Steps 1-9) without interpretation?
- [ ] Populate `CLAUDE.md` using the Project Identity Template + Kickoff Brief?
- [ ] Generate all placeholder files in `docs/constitution/`?

**If NO to any:** State which category (Ambiguous / Conflicts) and exactly what's unclear.

### 2. Runtime Friction Check

For the **FORGE-SD Profile Addendum**, identify:
- Any role boundaries that would cause confusion during Execute
- Any handoff points where information would be lost
- Any verification steps that are unclear or incomplete
- Any conflicts with your current global rules on the iMac Pro

### 3. Practical Gap Check

Based on your experience with Vantage and other projects:
- What would break on day one of a real project?
- What's missing that you've needed in practice?
- What's over-specified and would slow you down?

---

## What You Are NOT Reviewing

- **Canon validity** — Assume FORGE Core and Operations Manual are correct
- **Strategic decisions** — Don't second-guess why we chose this structure
- **Elegance** — We want executable, not elegant
- **Scope expansion** — Don't add features; flag gaps only

---

## Output Format

```markdown
## CC Validation Report

**Date:** [YYYY-MM-DD]
**Artifacts Reviewed:** [list all 4]
**Verdict:** EXECUTABLE / NEEDS REVISION / BLOCKED

### Executability Checklist

- [ ] Directory structure: [Executable / Ambiguous / Conflicts]
- [ ] Instantiation sequence: [Executable / Ambiguous / Conflicts]
- [ ] CLAUDE.md generation: [Executable / Ambiguous / Conflicts]
- [ ] Placeholder files: [Executable / Ambiguous / Conflicts]

### Issues Found

[List any Ambiguous or Conflicts items, ranked by severity]

1. **[High/Med/Low]** — [Issue description]
   - Category: [Ambiguous at runtime / Conflicts with tooling]
   - Location: [Which doc, which section]
   - What happens: [Specific failure mode]

### Gaps from Practice

[What's missing based on real project experience — Vantage, etc.]

### Conflicts with Global Rules

[Any conflicts with existing CC configuration on iMac Pro]

### Recommendation

[Proceed / Revise before proceeding / Major rework needed]
```

---

## Files to Review

The following files should be in this directory alongside this prompt:

- `forge-template-kickoff-brief.md`
- `forge-project-template-specification.md`
- `forge-sd-profile-addendum.md`
- `forge-template-project-identity.md`

Read all four before providing your validation report.

---

## After Your Review

- If **EXECUTABLE**: Leo will greenlight repo creation
- If **NEEDS REVISION**: CP will address specific friction points
- If **BLOCKED**: Escalate to Leo for resolution

---

## Reminder: Your Role

You are the **ground-truth sensor**. Your job is to tell us what actually happens vs. what we documented. Theory doesn't matter here — only execution reality.

Be direct. Flag issues without softening. We'd rather fix problems now than discover them mid-project.

---

*This review follows The FORGE Method™ — theforgemethod.org*
