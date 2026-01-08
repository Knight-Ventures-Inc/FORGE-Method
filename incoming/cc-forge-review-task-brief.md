# CP → CC: FORGE Method Ground-Truth Review

**From:** CP (Claude Project)  
**To:** CC (Claude Code)  
**Date:** 2026-01-03  
**Type:** Methodology Improvement Task  
**Priority:** High — Blocking FORGE v1.1 Release  
**Output Location:** `ai_prompts/forge/forge-method-review-2026-01-03.md`

---

## PRIMARY MISSION

**We need to understand the real execution engine.**

The FORGE document describes phases, handoffs, and governance — but it doesn't capture the **actual rhythm** that you, Cursor, and Leo run through multiple times per day to ship at blistering pace.

That rhythm IS the method. Everything else is scaffolding.

Your most important job in this review: **Document exactly how the CC-Cursor-Leo loop actually runs** — the why, the way, the how, the what, the timing. What makes it fast. What breaks it. What a new agent wouldn't know.

The rest of the review matters, but Section 1 (The Execution Engine) is the heart of this task.

**Important framing:** This is not an evaluation of performance. It is an extraction of institutional knowledge. Be maximally candid.

**Timebox guidance:** Depth is more important than coverage. If time is limited, prioritize Section 1 over everything else.

---

## Objective

Review **The FORGE Method™ v1.0** (`ai_prompts/forge/the-forge-method.md`) against your firsthand experience executing on Vantage DD. Produce a comprehensive, candid report identifying where the documented methodology matches reality, where it diverges, and what's missing entirely.

**Your unique value:** You are the only agent who has actually *executed* this methodology in production. Jordan ideates, CP specifies, Leo greenlights — but you and Cursor do the work. Your perspective is ground-truth.

---

## Context

### What This Document Is

The FORGE Method™ is our attempt to codify how Leo + Jordan + CP + CC + Cursor collaborate to build production-grade SaaS products. It defines:

- Five phases: **F**rame, **O**rchestrate, **R**efine, **G**overn, **E**xecute
- Agent roles and authority boundaries
- Handoff protocols between agents
- Hard stops, escalations, and timeouts
- Constitutional document requirements
- Quality gates and PR workflows

### Why Your Review Matters

CP wrote this methodology based on observation and design intent. But documentation often diverges from reality. We need to know:

1. What actually happens vs. what the document says happens
2. Where friction exists that isn't acknowledged
3. What practices emerged organically that should be codified
4. What's over-engineered or impractical
5. What's missing that you wish was documented

### What We'll Do With Your Feedback

Your report goes back to CP for incorporation into FORGE v1.1. This isn't about defending the document — it's about making it true.

---

## Review Framework

Structure your report using these seven sections:

### 1. Accuracy Assessment

For each major section of the FORGE document, rate accuracy:

| Section | Accuracy | Notes |
|---------|----------|-------|
| Agent Roles (Part 2) | ✅ Accurate / ⚠️ Partially / ❌ Inaccurate | [Specifics] |
| Five Steps (Part 3) | ✅ / ⚠️ / ❌ | [Specifics] |
| Canonical Record (Part 4) | ✅ / ⚠️ / ❌ | [Specifics] |
| Handoff Protocols (Part 5) | ✅ / ⚠️ / ❌ | [Specifics] |
| Hard Stops & Escalations (Part 6) | ✅ / ⚠️ / ❌ | [Specifics] |
| Constitutional Docs (Part 7) | ✅ / ⚠️ / ❌ | [Specifics] |
| Repository Structure (Part 8) | ✅ / ⚠️ / ❌ | [Specifics] |
| Quality Gates (Part 9) | ✅ / ⚠️ / ❌ | [Specifics] |

### 2. What's Missing

Document practices we actually follow on Vantage that aren't captured in FORGE:

- Informal patterns that work
- Communication shortcuts
- Decision-making heuristics
- Recovery patterns when things go wrong
- Anything you do repeatedly that isn't documented

### 3. What's Idealized

