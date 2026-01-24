# FORGE Stakeholder Interface

**Supra-tenant visibility and feedback system for FORGE projects.**

**Version:** 1.1
**Status:** Extension (Required for Software Projects)
**Added:** 2026-01-23

---

## What the Stakeholder Interface Is

The Stakeholder Interface is a **supra-tenant visibility and feedback system** that provides platform-level transparency for every FORGE SaaS project. It provides:

1. **Product Visibility** — Stakeholders see roadmap, milestones, and progress
2. **Structured Feedback** — Bugs, features, questions captured in usable format
3. **Priority Signals** — Voting influences (but doesn't decide) priority
4. **AI Assistance** — Stakeholder Interface AI explains and captures (Day One)

**Supra-Tenant:** The Stakeholder Portal belongs to the SaaS platform itself, not to any organization, firm, or venture. Stakeholders see the platform; they do not see tenant data.

**The Stakeholder Interface is the first deployable artifact of any FORGE project.** Stakeholders log in and interact before MVP code exists. This is Stakeholder-First FORGE.

---

## What the Stakeholder Interface Is NOT

| Stakeholder Interface Does NOT | Why |
|-------------------------------|-----|
| Replace internal project management | Teams use their own tools; stakeholders see the portal |
| Give stakeholders execution authority | Voting informs; humans decide and prioritize |
| Show internal implementation details | Stakeholders see outcomes, not sprint mechanics |
| Require external tools | Replaces Notion, Monday, Linear for stakeholder communication |

---

## Platform Plane Context

The Stakeholder Interface operates in the **platform plane**, not the tenant plane.

| Attribute | Platform Plane (Stakeholder Portal) | Tenant Plane (App) |
|-----------|-------------------------------------|-------------------|
| **Scope** | System-wide | Per organization |
| **Content** | Roadmap, milestones, feedback | Business data |
| **Visibility** | All stakeholders | Org members only |
| **Access** | Invite-only platform membership | Org membership |

### Session Isolation

Stakeholders access the portal through platform sessions, which are completely isolated from tenant sessions:

- Stakeholder session → Stakeholder Portal only
- Tenant session → Tenant app for specific org only

Switching between planes requires logout/login. No cross-visibility is permitted.

See: [Auth/RBAC - Platform vs Tenant Planes](./auth-rbac.md#platform-vs-tenant-planes)

---

## Stakeholder-First FORGE

**Stakeholders are the first live users of any FORGE project.**

This is not a philosophical statement — it's an operational requirement:

```
Stand-Up (Phase 0)
├── Auth/RBAC deployed
├── Stakeholder Interface deployed ← Stakeholders log in HERE
└── Discovery running

Frame (Phase 1)
├── Stakeholders already engaged
├── Feedback loop established
└── North Star informed by real input
```

By the time Frame completes, stakeholders have been participating for weeks. They are not passive observers waiting for MVP.

---

## What Stakeholders See

### Visible Content

| Content | Description | Source |
|---------|-------------|--------|
| **Vision/North Star** | What we're building and why | Discovery → Frame |
| **Current Phase** | Where we are in FORGE lifecycle | Manual or automated |
| **Milestones** | Key deliverables and dates | Build Plan |
| **Status Updates** | What happened, what's next | Team posts |
| **Submissions** | All stakeholder feedback | Stakeholders |
| **Vote Counts** | Priority signals from stakeholders | Stakeholders |

### NOT Visible to Stakeholders

| Hidden | Why |
|--------|-----|
| Sprint planning | Internal execution mechanics |
| Task breakdowns | Noise for non-implementers |
| Architectural decisions | Technical detail not relevant |
| Internal discussions | Team-only context |
| Unreviewed drafts | Not ready for external eyes |

**Principle:** The Stakeholder Interface shows **outcomes and progress**, not **process and mechanics**.

---

## What Stakeholders Can Do

### Submit Feedback

Stakeholders submit structured feedback:

| Type | Description |
|------|-------------|
| **Bug** | Something isn't working as expected |
| **Feature** | Request for new capability |
| **Question** | Clarification or inquiry |
| **Feedback** | General input or reaction |

Submissions are structured, not freeform. This makes them actionable.

### Vote on Submissions

Stakeholders vote to signal priority:

- **Upvote only** — No downvotes (avoids adversarial dynamics)
- **One vote per submission** — Prevents gaming
- **Totals visible** — Counts shown, individual voters hidden
- **Informs, not decides** — Humans triage and prioritize

### Interact with AI

See: [Stakeholder Interface AI](#stakeholder-interface-ai-foundational) below.

### What Stakeholders Cannot Do

| Prohibited | Why |
|------------|-----|
| Change scope directly | Submissions are inputs, not decisions |
| Mark work as accepted | Admin authority only |
| Bypass triage | All submissions reviewed by humans |
| Access internal tools | Stakeholder surface is scoped |

---

## Stakeholder Interface AI (Foundational)

Every Stakeholder Interface ships with an **AI assistant**. This is not optional — it is a required component of the interface.

### What Stakeholder Interface AI Does (Day One)

| Capability | Description |
|------------|-------------|
| **Explain** | North Star, FORGE phases, milestones, system overview |
| **Answer** | Questions about the project (read-only, from visible content) |
| **Capture** | Feedback, bugs, features, questions → structured records |
| **Learn** | Individual stakeholder context (profile, history, preferences) |

### What Stakeholder Interface AI Does NOT Do (Day One)

| Prohibited | Why |
|------------|-----|
| **Execute tasks** | No "go do X" commands |
| **Activate work** | No task creation in dev backlog |
| **Prioritize** | No ordering or ranking decisions |
| **Access internals** | Only sees portal-visible content |
| **Mutate data** | Except feedback/submission records |

### The Critical Distinction

**Stakeholder Interface AI (Foundational):**
- Available Day One
- Explains and captures
- Read-only + feedback intake
- Required component

**FAI-for-execution (Future):**
- Maturity-gated
- Performs actions on behalf of users
- Requires explicit enablement
- See: [FAI Overview](./fai-overview.md)

These are the **same AI identity** with **different capability surfaces**, unlocked over time.

### AI Response Boundaries

The AI must clearly communicate its boundaries:

**When asked to explain:**
> "The North Star for this project is [X]. We're currently in the Execute phase, working toward the [milestone] deadline."

**When asked to capture feedback:**
> "I'll record that as a feature request. Would you like to add any additional context?"

**When asked to execute:**
> "I can explain how that works, but I can't make changes. Would you like me to submit this as a request for the team?"

---

## Shared Visibility

**All stakeholders see all submissions within their organization.**

This enables:
- Avoiding duplicate submissions
- Building on others' ideas
- Collective voting on priorities
- Transparency among stakeholders

Submissions are **never** visible cross-organization. Tenant isolation is absolute.

---

## Feedback Lifecycle

Submissions follow a defined lifecycle:

```
New → Triaged → In Progress → Resolved
                                  │
                            or → Won't Fix
```

| Status | Meaning | Set By |
|--------|---------|--------|
| New | Just submitted | System |
| Triaged | Reviewed, accepted | Admin/Member |
| In Progress | Being worked on | Admin/Member |
| Resolved | Completed | Admin/Member |
| Won't Fix | Declined with explanation | Admin/Member |

Stakeholders see status changes. They do not control them.

---

## When to Adopt

### Required For:

- All FORGE software projects
- Any project with external stakeholders
- Any project needing structured feedback

### Adoption Checklist

Before Phase 0 (Stand-Up) completes:

- [ ] Auth/RBAC deployed (dependency)
- [ ] Stakeholder Interface deployed (even if content is minimal)
- [ ] At least one stakeholder invited
- [ ] Feedback submission working
- [ ] Stakeholder Interface AI configured
- [ ] Status update capability exists

---

## Integration Points

### With Auth/RBAC

The Stakeholder Interface requires Auth/RBAC:
- `stakeholder` role gates access
- User identity attributes feedback
- Org context scopes all content

### With Discovery Pack

Discovery produces content for the interface:
- North Star becomes visible to stakeholders
- Milestones derive from discovery decisions
- Vision statements inform AI explanations

### With FAI-for-execution (Future)

When enabled, FAI extends Stakeholder Interface AI:
- Same interface, expanded capabilities
- Execution requires explicit confirmation
- Capability tiers unlock progressively

This is explicitly deferred. See [FAI Overview](./fai-overview.md).

---

## Hard Boundaries

These constraints are non-negotiable:

| Boundary | Enforcement |
|----------|-------------|
| Stakeholder AI is required | Not optional on Day One |
| AI explains, does not execute | No action capabilities initially |
| Voting informs, does not decide | Humans triage |
| Tenant isolation is absolute | No cross-org visibility |
| First-party only | No external tools for stakeholder communication |

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-23 | Initial Stakeholder Interface extension definition |

---

*This extension is part of The FORGE Method(TM) — theforgemethod.org*
