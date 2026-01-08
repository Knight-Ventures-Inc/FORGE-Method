# FORGE Template: Kickoff Brief

**The Gate Between Ideation and FORGE**

**Version:** 1.0  
**Status:** First-Class Artifact

---

## Purpose

The Kickoff Brief is the **only artifact** used to promote a project from ideation (KV) into FORGE. It is the formal handoff from Strategist to Spec Author.

This document:
- Captures intent without implementation detail
- Locks scope before constitutional documents are written
- Requires explicit Human Lead approval to proceed
- Selects the execution profile (e.g., FORGE-SD for software)

**One page maximum.** If it's longer, you're in Refine territory.

---

## When to Create

Create when:
- Ideation is complete (you and Strategist have shaped the concept)
- You can explain the product in 60 seconds
- You're ready to commit resources to building
- Human Lead is prepared to greenlight

Do NOT create when:
- Still exploring "should we build this?"
- Key questions remain unanswered
- Scope is fuzzy or expanding

---

## What Problem It Prevents

- Projects drifting into FORGE without clear intent
- Spec Author guessing what to specify
- Constitutional documents built on unstable foundations
- Scope creep before work even begins
- "I thought we agreed..." conversations later

---

## Who Fills This Out

**Strategist** (Jordan) completes the brief based on ideation conversations.

**Human Lead** (Leo) reviews and signs the Greenlight field.

**Spec Author** (CP) receives the approved brief and begins constitutional document authoring.

---

## Template

```markdown
# Kickoff Brief: [Project Name]

**Date:** [YYYY-MM-DD]  
**Strategist:** [Name/Agent]  
**Human Lead:** [Name]

---

## Project Identity

**One-line description:**  
[What this project does in ≤15 words]

**Project codename:** [Short identifier, e.g., "vantage", "bolo", "propertypal"]

---

## Intent Summary

**What problem are we solving?**  
[2-3 sentences. Who feels this pain? Why does it matter?]

**What are we building?**  
[2-3 sentences. Focus on what it DOES, not how it works.]

**Who is this for?**  
- Primary users: [Who uses this directly]
- Stakeholders: [Who cares about outcomes]

---

## Scope

**What's IN (MVP)**  
- [Core capability 1]
- [Core capability 2]
- [Core capability 3]

**What's OUT (Explicit Non-Goals)**  
- [Excluded item 1] — [why]
- [Excluded item 2] — [why]
- [Excluded item 3] — [why]

---

## Success Criteria

**Definition of Done (MVP)**  
- [ ] [Concrete deliverable 1]
- [ ] [Concrete deliverable 2]
- [ ] Deployed to production
- [ ] Primary user can complete core workflow

---

## Execution Profile

**Selected Profile:** [ ] FORGE-SD (Software Development)

*Future profiles (not yet defined):*
- [ ] FORGE-BOOK
- [ ] FORGE-SVC

**Tech Stack (if FORGE-SD):**  
[e.g., Next.js 15 / TypeScript / Supabase / Vercel — or "TBD in Refine"]

---

## Open Questions

Questions that must be answered before Refine begins:

| Question | Owner | Status |
|----------|-------|--------|
| [Question 1] | [Who] | Open / Resolved / Deferred |
| [Question 2] | [Who] | Open / Resolved / Deferred |

*If critical questions remain Open, do not proceed to Greenlight.*

*Any question marked "Deferred" must explicitly state where the decision will be made (Refine or Execute). Otherwise, Greenlight is blocked.*

---

## Human Greenlight

**By signing below, Human Lead confirms:**
- [ ] Intent is clear and stable
- [ ] Scope is locked (changes require re-approval)
- [ ] Resources can be committed to this project
- [ ] This project is authorized to proceed to FORGE

**Approved by:** ____________________  
**Date:** ____________________

---

*Kickoff complete. Ready to proceed to Orchestrate/Refine.*
```

---

## Field Definitions

| Field | Purpose | Guidance |
|-------|---------|----------|
| **One-line description** | Forces clarity | If you can't say it in 15 words, you don't understand it yet |
| **Project codename** | Short identifier | Used in folder names, branch prefixes, conversation references |
| **Intent Summary** | Why this exists | Problem → Solution → Users. No implementation detail. |
| **Scope IN** | What we're building | 3-5 capabilities max for MVP. More = scope creep risk |
| **Scope OUT** | What we're NOT building | At least 3 items. Forces explicit exclusions. |
| **Success Criteria** | How we know we're done | Must be verifiable, not aspirational |
| **Execution Profile** | How we'll build it | FORGE-SD for software; others TBD |
| **Open Questions** | Remaining unknowns | All must be Resolved or explicitly deferred before Greenlight |
| **Human Greenlight** | Authorization gate | Law 3: No phase advances without explicit human approval |

---

## Kickoff Brief vs Frame Artifact

These documents serve related but distinct purposes:

| Aspect | Kickoff Brief | Frame Artifact |
|--------|---------------|----------------|
| **Length** | 1 page max | 2-6 pages |
| **Detail** | Intent only | Full problem/solution analysis |
| **When created** | End of ideation | During Frame phase |
| **Who creates** | Strategist | Strategist or Human Lead |
| **Purpose** | Gate entry to FORGE | Comprehensive framing |

**Relationship:** The Kickoff Brief is a *compressed* Frame. For simple projects, they may be identical. For complex projects, the Frame Artifact expands on the Kickoff Brief's intent.

**Rule:** A Kickoff Brief is always required. A full Frame Artifact is optional but recommended for complex or high-stakes projects.

---

## Common Failure Modes

| Failure | Symptom | Prevention |
|---------|---------|------------|
| Too long | >1 page | Compress or split into Frame Artifact |
| Implementation detail | Tech decisions in scope | Remove; belongs in Refine |
| No explicit non-goals | Everything feels in scope | Force 3+ items in OUT section |
| Vague success criteria | "Users are happy" | Require checkboxes with concrete deliverables |
| Open questions unresolved | Greenlight with unknowns | Block Greenlight until resolved/deferred |
| Missing Greenlight | Project starts without approval | Require signature before any work |

---

## What Happens After Kickoff

1. **Human Lead signs Greenlight** — Project is authorized
2. **Kickoff Brief goes to Spec Author (CP)** — Via download/handoff
3. **Spec Author begins constitutional documents** — North Star, Architecture, etc.
4. **Constitutional docs go to CC** — For project instantiation
5. **Execute begins** — The FORGE Cycle runs

The Kickoff Brief is **read-only after Greenlight**. Scope changes require:
1. New Kickoff Brief or amendment
2. Human Lead re-approval
3. Impact assessment on existing constitutional docs

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-04 | Initial template |

---

**[UNIVERSAL]**

**© 2026 Knight Ventures, Inc. All rights reserved.**

**FORGE™** is a trademark of Knight Ventures, Inc.
