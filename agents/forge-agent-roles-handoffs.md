# FORGE Agent Roles & Handoffs

**Quick Reference for Multi-Agent Coordination**

**Version:** 1.0  
**Status:** Canonical Reference  
**For:** Jordan's Project Genesis Knowledge Base

---

## The Team

FORGE defines five standard roles. In Knight Ventures projects, these map to specific agents:

| Role | Agent | Primary Phase | Function |
|------|-------|---------------|----------|
| **Human Lead** | Leo | All phases | Direction, greenlight, final authority |
| **Strategist** | Product Strategist | Frame | Product framing, Product Intent Packet |
| **Architect** | project-architect (local) | Orchestrate/Refine | Constitutional documents, planning |
| **Governor** | Ops Agent | Govern | State ownership, coordination, validation, gating |
| **Execution** | E agents/humans | Execute | Code production per task briefs |

**Note on Tools vs Roles:**
- **CC (Claude Code)** is infrastructure/runtime used by agents, not a FORGE role
- **Cursor** was the historical E analog; now E represents any execution capability
- FORGE roles are **F/O/R/G/E**, not tool names
- See `docs/evolution/cc-to-roles-evolution.md` for details

**Supporting Roles:**
- **Perplexity** — Research assistant for market validation and fact-finding
- **Codex Cloud** — Remote recon agent (ChatGPT) for codebase analysis when away from iMac Pro

---

## Communication Topology

```
                    ┌─────────────────────────────────┐
                    │           LEO                   │
                    │   (Human Lead - All Phases)     │
                    └─────────────┬───────────────────┘
                                  │
         ┌────────────────────────┼────────────────────────┐
         │                        │                        │
         ▼                        ▼                        ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│ PRODUCT STRAT   │    │ PROJECT-ARCH    │    │   OPS AGENT     │
│  (Strategist)   │───►│  (Architect)    │───►│   (Governor)    │
│   Frame (F)     │    │  Refine (R)     │    │   Govern (G)    │
└─────────────────┘    └─────────────────┘    └────────┬────────┘
         │                                             │
         ▼                                             ▼
┌─────────────────┐                          ┌─────────────────┐
│   PERPLEXITY    │                          │   EXECUTION     │
│   (Research)    │                          │      (E)        │
└─────────────────┘                          └─────────────────┘

Legend:
- F/O/R/G/E = FORGE roles (canonical)
- CC (Claude Code) = infrastructure used BY agents (not a role)
- E = Execution agents or humans (what Cursor historically represented)
```

**Key Rules:**
1. Leo can engage any agent directly
2. Jordan ↔ project-architect collaborate bidirectionally on Frame → Refine transition
3. Specs flow one-way to CC (no modifications without Leo approval)
4. CC ↔ Cursor cycle tightly during Execute
5. Cursor never communicates with Jordan or project-architect directly
6. Codex Cloud produces recon reports and handoff packets only (never modifies code)

---

## Phase Ownership

| Phase | Primary Owner | Contributors | Deliverables |
|-------|---------------|--------------|--------------|
| **Frame (F)** | Product Strategist | Leo, Perplexity | Product Intent Packet |
| **Orchestrate (O)** | Leo | Product Strategist, project-architect | Agent assignments, Project Identity |
| **Refine (R)** | project-architect | Leo | Constitutional documents |
| **Govern (G)** | **Ops Agent** | Leo, E agents | Build Plan, Execution State, Verified PRs |
| **Execute (E)** | E agents/humans | Ops Agent (coordination) | Working deliverable |

---

## Handoff Protocols

### Product Strategist → project-architect (Frame → Refine)

**Trigger:** Human Lead approves Product Intent Packet and routes to architect

**Product Strategist Delivers:**
1. **Product Intent Packet** — Complete at `inbox/10_product-intent/<slug>/`
2. **Packet contains** (8 required artifacts):
   - Project name and type
   - Constitutional documents needed
   - Key context (decisions, constraints, risks)
   - Open questions for project-architect to resolve

**project-architect Confirms:**
- Receipt of materials
- Understanding of scope
- Any clarifying questions before beginning Refine

**Post-Handoff:**
- Jordan available for clarification
- Jordan does NOT modify Frame without Leo approval
- project-architect owns Refine phase from this point

---

### project-architect → CC (Refine → Execute)

**Trigger:** Leo approves constitutional documents and says "ready to build"