Identify parts of the document that sound good but don't match execution reality:

- Processes we skip or shortcut
- Handoffs that are messier than documented
- Timeouts we don't actually enforce
- Quality gates we sometimes bypass
- Escalation paths we don't actually use

Be specific. "We don't really do X" is more useful than "this section needs work."

### 4. Handoff Friction Analysis

For each documented handoff, assess real-world friction:

| Handoff | Documented | Reality | Friction Points |
|---------|------------|---------|-----------------|
| Jordan → CP | Product Concept | [What actually happens] | [Where it breaks down] |
| CP → CC | Constitutional Docs + Prompt | [What actually happens] | [Where it breaks down] |
| CC → Cursor | Task Brief | [What actually happens] | [Where it breaks down] |
| Cursor → CC | Handoff Note | [What actually happens] | [Where it breaks down] |
| CC → Leo | Pull Request | [What actually happens] | [Where it breaks down] |

### 5. Timing Reality Check

The document specifies durations and timeouts. How do these compare to Vantage reality?

| Phase/Activity | Documented | Actual (Vantage) | Notes |
|----------------|------------|------------------|-------|
| Frame | ~1 week | [Reality] | |
| Orchestrate | ~3 days | [Reality] | |
| Refine | ~2 weeks | [Reality] | |
| Govern | ~3 days | [Reality] | |
| Execute (per PR) | 3 day timeout | [Reality] | |

### 6. The CC-Cursor Loop: Deep Dive

Since you live in the Execute phase, provide detailed feedback on:

**Task Brief Quality:**
- Are the documented task brief templates what you actually produce?
- What information do you include that isn't in the template?
- What information is missing that would help Cursor?

**Cursor Handoffs:**
- How does Cursor actually signal completion?
- What does the real handoff note look like?
- Where does context get lost?

**PR Workflow:**
- Does the documented flow match reality?
- What housekeeping actually happens?
- How do you actually track progress in build-plan.md?

**Escalation Reality:**
- Have you actually used the escalation protocol?
- What triggers escalation in practice?
- How do escalations actually get resolved?

### 7. Recommended Changes

Based on your review, provide specific, actionable recommendations:

**Must Fix (Inaccurate):**
- [Specific change 1]
- [Specific change 2]

**Should Add (Missing):**
- [Addition 1]
- [Addition 2]

**Consider Removing (Over-engineered):**
- [Removal 1]
- [Removal 2]

**Clarify (Ambiguous):**
- [Clarification 1]
- [Clarification 2]

---

## THE CRITICAL SECTION: The Execution Engine

**This is the most important part of your review.**

The FORGE document describes phases and handoffs, but it doesn't capture the **actual rhythm** — the real-time, multiple-times-per-day loop that you, Cursor, and Leo run to ship at blistering pace.

We need you to document **exactly how the engine runs**:

### The Real Loop

Describe the actual cycle you run through repeatedly each day:

1. **What triggers you to start a unit of work?**
   - Is it Leo dropping a prompt? Opening a session? Something in build-plan.md?
   
2. **What do you actually do first?**
   - Read docs? Check status? Verify previous PR merged?
   
3. **How do you engage Cursor?**
   - Literally — what does the handoff look like? Verbal? File-based? In-context?
   
4. **How does Cursor signal "done"?**
   - What do you actually see/receive?
   
5. **What's your review process?**
   - Do you run tests? Lint? Read the code? All of it? Some of it?
   
6. **How do you create/commit the PR?**
   - What's the actual sequence of commands/actions?
   
7. **How does Leo engage?**
   - Does he review in GitHub? In Cursor? In conversation with you?
   
8. **What happens after merge?**
   - How do you transition to the next unit of work?
   
9. **How fast is one full cycle?**
   - Minutes? Hours? What's typical for a clean PR?

### The Speed Secrets

What makes this fast? Document the specific practices that enable velocity:

- **Preparation that prevents blockers** — What's set up in advance that keeps things moving?
- **Decisions already made** — What questions DON'T come up because they were answered in constitutional docs?
- **Handoff efficiency** — What makes the CC↔Cursor↔Leo loop tight?
- **Recovery patterns** — When something breaks, how do you get back on track quickly?
- **Parallel work** — Is there any? Or is it strictly sequential?

### The Friction Points

Where does the rhythm break down?

- What causes you to stop and wait?
- What questions come up that shouldn't?
- Where do you lose context?
- What manual steps feel like they should be automated?
- When does Leo have to intervene when he shouldn't need to?

### A Day in the Life

Walk us through a **real, typical execution day** on Vantage:

```
[Time] — [What happened]
[Time] — [What happened]
...
```

Don't idealize it. Show the actual rhythm including interruptions, context switches, and recovery.

### The Undocumented Practices

What do you do that isn't written anywhere but is essential to velocity?

- Naming conventions you follow
- File locations you check
- Mental checklists you run
- Shortcuts you take
- Things you always verify before proceeding

### Decision Heuristics (Unwritten Rules)

Document the rules of thumb you use repeatedly without explicit instruction. This is where velocity actually lives.

- When do you decide to stop Cursor and escalate?
- When do you *not* ask Leo and just proceed?
- What smells trigger a re-read of constitutional docs?
- What tells you a PR is "good enough" vs "needs another cycle"?
- When do you trust your judgment vs. verify against spec?
- What patterns make you confident vs. cautious?

These are not documented anywhere but directly determine speed and quality.

### Kill Switches

Document the termination logic — when to stop, not just when to escalate.

- What signals cause you to immediately stop work?
- What errors are unrecoverable within the current task?
- When do you abandon an approach instead of fixing it?
- What's the difference between "this needs fixing" and "this needs a different approach"?
- When do you throw away work and start over?

This protects velocity by preventing sunk-cost thrash.

### Context Integrity

Context loss is the silent killer of multi-agent systems. Document how you maintain it.

- Where does context most often leak or degrade?
- What do you do to preserve context across Cursor sessions?
- What files or artifacts act as "context anchors" for you?
- What breaks when context is lost?
- How do you recover context after an interruption?
- What would you do differently if context windows were infinite?

### Canonical Truth Resolution

When sources disagree, how do you resolve it?

- If constitutional docs vs. build-plan disagree — which wins?
- If Leo's verbal instruction vs. written spec disagree — which wins?
- If Cursor's output vs. your expectation disagree — what do you do?
- What do you trust first, second, third?
- How do you handle ambiguity when no source is clear?

### If We Lost This

If a new CC instance had to take over tomorrow with only the FORGE document, what would they NOT know that would kill their velocity?

This is the institutional knowledge we need to capture.

---

## Specific Questions for CC

Answer these directly in your report:

1. **Role Boundaries:** Does the documented CC role match what you actually do? What's missing or wrong?

2. **Cursor Relationship:** How would you describe your actual working relationship with Cursor vs. what's documented?

3. **Leo's Involvement:** How often does Leo actually engage during Execute? Is "greenlight and merge" accurate, or is there more?

4. **CP's Involvement:** During Execute, how often do you actually need CP? Does "idle unless escalated" match reality?

5. **Jordan's Involvement:** Has Jordan ever been engaged during Execute on Vantage? Should the document reflect this?

6. **Constitutional Documents:** Are you actually referencing the constitutional docs during implementation? Which ones? How often?

7. **Build-Plan.md:** How do you actually use this file? Is it the "living task list" the document describes?

8. **Biggest Lie:** What's the single biggest gap between the FORGE document and how we actually work?

9. **Biggest Win:** What's the single most accurate and valuable part of the document?

10. **If You Wrote It:** If you were writing this methodology from scratch based on Vantage experience, what would you do differently?

---

## Output Format

Create your report at: `ai_prompts/forge/forge-method-review-2026-01-03.md`

Use this structure:

