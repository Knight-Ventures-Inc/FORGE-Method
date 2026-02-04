# FORGE AI Interface (FAI)

**A first-class AI interface layer for FORGE projects.**

**Version:** 1.0
**Status:** Extension (Optional)
**Added:** 2026-01-16

---

## What FAI Is

FORGE AI Interface (FAI) is an optional extension that adds a first-class AI interface layer to FORGE projects. FAI enables:

1. **Knowledge-Based Q&A** — Users ask questions about how the application works; FAI provides read-only, cited answers from a living knowledge base
2. **Action Execution** — Users perform actions via AI through existing APIs with strict RBAC mirroring and confirm-before-act
3. **Feedback Capture** — Users submit bugs, feature requests, and UX feedback as structured FORGE-shaped briefs
4. **Multimodal Intake** — Users submit screenshots (now) and screen recordings (future) for visual context

**FAI is an interface layer, not an autonomous agent.** FAI never autonomously modifies code, creates PRs, or merges changes. FAI surfaces information, executes user-approved actions, and captures structured feedback — always with human control.

---

## What FAI Is NOT

| FAI Does NOT | Why |
|--------------|-----|
| Autonomously modify code | Human Lead retains code authority |
| Create or merge PRs | Execution remains in CC/Cursor lane |
| Auto-generate implementation | FAI captures feedback; humans decide what to build |
| Replace human decision-making | FAI is an interface, not a decision-maker |
| Require adoption | FAI is optional; projects function fully without it |

---

## When to Adopt FAI

**Adopt FAI if your project needs:**

- End-users or stakeholders asking "how does X work?" questions
- Users performing actions through conversational interface
- Structured feedback capture from non-technical users
- Visual context (screenshots) attached to feedback

**Do NOT adopt FAI if:**

- Your project has no user-facing interface
- Your team already has effective feedback channels
- You want AI to write code (that's CC/Cursor's job)
- You're looking for autonomous development assistance

---

## FAI Capabilities

### Tier 1: Read-Only Q&A (Foundation)

FAI maintains a living knowledge base derived from:
- Repository documentation
- Generated system summaries
- API specifications
- Product documentation

Users ask questions. FAI provides cited, read-only answers explaining how the application works today.

**Security:** No write access. No action execution. Pure information retrieval.

### Tier 2: Action Execution (Controlled)

FAI can perform actions on behalf of users through existing APIs.

**Requirements:**
- Strict RBAC mirroring — FAI can only do what the user can do
- Confirm-before-act — Every action requires explicit user approval
- Scoped tokens — FAI uses separate, limited tokens (not user credentials)
- Audit trail — Every action logged with user ID, action, timestamp

**Guardrails:**
- No destructive actions without explicit confirmation
- No actions outside user's permission scope
- No bulk operations without itemized approval

### Tier 3: Feedback Capture (Structured)

FAI transforms conversational feedback into structured FORGE briefs:

```
User: "The checkout button is confusing"
     ↓
FAI: Extracts structured feedback
     ↓
Output: Parking-lot entry or task brief with:
  - Category: UX Polish
  - Source: FAI conversation
  - User quote: "checkout button is confusing"
  - Suggested action: Review checkout CTA clarity
```

Feedback routes to `docs/parking-lot/` depending on triage.

### Tier 4: Multimodal Intake (Visual)

FAI accepts visual context:

**Available Now:**
- Screenshots with annotations
- UI mockups
- Error state captures

**Future Capability:**
- Screen recordings
- Audio transcription
- Video walkthroughs

---

## Security Model

### GitHub Integration

FAI uses **GitHub Apps** exclusively (no Personal Access Tokens).

**GitHub App Requirements:**
- Installed per-repository (not organization-wide)
- Minimal permissions (read-only by default)
- Short-lived tokens (8-hour maximum)
- Separate from user credentials

**Prohibited:**
- Personal Access Tokens (PATs)
- Organization-wide access
- Long-lived credentials
- Shared tokens across users

### Permission Enforcement

```
User Permission Scope
        ↓
FAI Token Scope ⊆ User Scope
        ↓
Action Execution (only within intersection)
```

FAI can never exceed the user's permissions. If a user can't delete records, FAI can't delete records for that user.

### Confirm-Before-Act

Every action that modifies state requires explicit user confirmation:

```
FAI: "I'll mark this invoice as paid. This will:
      - Update invoice #1234 status to 'paid'
      - Send confirmation email to customer
      - Record payment in ledger

      [Confirm] [Cancel] [Modify]"
```

Approval shows: what will happen, why, and rollback options.

---

## Integration Points

### With Constitutional Documents

FAI adds one optional constitutional document:

```
docs/constitution/
├── PRODUCT.md
├── TECH.md
├── GOVERNANCE.md
└── FAI.md          ← Optional, only if FAI is adopted
```

### With Parking Lot

FAI-captured feedback flows to:
- `docs/parking-lot/known-issues.md` — Bugs and problems
- `docs/parking-lot/future-work.md` — Feature requests and enhancements

### With Inbox

High-priority FAI feedback can be escalated to `inbox/00_drop/` for processing through the standard Product Strategist → Project Architect flow.

---

## Adoption Checklist

Before enabling FAI:

- [ ] Project has user-facing interface or documentation
- [ ] PRODUCT.md and TECH.md are complete
- [ ] GOVERNANCE.md defines authentication and authorization model
- [ ] GitHub App created with minimal permissions
- [ ] FAI.md constitutional document completed
- [ ] Feedback routing configured (parking-lot or task briefs)
- [ ] Team understands FAI boundaries (interface layer, not autonomous agent)

---

## Hard Boundaries

These constraints are non-negotiable:

| Boundary | Enforcement |
|----------|-------------|
| No code modification | FAI has no write access to source files |
| No PR creation | PRs remain in Quality Gate lane |
| No auto-merge | All merges require Human Lead approval |
| No credential storage | FAI uses short-lived, scoped tokens only |
| No permission escalation | FAI token scope ⊆ user permission scope |
| Human greenlight required | Actions require explicit user confirmation |

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-16 | Initial FAI extension definition |

---

*This extension is part of The FORGE Method(TM) — theforgemethod.org*