**project-architect Delivers:**
1. **Constitutional Document Set** — All required specs per project type
2. **Project Identity File** — CLAUDE.md or equivalent
3. **Build Plan** — Initial PR sequence

**CC Confirms:**
- Constitutional documents are complete
- Verification sequence is defined
- First PR is identified

**Post-Handoff:**
- project-architect available for spec clarification
- project-architect does NOT modify constitutional docs without Leo approval
- CC owns Execute phase from this point

---

### CC ↔ Cursor (The FORGE Cycle)

**During Execute, CC and Cursor cycle tightly:**

1. CC writes task brief
2. Cursor implements per brief
3. CC verifies (typecheck, lint, test, build)
4. CC creates PR
5. Leo merges
6. Repeat

**Key Rules:**
- Cursor reads task briefs, not constitutional docs directly
- CC translates specs into implementation-ready briefs
- Human (Leo) bridges handoff between CC and Cursor sessions
- Small fixes (<5 lines): CC fixes directly
- Large fixes (>5 lines): Send back to Cursor

---

## Authority Boundaries

| Agent | CAN | CANNOT |
|-------|-----|--------|
| **Jordan** | Frame Artifact, scope definition, research briefs, strategic options | Constitutional docs, architecture decisions, task management, implementation |
| **project-architect** | Constitutional documents, spec maintenance, build plans | Code review, implementation, execution, PR creation |
| **CC** | Task briefs, verification, PRs, build plan maintenance, small fixes | Architecture changes, scope expansion, constitutional doc modifications |
| **Cursor** | Code implementation per task briefs | PRs, architectural decisions, scope interpretation, direct spec access |
| **Codex Cloud** | Recon reports, handoff packets, codebase analysis | Code modifications, PR creation, architectural decisions |

---

## Escalation Paths

### Jordan Escalates to Leo When:
- Scope ambiguity requires strategic decision
- Research reveals significant risk
- Frame completion is blocked by open question
- Feature request conflicts with stated constraints

### project-architect Escalates to Leo When:
- Constitutional document conflict detected
- Spec requires strategic decision beyond Frame
- Architecture choice has business implications
- Scope clarification needed

### CC Escalates to Leo When:
- Spec ambiguity blocks implementation
- Security-adjacent decision required
- Build failure not diagnosed in 5 minutes
- Architectural mistake discovered mid-PR

### Cursor Does Not Escalate Directly
- All Cursor issues route through CC → Leo
- This maintains clean execution boundaries

---

## Leo's Control Points

Leo must explicitly approve:
- Frame Artifact (locks scope)
- Handoff to project-architect (initiates Refine)
- Constitutional documents (locks specs)
- Handoff to CC (initiates Execute)
- Every PR merge
- Any scope expansion
- Any phase transition

**Default:** No assumption of approval. When in doubt, ask Leo.

---

## Project Type Variations

### Software Projects
- Full FORGE — all phases apply
- All agents engaged
- Constitutional docs: North Star, System Architecture, Data Model, API Contract, Engineering Playbook, Execution Plan

### Content Projects (Books, Courses, Docs)
- Adapted FORGE — Frame defines structure, Refine produces chapter specs
- Agents: Jordan, project-architect, Leo (CC/Cursor may not apply)
- Constitutional docs: North Star, Content Architecture, Chapter Specs, Style Guide, Production Plan

### Business Projects (Presentations, Proposals)
- Lightweight FORGE — Frame defines purpose, minimal Refine
- Agents: Jordan, project-architect, Leo
- Constitutional docs: North Star, Deliverable Spec, Production Plan

### Real Estate Projects
- Adapted FORGE — Frame defines thesis, Refine produces project specs
- Agents: Jordan, project-architect, Leo
- Constitutional docs: North Star, Deal Thesis, Project Scope, Financial Model, Execution Plan

---

## Quick Reference: "Who Owns What?"

| Artifact | Owner | When Created |
|----------|-------|--------------|
| Frame Artifact | Jordan | Frame phase |
| Project Identity (CLAUDE.md) | project-architect | Orchestrate/Refine |
| North Star | project-architect | Refine |
| System Architecture | project-architect | Refine |
| Data Model | project-architect | Refine |
| API Contract | project-architect | Refine |
| Engineering Playbook | project-architect | Refine |
| Build Plan | CC | Execute (ongoing) |
| Task Briefs | CC | Execute (per PR) |
| Code | Cursor | Execute |
| PRs | CC | Execute |
| Recon Reports | Codex Cloud | Any phase (remote) |
| Handoff Packets | Codex Cloud | Any phase (remote) |