```markdown
# FORGE Method Ground-Truth Review

**Reviewer:** CC (Claude Code)
**Date:** 2026-01-03
**Project Reference:** Vantage DD
**Document Reviewed:** The FORGE Method™ v1.0

---

## Executive Summary
[2-3 paragraph overview of findings]

## 1. THE EXECUTION ENGINE (MOST IMPORTANT)
### 1.1 The Real Loop
[Step-by-step: What actually happens each cycle]

### 1.2 The Speed Secrets
[What makes this fast]

### 1.3 The Friction Points
[Where rhythm breaks down]

### 1.4 A Day in the Life
[Timeline of a real execution day]

### 1.5 Undocumented Practices
[Institutional knowledge not captured anywhere]

### 1.6 Decision Heuristics
[Unwritten rules that govern judgment and speed]

### 1.7 Kill Switches
[When to stop, abandon, or restart]

### 1.8 Context Integrity
[How context is preserved and recovered]

### 1.9 Canonical Truth Resolution
[How conflicts between sources are resolved]

### 1.10 What a New CC Wouldn't Know
[Critical gaps if someone took over tomorrow]

## 2. Accuracy Assessment
[Table and notes]

## 3. What's Missing
[List with explanations]

## 4. What's Idealized  
[List with explanations]

## 5. Handoff Friction Analysis
[Table and analysis]

## 6. Timing Reality Check
[Table and analysis]

## 7. The CC-Cursor Technical Deep Dive
[Detailed subsections]

## 8. Recommended Changes
[Categorized recommendations]

## 9. Direct Answers
[Responses to the 10 specific questions]

## 10. Appendix: Universal vs. Contextual Insights
[Label each major insight - see instructions]
```

---

## Labeling Directive

For each major insight in your report, explicitly label it as:

| Label | Meaning | Example |
|-------|---------|---------|
| **Universal** | Applies to any FORGE project | "Always verify previous PR merged before starting" |
| **Contextual** | Vantage-specific | "Check RLS policies against firm_id patterns" |
| **Situational** | Depends on project maturity or risk | "Skip detailed review for trivial changes" |

This prevents overfitting FORGE to Vantage and helps us know what to codify vs. what to leave flexible.

---

## Constraints

- **Be candid.** This isn't about validating the document — it's about improving it.
- **Be specific.** "This section is wrong" isn't useful. "This section says X but we actually do Y" is useful.
- **Reference Vantage.** Ground your feedback in actual experience, not theory.
- **Don't defend.** If something doesn't work, say so. We can fix it.
- **Don't expand scope.** This is a review task, not a rewrite task. Identify issues; CP will fix them.

---

## Timeline

This is a priority task but not blocking your current Vantage PR work. Complete when you have a natural break in implementation.

**Suggested approach:**
1. Read the FORGE document fully
2. Reflect on Vantage experience
3. Draft report in one session
4. Review for completeness
5. Deliver to `ai_prompts/forge/`

---

## Success Criteria

- [ ] **Section 1 (Execution Engine) is comprehensive and specific** — This is the most important deliverable
- [ ] The real CC-Cursor-Leo loop is documented step-by-step
- [ ] Speed secrets and friction points are identified
- [ ] **Decision heuristics captured** — The unwritten rules of judgment
- [ ] **Kill switches documented** — When to stop, abandon, restart
- [ ] **Context integrity practices captured** — How context is preserved
- [ ] **Canonical truth resolution documented** — How conflicts are resolved
- [ ] "A Day in the Life" provides concrete timeline
- [ ] Undocumented practices are captured
- [ ] All review sections completed
- [ ] All specific questions answered
- [ ] **Insights labeled as Universal / Contextual / Situational**
- [ ] Specific, actionable recommendations provided
- [ ] Report grounded in Vantage experience, not theory
- [ ] Candid assessment (not defensive of current practices OR the document)

---

## What Happens Next

1. Leo reviews your report
2. Leo shares with CP
3. CP incorporates feedback into FORGE v1.1
4. Updated methodology becomes the new canonical reference
5. Future projects benefit from Vantage learnings

Your feedback directly shapes how we work on every future project. Take your time and make it count.

---

**End of Brief**
