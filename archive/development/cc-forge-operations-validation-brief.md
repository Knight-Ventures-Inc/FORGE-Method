# CP → CC: FORGE Operations Manual Validation

**From:** CP (Claude Project)  
**To:** CC (Claude Code)  
**Date:** 2026-01-04  
**Type:** Methodology Validation Task  
**Priority:** High  
**Output Location:** `ai_prompts/forge/forge-operations-review-2026-01-04.md`

---

## Objective

Review the **FORGE Operations Manual v1.1** (`ai_prompts/forge/forge-operations.md`) and validate whether it accurately captures how we actually work.

Your ground-truth review was incorporated into this document. Now we need you to confirm: **Did we get it right?**

---

## Context

Based on your comprehensive review, we built the FORGE Operations Manual to capture:
- The 16-step FORGE Cycle
- The verification sequence
- Decision heuristics (fix vs escalate vs abandon)
- Kill switches
- Context integrity protocols
- Canonical truth hierarchy
- File-based handoff mechanics

This document is intended to be **reusable across all future FORGE projects** — not Vantage-specific.

---

## Your Task

### 1. Accuracy Check

For each major section, confirm accuracy:

| Section | Accurate? | Notes |
|---------|-----------|-------|
| The FORGE Cycle (Part 1) | ✅ / ⚠️ / ❌ | |
| Verification Sequence (Part 2) | ✅ / ⚠️ / ❌ | |
| Decision Heuristics (Part 3) | ✅ / ⚠️ / ❌ | |
| Kill Switches (Part 4) | ✅ / ⚠️ / ❌ | |
| Context Integrity (Part 5) | ✅ / ⚠️ / ❌ | |
| Canonical Truth Resolution (Part 6) | ✅ / ⚠️ / ❌ | |
| File-Based Handoffs (Part 7) | ✅ / ⚠️ / ❌ | |
| Task Brief Construction (Part 8) | ✅ / ⚠️ / ❌ | |
| Build Plan as State Machine (Part 9) | ✅ / ⚠️ / ❌ | |
| What New Team Members Must Know (Part 10) | ✅ / ⚠️ / ❌ | |
| Speed Secrets Summary (Part 11) | ✅ / ⚠️ / ❌ | |

### 2. Vantage Contamination Check

**Critical:** This document should be FORGE-universal, not Vantage-specific.

Flag any content that is:
- Vantage-specific and should be removed
- Vantage-specific but incorrectly labeled as [UNIVERSAL]
- Missing [CONTEXTUAL] or [SITUATIONAL] labels

We want to ship a clean, reusable methodology — not a Vantage manual.

### 3. Missing Elements

Is anything missing that you do consistently but isn't captured?

Your original review was thorough, but during translation to document form, we may have:
- Oversimplified something important
- Lost nuance in formatting
- Missed an implicit practice

### 4. Overcomplicated Elements

Is anything in the document more complex than reality?

If we over-engineered something that's actually simple in practice, flag it.

### 5. New CC Onboarding Test

Imagine a new CC instance reads only this Operations Manual (plus FORGE Core).

**Could they:**
- [ ] Understand what The FORGE Cycle is?
- [ ] Run the verification sequence correctly?
- [ ] Know when to fix vs escalate vs abandon?
- [ ] Recover context at session start?
- [ ] Maintain the build plan correctly?
- [ ] Write an effective task brief?

If any answer is "no" or "maybe," explain what's missing.

---

## Output Format

```markdown
# FORGE Operations Manual Validation

**Reviewer:** CC (Claude Code)
**Date:** 2026-01-04
**Document Reviewed:** forge-operations.md v1.1

---

## 1. Accuracy Check
[Table with assessments and notes]

## 2. Vantage Contamination
[List any Vantage-specific content that should be removed or relabeled]

## 3. Missing Elements
[Anything important that didn't make it into the document]

## 4. Overcomplicated Elements
[Anything simpler in reality than documented]

## 5. New CC Onboarding Test
[Assessment of whether a new CC could operate from this document]

## 6. Verdict
[Overall assessment: Ready to ship? Needs revision?]

## 7. Specific Line-Level Feedback (Optional)
[Any specific corrections or suggestions]
```

---

## Constraints

- **Be honest.** If we got something wrong, say so.
- **Be specific.** "Section 3 is wrong" isn't useful. "Section 3.2 says X but reality is Y" is useful.
- **Focus on universality.** Flag anything Vantage-specific.
- **Don't expand scope.** This is validation, not a rewrite request.

---

## What Happens Next

Your validation determines whether FORGE Operations Manual is ready for:
1. Use on our next internal project
2. Publication to theforgemethod.org
3. GitHub repo seeding

If you approve, we ship. If you flag issues, CP revises.

---

## Note on Vantage Work

This is a methodology task, not a Vantage feature task. Complete when you have a natural break in PR work. Do not let this block Vantage progress.

---

**End of Brief**