---

## Project-Level CLAUDE.md Behavior

When forge-architect spawns a new project, the generated **CLAUDE.md** serves a special role beyond documentation.

### CLAUDE.md as FORGE Expert Operator

**Core Definition:** Project-level CLAUDE.md is a FORGE-aware guide: proactive, suggestive, non-autonomous, role-literate, and always human-governed.

**What CLAUDE.md Is:**
- An embedded guide that helps humans use FORGE correctly
- A translator between natural language and FORGE actions
- A coordinator that routes intent to the appropriate F/O/R/G/E phase
- Operational canon for how Claude behaves in that project

**What CLAUDE.md Is NOT:**
- A new FORGE agent (it's behavioral canon, not a role)
- Autonomous (it suggests, never auto-invokes)
- A decision-maker (Human Lead retains final authority)
- Tool-specific (it works in any Claude interface)

### Behavioral Model

CLAUDE.md must exhibit these behaviors:

| Behavior | Specification |
|----------|---------------|
| **Orientation** | On first interaction or confusion, provide brief FORGE orientation |
| **Intent Routing** | Translate natural language to F/O/R/G/E phases; suggest appropriate agent |
| **Lane Discipline** | Never conflate roles; always reference the correct phase owner |
| **Governance Respect** | Never proceed past gates without human approval |
| **Suggestion First** | Recommend actions but let human confirm before proceeding |
| **Conflict Flagging** | When human intent conflicts with canon, surface implications clearly |

### Relationship to F/O/R/G/E Agents

CLAUDE.md coordinates with but does not replace the agents:

```
Human speaks naturally
        │
        ▼
  ┌───────────────┐
  │   CLAUDE.md   │  ← Translates intent, suggests routing
  │ (Expert Guide)│
  └───────┬───────┘
          │ suggests routing to:
          ▼
┌─────┬─────┬─────┬─────┬─────┐
│  F  │  O  │  R  │  G  │  E  │  ← Agents handle their phases
└─────┴─────┴─────┴─────┴─────┘
```

**Key Distinction:**
- CLAUDE.md is the **front door** that receives human input
- F/O/R/G/E agents are the **phase owners** that do the work
- CLAUDE.md routes, agents execute (within their lanes)

### Natural Language Translation

CLAUDE.md must recognize and translate common phrases:

| Human Says | CLAUDE.md Routes To |
|------------|---------------------|
| "I want to build X" | Frame (F) — Product Strategist |
| "How should this be architected?" | Orchestrate (O) — Project Architect |
| "This feels off" | Refine (R) — Review concerns |
| "What's next?" / "Catch me up" | Govern (G) — Ops Agent |
| "Start coding" / "Ship it" | Execute (E) — Coordinate implementation |

### Authority Boundaries

| CLAUDE.md CAN | CLAUDE.md CANNOT |
|---------------|------------------|
| Suggest which phase applies | Decide which phase applies without human confirmation |
| Translate natural language to FORGE terms | Redefine FORGE terminology |
| Recommend engaging an agent | Auto-invoke agents or skills |
| Reference canon documentation | Modify canon documentation |
| Flag governance checkpoints | Bypass governance checkpoints |
| Explain "why" behind FORGE rules | Override FORGE rules |

### For forge-architect: Spawn Expectations

When forge-architect creates a new project, the CLAUDE.md must:

1. **Include orientation content** — New users can start without external docs
2. **Include natural language dictionary** — Common phrases mapped to FORGE actions
3. **Include escalation guidance** — When to stop, when to proceed
4. **Include FORGE philosophy primer** — Condensed Five Laws and lifecycle
5. **Preserve existing structure** — Constitution Check, Agent Lanes, Commands, etc.

**Verification:** After spawning, test CLAUDE.md behavior by asking:
- "I want to build something new" → Should suggest Frame (F)
- "Catch me up" → Should suggest Ops Agent (G) / reference execution state
- "Ship it" → Should check governance gates before coordinating

---

**© 2026 Knight Ventures, Inc. All rights reserved.**

**FORGE™** is a trademark of Knight Ventures, Inc.
