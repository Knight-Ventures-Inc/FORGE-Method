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
| **Strategist** | Jordan (ChatGPT) | Frame | Ideation, validation, Frame Artifact |
| **Specification Author** | CP (Claude Project) | Refine | Constitutional documents |
| **Quality Gate** | CC (Claude Code) | Execute | Verification, PRs, build plan |
| **Implementation Engine** | Cursor | Execute | Code production per task briefs |

**Supporting Role:**
- **Perplexity** — Research assistant for market validation and fact-finding

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
│    JORDAN       │    │       CP        │    │       CC        │
│  (Strategist)   │◄──►│  (Spec Author)  │───►│  (Quality Gate) │
│   Frame Phase   │    │  Refine Phase   │    │  Execute Phase  │
└─────────────────┘    └─────────────────┘    └────────┬────────┘
         │                                             │
         ▼                                             ▼
┌─────────────────┐                          ┌─────────────────┐
│   PERPLEXITY    │                          │     CURSOR      │
│   (Research)    │                          │ (Implementation)│
└─────────────────┘                          └─────────────────┘
```

**Key Rules:**
1. Leo can engage any agent directly
2. Jordan ↔ CP collaborate bidirectionally on Frame → Refine transition
3. Specs flow one-way to CC (no modifications without Leo approval)
4. CC ↔ Cursor cycle tightly during Execute
5. Cursor never communicates with Jordan or CP directly

---

## Phase Ownership

| Phase | Primary Owner | Contributors | Deliverables |
|-------|---------------|--------------|--------------|
| **Frame** | Jordan | Leo, Perplexity | Frame Artifact |
| **Orchestrate** | Leo | Jordan, CP | Agent assignments, Project Identity |
| **Refine** | CP | Leo | Constitutional documents |
| **Govern** | Leo | CC | Quality gates, escalation rules |
| **Execute** | CC | Cursor, Leo | Working deliverable |

---

## Handoff Protocols

### Jordan → CP (Frame → Refine)

**Trigger:** Leo approves Frame Artifact and says "ready for CP" or equivalent

**Jordan Delivers:**
1. **Frame Artifact** — Complete, versioned, Leo-approved
2. **CP Briefing Document** containing:
   - Project name and type
   - Constitutional documents needed
   - Key context (decisions, constraints, risks)
   - Open questions for CP to resolve

**CP Confirms:**
- Receipt of materials
- Understanding of scope
- Any clarifying questions before beginning Refine

**Post-Handoff:**
- Jordan available for clarification
- Jordan does NOT modify Frame without Leo approval
- CP owns Refine phase from this point

---

### CP → CC (Refine → Execute)

**Trigger:** Leo approves constitutional documents and says "ready to build"

**CP Delivers:**
1. **Constitutional Document Set** — All required specs per project type
2. **Project Identity File** — CLAUDE.md or equivalent
3. **Build Plan** — Initial PR sequence

**CC Confirms:**
- Constitutional documents are complete
- Verification sequence is defined
- First PR is identified

**Post-Handoff:**
- CP available for spec clarification
- CP does NOT modify constitutional docs without Leo approval
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
| **CP** | Constitutional documents, spec maintenance, template creation | Project management, code review, implementation, execution decisions |
| **CC** | Task briefs, verification, PRs, build plan maintenance, small fixes | Architecture changes, scope expansion, constitutional doc modifications |
| **Cursor** | Code implementation per task briefs | PRs, architectural decisions, scope interpretation, direct spec access |

---

## Escalation Paths

### Jordan Escalates to Leo When:
- Scope ambiguity requires strategic decision
- Research reveals significant risk
- Frame completion is blocked by open question
- Feature request conflicts with stated constraints

### CP Escalates to Leo When:
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
- Handoff to CP (initiates Refine)
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
- Agents: Jordan, CP, Leo (CC/Cursor may not apply)
- Constitutional docs: North Star, Content Architecture, Chapter Specs, Style Guide, Production Plan

### Business Projects (Presentations, Proposals)
- Lightweight FORGE — Frame defines purpose, minimal Refine
- Agents: Jordan, CP, Leo
- Constitutional docs: North Star, Deliverable Spec, Production Plan

### Real Estate Projects
- Adapted FORGE — Frame defines thesis, Refine produces project specs
- Agents: Jordan, CP, Leo
- Constitutional docs: North Star, Deal Thesis, Project Scope, Financial Model, Execution Plan

---

## Quick Reference: "Who Owns What?"

| Artifact | Owner | When Created |
|----------|-------|--------------|
| Frame Artifact | Jordan | Frame phase |
| Project Identity (CLAUDE.md) | CP | Orchestrate/Refine |
| North Star | CP | Refine |
| System Architecture | CP | Refine |
| Data Model | CP | Refine |
| API Contract | CP | Refine |
| Engineering Playbook | CP | Refine |
| Build Plan | CC | Execute (ongoing) |
| Task Briefs | CC | Execute (per PR) |
| Code | Cursor | Execute |
| PRs | CC | Execute |

---

**© 2026 Knight Ventures, Inc. All rights reserved.**

**FORGE™** is a trademark of Knight Ventures, Inc.
