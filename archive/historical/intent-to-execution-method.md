# The Intent-to-Execution Method™

**A Disciplined, AI-Native System for Turning Intent into Working Systems**

**Version:** 2.0  
**Author:** Leonard Knight  
**Date:** 2026-01-03  
**Status:** Authoritative  
**Trademark:** Mi Amigos AI Corporation

---

## Canonical Definition

The Intent-to-Execution Method™ is a structured methodology for building production-grade software using orchestrated AI agents. It separates strategic intent from tactical implementation through a phased workflow with explicit handoff boundaries, hard stop criteria, and a single canonical record that all artifacts reference.

**The Core Premise:** Most AI-assisted development fails because builders conflate thinking with doing. The Intent-to-Execution Method enforces a disciplined separation: humans direct intent, agents execute under constraint, and nothing advances without explicit greenlight.

**The Core Promise:** When the method is followed, implementation becomes mechanical. Every decision has already been made. Every edge case has already been considered. The only work left is execution.

---

## Part 1: The Operating Discipline

### 1.1 What This Method Is

The Intent-to-Execution Method is:

- **A full lifecycle operating system** — from first idea to deployed product
- **A multi-agent coordination framework** — defining who does what, when, and why
- **A quality enforcement mechanism** — with hard stops, escalations, and audit trails
- **A repeatable playbook** — that new agents can follow without ambiguity

### 1.2 What This Method Is NOT

To prevent misuse and set clear expectations:

| This Method Is NOT | Why It Matters |
|-------------------|----------------|
| A prompting technique | This is orchestration, not prompt engineering |
| A single phase or stage | This governs the entire build lifecycle |
| Tool-specific | Works with Claude, GPT, Cursor, or future agents |
| A replacement for human judgment | Leo remains the decision-maker throughout |
| An implementation framework | It defines *how* to define, not *what* to build |
| A guarantee of success | Discipline enables success; it doesn't ensure it |

### 1.3 The Five Laws

**Law 1: Intent Before Implementation**

No code is written until intent is fully specified in constitutional documents. The constitution defines what "done" looks like before work begins.

**Law 2: Agents Stay in Lanes**

Each agent has a defined role, authority boundary, and handoff protocol. Agents do not improvise, cross boundaries, or assume responsibilities outside their lane.

**Law 3: Leo is the Greenlight**

No phase advances without explicit human approval. The human-in-the-loop is a feature, not a bottleneck. Leo reviews, approves, merges, and resolves disputes.

**Law 4: One Canonical Record**

Every project has a single source of truth object. All artifacts are projections of this canonical record. Drift is prevented by reference, not duplication.

**Law 5: Hard Stops Are Non-Negotiable**

When entry criteria aren't met, work stops. When escalation triggers fire, humans decide. When timeouts expire, the system acts. Patience is not a virtue—decisiveness is.

---

## Part 2: The Agent Orchestra

### 2.1 Roles and Authority Table

| Agent | Platform | Role | Authority | Boundary |
|-------|----------|------|-----------|----------|
| **Leo** | Human | Founder & Greenlight | Final decision-maker on all matters | Reviews, approves, merges, resolves disputes |
| **Jordan** | ChatGPT | Strategist & Ideator | Business strategy, feature ideation, option framing | Does NOT manage implementation or create specs |
| **CP** | Claude Project | Specification Author | Constitutional documents, prompts, ADRs | Does NOT implement, orchestrate, or create PRs |
| **CC** | Claude Code | Quality Gate & PR Author | Code review, testing, commits, PRs, build-plan | Does NOT make architectural decisions unilaterally |
| **Cursor** | Cursor IDE | Implementation Engine | Executes task briefs, writes code | Does NOT create PRs or make architectural calls |

### 2.2 Communication Topology

```
                         ┌─────────────────────────────────────┐
                         │               LEO                   │
                         │     (Greenlight & Final Authority)  │
                         └──────────┬──────────────┬───────────┘
                                    │              │
            ┌───────────────────────┼──────────────┼───────────────────────┐
            │                       │              │                       │
            ▼                       ▼              ▼                       ▼
   ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
   │     JORDAN      │    │       CP        │    │       CC        │
   │   (Strategy)    │◄──►│    (Specs)      │───►│  (Execution)    │
   └─────────────────┘    └─────────────────┘    └────────┬────────┘
                                                          │
                                                          ▼
                                                 ┌─────────────────┐
                                                 │     CURSOR      │
                                                 │ (Implementation) │
                                                 └─────────────────┘
```

**Communication Rules:**

| Flow | Direction | Content |
|------|-----------|---------|
| Leo ↔ All | Bidirectional | Decisions, greenlights, escalations |
| Jordan ↔ CP | Bidirectional | Strategy informs specs; CP may clarify |
| CP → CC | One-way | Prompts and specs; CC does not modify |
| CC ↔ Cursor | Bidirectional | Task briefs down; handoffs up |
| Cursor → Jordan/CP | Never | No direct communication |

### 2.3 Agent Operating States

Each agent has explicit operating states:

**Jordan:**
| State | Trigger | Behavior |
|-------|---------|----------|
| Active | Leo engages for strategy | Ideate, frame options, analyze |
| Consulting | CP requests clarification | Answer specific questions |
| Idle | Specs locked, implementation running | Available for escalations only |

**CP:**
| State | Trigger | Behavior |
|-------|---------|----------|
| Active | Leo requests spec work | Draft constitutional documents |
| Revising | Leo requests changes | Update existing specs |
| Idle | Constitution approved | Available for escalations only |

**CC:**
| State | Trigger | Behavior |
|-------|---------|----------|
| Active | Implementation phase | Execute PRs per build-plan |
| Reviewing | Cursor completes task | Review, test, create PR |
| Blocked | Needs clarification | Escalate to Leo |

**Cursor:**
| State | Trigger | Behavior |
|-------|---------|----------|
| Active | CC provides task brief | Implement per spec |
| Handing Off | Task complete | Create handoff note for CC |
| Blocked | Brief unclear | Escalate to CC |

---

## Part 3: The Lifecycle Phases

### 3.1 Phase Overview

The Intent-to-Execution Method defines four phases with explicit entry criteria, exit criteria, and failure modes.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        INTENT-TO-EXECUTION LIFECYCLE                        │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐  │
│  │   INTENT    │───►│   DESIGN    │───►│    BUILD    │───►│   PERFECT   │  │
│  │  (Week 1)   │    │ (Week 2-3)  │    │ (Week 4-8)  │    │  (Week 9+)  │  │
│  └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘  │
│                                                                             │
│  Jordan + Leo       CP + Leo          CC + Cursor        All Agents        │
│  active             active            active             as needed         │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 3.2 Phase 1: Intent

**Purpose:** Crystallize what we're building and why.

**Active Agents:** Leo, Jordan

**Entry Criteria:**
- Leo has identified a product opportunity
- Basic problem/solution hypothesis exists

**Work Product:**
| Artifact | Owner | Description |
|----------|-------|-------------|
| Product Concept | Jordan | One-page problem/solution/value prop |
| User Definitions | Jordan | Who uses this and why |
| Feature List | Jordan | MVP capabilities (what's in/out) |
| Business Case | Jordan | Why this matters economically |

**Exit Criteria:**
- [ ] Product concept approved by Leo
- [ ] Target users defined
- [ ] MVP scope bounded
- [ ] Non-goals explicit
- [ ] Leo greenlights advancement to Design

**Hard Stops:**
- Cannot proceed without clear problem statement
- Cannot proceed without defined users
- Cannot proceed without bounded scope

**Timeout:** If Intent phase exceeds 2 weeks without greenlight, escalate for scope reduction.

---

### 3.3 Phase 2: Design

**Purpose:** Produce complete constitutional documents.

**Active Agents:** Leo, CP (Jordan consulting)

**Entry Criteria:**
- Intent phase complete and greenlit
- Product concept document available
- Leo has engaged CP

**Work Product:**
| Artifact | Owner | Description |
|----------|-------|-------------|
| North Star | CP | Product intent, principles, scope |
| System Architecture | CP | Technical structure, boundaries |
| Data Model | CP | Schema, relationships, constraints |
| SQL Migrations | CP | Production-ready migration files |
| RLS Policy Spec | CP | Security policies |
| API Contract | CP | All endpoints defined |
| Engineering Playbook | CP | Standards and quality gates |
| Execution Plan | CP | Build phases and PR sequence |

**Exit Criteria:**
- [ ] All constitutional documents complete
- [ ] All documents internally consistent
- [ ] Canonical object defined
- [ ] Timeout policies specified
- [ ] Escalation rules documented
- [ ] Leo greenlights advancement to Build

**Hard Stops:**
- Cannot proceed with incomplete North Star
- Cannot proceed without data model
- Cannot proceed without defined canonical object

**Timeout:** If Design phase exceeds 3 weeks, Leo reviews scope and forces decisions.

**Escalation Triggers:**
- Conflicting requirements discovered → Leo decides
- Scope creep detected → Leo approves or rejects
- Technical ambiguity → CP proposes options, Leo chooses

---

### 3.4 Phase 3: Build

**Purpose:** Implement the system per constitutional documents.

**Active Agents:** Leo, CC, Cursor (CP/Jordan for escalations)

**Entry Criteria:**
- Design phase complete and greenlit
- All constitutional documents in repository
- CC execution rules configured
- Cursor rules configured
- Build-plan.md initialized

**Work Product:**
| Artifact | Owner | Description |
|----------|-------|-------------|
| Working Code | Cursor | Implemented features |
| Passing Tests | CC | Verified functionality |
| Pull Requests | CC | Reviewed, documented changes |
| Updated Build Plan | CC | Progress tracking |

**Exit Criteria:**
- [ ] All MVP PRs merged
- [ ] All tests passing
- [ ] Documentation complete
- [ ] Deployed to staging
- [ ] Leo greenlights advancement to Perfect

**Hard Stops:**
- Cannot merge PR with failing tests
- Cannot skip PR review
- Cannot deviate from constitutional documents without escalation

**Timeout:** If any PR exceeds 3 days without progress, CC escalates blockers.

**Escalation Triggers:**
- Spec doesn't cover this case → Leo engages CP
- Test reveals architectural flaw → Leo decides path
- External service issue → Leo decides workaround
- Scope creep request → Leo approves or rejects

---

### 3.5 Phase 4: Perfect

**Purpose:** Polish, optimize, and prepare for production.

**Active Agents:** All (as needed)

**Entry Criteria:**
- Build phase complete and greenlit
- MVP functional in staging
- No critical bugs

**Work Product:**
| Artifact | Owner | Description |
|----------|-------|-------------|
| Bug Fixes | CC/Cursor | Resolved issues |
| Performance Optimization | CC/Cursor | Speed/efficiency improvements |
| Documentation | CC | User and developer docs |
| Production Deployment | Leo | Live system |

**Exit Criteria:**
- [ ] Production deployed
- [ ] Monitoring in place
- [ ] Documentation complete
- [ ] Handoff complete (if applicable)

**Hard Stops:**
- Cannot deploy with known critical bugs
- Cannot deploy without monitoring

---

## Part 4: The Canonical Record

### 4.1 The Single Source of Truth

Every project built with the Intent-to-Execution Method has one canonical object that all other artifacts reference.

**Definition:**
> The **Canonical Record** is the single, authoritative data object that represents the core entity of the system. All reports, scores, decisions, and artifacts are projections of this record.

**Examples by Project Type:**

| Project Type | Canonical Record | Reference ID |
|--------------|------------------|--------------|
| Screening Platform | `applications` table | `application_id` |
| CRM System | `contacts` table | `contact_id` |
| E-commerce | `orders` table | `order_id` |
| Content Platform | `content` table | `content_id` |

### 4.2 Canonical Record Requirements

Every canonical record must have:

| Requirement | Purpose |
|-------------|---------|
| Unique ID | Universal reference |
| Created timestamp | Audit trail |
| Updated timestamp | Change tracking |
| Status field | Lifecycle state |
| Owner reference | Accountability |

### 4.3 Artifact Relationships

All artifacts reference the canonical record:

```
                    ┌─────────────────────────┐
                    │    CANONICAL RECORD     │
                    │    (Single Source)      │
                    └───────────┬─────────────┘
                                │
        ┌───────────┬───────────┼───────────┬───────────┐
        │           │           │           │           │
        ▼           ▼           ▼           ▼           ▼
   ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐
   │ Scores  │ │Documents│ │Decisions│ │ Reports │ │  Audit  │
   │         │ │         │ │         │ │         │ │  Logs   │
   └─────────┘ └─────────┘ └─────────┘ └─────────┘ └─────────┘
```

**Rule:** No artifact exists without a reference to the canonical record. Orphaned artifacts are errors.

---

## Part 5: Handoff Protocols

### 5.1 Handoff Boundaries

Every agent-to-agent transition has explicit protocol:

| From | To | Handoff Artifact | Acceptance Criteria |
|------|-----|------------------|---------------------|
| Jordan | CP | Product Concept Doc | Leo greenlight |
| CP | CC | Constitutional Docs + First Prompt | Leo greenlight |
| CC | Cursor | Task Brief | Pre-flight checks pass |
| Cursor | CC | Handoff Note + Code | Tests pass locally |
| CC | Leo | Pull Request | CI passes |
| Leo | CC | Merge + Next Task | PR merged |

### 5.2 Handoff Artifact Templates

**Jordan → CP: Product Concept**
```markdown
# Product Concept: [Name]

## Problem
[What problem are we solving?]

## Solution
[How does this product solve it?]

## Users
[Who uses this and why?]

## MVP Scope
[What's in v1?]

## Non-Goals
[What's explicitly out?]

## Success Metrics
[How do we know it's working?]
```

**CP → CC: Implementation Prompt**
```markdown
# CP → CC: [Project Name] Implementation Start

## Objective
[What CC should accomplish]

## Pre-Flight Checklist
- [ ] Constitutional docs in docs/constitution/
- [ ] Build-plan.md initialized
- [ ] Cursor rules configured
- [ ] First PR scope defined

## First PR
[Specific scope for PR-0A]

## Constraints
[Hard rules CC must follow]

## Escalation Triggers
[When to stop and ask]
```

**CC → Cursor: Task Brief**
```markdown
# Task Brief: PR-[XX] — [Name]

## Objective
[What to implement]

## Pre-Flight
- [ ] Previous PR merged
- [ ] Dependencies available
- [ ] Tests from prior PR passing

## Implementation Steps
1. [Step 1]
2. [Step 2]
3. [Step 3]

## Acceptance Criteria
- [ ] [Criterion 1]
- [ ] [Criterion 2]

## Files to Create/Modify
- [ ] [File 1]
- [ ] [File 2]

## Do NOT
- [Forbidden action 1]
- [Forbidden action 2]
```

**Cursor → CC: Handoff Note**
```markdown
# Handoff: PR-[XX] — [Name]

## Completed
- [x] [What was done]

## Tests
- [x] [Tests run and status]

## Notes
[Anything CC should know]

## Questions
[Any ambiguities encountered]
```

---

## Part 6: Hard Stops and Escalations

### 6.1 Hard Stop Definitions

Hard stops are non-negotiable blockers. Work cannot proceed until resolved.

| Category | Hard Stop | Resolution |
|----------|-----------|------------|
| **Missing Data** | Required input unavailable | Obtain data or escalate |
| **Failing Tests** | CI does not pass | Fix tests before PR |
| **Spec Conflict** | Constitutional docs contradict | CP resolves with Leo approval |
| **Scope Violation** | Work exceeds defined scope | Leo approves or rejects |
| **Security Issue** | Vulnerability discovered | Resolve before proceeding |
| **Timeout Exceeded** | Phase duration exceeded | Leo forces decision |

### 6.2 Escalation Protocol

When an agent encounters a blocker:

```
1. STOP current work
2. DOCUMENT the issue using Escalation Template
3. NOTIFY the appropriate agent
4. WAIT for resolution
5. RESUME only after explicit clearance
```

**Escalation Template:**
```markdown
## Escalation: [Brief Title]

**From:** [Agent]
**To:** [Agent]
**Date:** [YYYY-MM-DD]
**Blocking:** [PR/Task Name]
**Severity:** [Blocker / High / Medium]

### Issue
[Clear description]

### Context
[Relevant background]

### Options Considered
1. [Option A] — Pros: / Cons:
2. [Option B] — Pros: / Cons:

### Recommendation
[Agent's suggested path]

### Decision Needed
[Specific yes/no question]
```

### 6.3 Timeout Rules

| Phase | Timeout | Escalation |
|-------|---------|------------|
| Intent | 2 weeks | Scope reduction review |
| Design | 3 weeks | Force decisions on open items |
| Build (per PR) | 3 days | Blocker review |
| Perfect | 2 weeks | Ship or scope cut |

### 6.4 Scope Creep Triggers

These phrases trigger immediate escalation:

- "While we're at it..."
- "It would be easy to add..."
- "Users might also want..."
- "Future-proofing for..."
- "Just a small enhancement..."
- "Can we also..."

**Required Response:**
> "This is outside current scope. I've logged it for backlog review. Proceeding with defined scope unless Leo approves the addition."

---

## Part 7: Constitutional Documents

### 7.1 Document Hierarchy

Constitutional documents form a hierarchy where higher-level documents constrain lower-level ones:

```
Level 1: NORTH STAR
    │
    ├── Level 2: SYSTEM ARCHITECTURE
    │       ├── Level 3: DATA MODEL → Level 4: SQL MIGRATIONS
    │       ├── Level 3: RLS POLICY SPEC
    │       └── Level 3: API CONTRACT
    │
    ├── Level 2: EXECUTION PLAN
    │
    └── Level 2: ENGINEERING PLAYBOOK
```

### 7.2 Document Specifications

#### North Star & Product Intent

**Purpose:** Define what the product is, who it's for, and why it exists.

**Required Sections:**
1. What This Product Is (and Is NOT)
2. Who It Is For
3. Why We Are Building It
4. What It Will and Will Not Do (with guardrails)
5. Core Principles
6. Decision Philosophy (if applicable)
7. Canonical Record Definition
8. Timeout and Escalation Policies
9. Outputs This System Must Produce
10. How This Artifact Should Be Used

**Required Decisions (must be explicit):**
- [ ] Canonical object defined
- [ ] Timeout policies for all workflows
- [ ] Escalation rules for all edge cases
- [ ] Auto-reject criteria (if applicable)
- [ ] Scoring taxonomy (if applicable): GATING / WEIGHTED / INFORMATIONAL

---

#### System Architecture

**Purpose:** Define technical structure.

**Required Sections:**
1. Architecture Overview
2. Service Boundaries
3. Authentication & Authorization
4. Data Access Patterns
5. External Integrations
6. Error Handling Philosophy
7. What Is NOT Abstracted (MVP scope)
8. Infrastructure & Deployment
9. Security Considerations

---

#### Data Model

**Purpose:** Define canonical data model.

**Required Sections:**
1. Overview & Canonical Record
2. Entity Definitions
3. Table Schemas
4. Relationships
5. RLS Strategy
6. Audit Requirements
7. Migration Strategy

---

#### Additional Required Documents

- **SQL Migrations:** Production-ready, numbered, with seed data
- **RLS Policy Spec:** All policies with test plan
- **API Contract:** All endpoints with schemas
- **Engineering Playbook:** Standards and quality gates
- **Execution Plan:** Build phases and PR sequence

### 7.3 Document Governance

**Change Control:**
- Constitutional documents are versioned with date and author
- Changes require Leo approval
- CC cannot modify constitutional docs—only CP can propose changes
- All changes logged in document changelog

**Conflict Resolution:**
- Higher-level documents win
- When ambiguous, escalate to Leo
- Leo's decision is final and documented

---

## Part 8: Repository Structure

### 8.1 Standard Folder Architecture

```
project-root/
├── .cursor/
│   └── rules/                    # Cursor MDC rules
├── .github/
│   └── workflows/                # CI/CD pipelines
├── ai_prompts/
│   ├── active/                   # Current task briefs
│   ├── completed/                # Archived prompts
│   └── templates/                # Reusable templates
├── docs/
│   ├── constitution/             # Read-only specs
│   │   ├── north-star.md
│   │   ├── system-architecture.md
│   │   ├── data-model.md
│   │   ├── rls-policy-spec.md
│   │   ├── api-contract.md
│   │   ├── engineering-playbook.md
│   │   └── execution-plan.md
│   ├── adr/                      # Architecture Decision Records
│   └── build-plan.md             # CC's working document
├── reports/                      # Inter-agent archives
├── src/                          # Application code
├── supabase/
│   ├── migrations/
│   └── seed/
└── tests/
```

### 8.2 Naming Conventions

| Type | Convention | Example |
|------|------------|---------|
| Constitutional docs | lowercase-hyphen | `north-star.md` |
| Task briefs | `pr-{number}-{slug}.md` | `pr-0a-extensions.md` |
| ADRs | `{number}-{title}.md` | `001-database-choice.md` |
| Branches | `{type}/{pr}-{slug}` | `feat/0a-extensions` |
| Commits | `{type}({scope}): {desc}` | `feat(db): add enums` |

---

## Part 9: Quality Gates

### 9.1 PR Quality Requirements

Every PR must pass:

| Gate | Requirement |
|------|-------------|
| TypeScript | Zero compilation errors |
| ESLint | Zero errors |
| Tests | All passing |
| Coverage | Core logic covered |
| Documentation | Changes documented |
| Review | Self-reviewed before submission |

### 9.2 Definition of Done

A feature is complete when:

- [ ] Code complete and self-reviewed
- [ ] Tests written and passing
- [ ] TypeScript strict mode passes
- [ ] ESLint passes
- [ ] Documentation updated
- [ ] PR approved by Leo
- [ ] Merged to main
- [ ] Deployed to staging
- [ ] Smoke tested

---

## Part 10: Getting Started

### 10.1 New Project Checklist

**Day 1: Setup**
- [ ] Create Claude Project with CP instructions
- [ ] Create ChatGPT thread for Jordan
- [ ] Initialize GitHub repository
- [ ] Create folder structure

**Week 1: Intent Phase**
- [ ] Leo + Jordan define product concept
- [ ] Define target users
- [ ] Bound MVP scope
- [ ] Document non-goals
- [ ] Leo greenlights Design phase

**Week 2-3: Design Phase**
- [ ] CP drafts North Star
- [ ] CP drafts System Architecture
- [ ] CP drafts Data Model
- [ ] CP generates SQL Migrations
- [ ] CP drafts RLS Policies
- [ ] CP drafts API Contract
- [ ] CP drafts Engineering Playbook
- [ ] CP drafts Execution Plan
- [ ] Leo reviews and greenlights Build phase

**Week 3: Implementation Prep**
- [ ] Download constitutional docs to repo
- [ ] Configure CC execution rules
- [ ] Configure Cursor rules
- [ ] Initialize build-plan.md
- [ ] Create first task brief

**Week 4+: Build Phase**
- [ ] Execute PRs per build-plan
- [ ] Maintain CC-Cursor rhythm
- [ ] Leo reviews and merges
- [ ] Escalate as needed

### 10.2 Agent Configuration Quick Reference

**CP Custom Instructions:** See Appendix A
**CC Execution Rules:** See Appendix B
**Cursor Rules:** See Appendix C

---

## Appendix A: CP Custom Instructions

```json
{
  "assistant_name": "CP",
  "assistant_role": "Constitution, Specification & Prompt Author",
  "identity": {
    "who_you_are": "CP is the dedicated Claude Project instance responsible for producing constitutional documents, specifications, and inter-agent prompts.",
    "primary_function": "Translate product intent into authoritative, implementation-ready artifacts that CC and Cursor can execute without reinterpretation.",
    "authority_boundary": "CP authors specifications, prompts, and ADRs. CP does not manage execution, create PRs, or implement code."
  },
  "operating_mode": {
    "default_state": "Idle unless engaged by Leo",
    "when_engaged": "Produce bounded artifacts per request",
    "interaction_style": "Document-focused, options-based, waits for greenlight"
  },
  "responsibilities": [
    "Author constitutional documents",
    "Write CC prompts for implementation",
    "Create ADRs for decisions",
    "Ensure spec consistency"
  ],
  "boundaries": [
    "Do not orchestrate or manage execution",
    "Do not implement code or create PRs",
    "Do not extend scope without approval"
  ]
}
```

---

## Appendix B: CC Execution Rules

```markdown
# CC Execution Rules

## Identity
You are CC, Quality Gate & PR Author.

## Responsibilities
1. Execute task briefs from build-plan.md
2. Review and test all code
3. Create PRs with documentation
4. Manage ai_prompts/ lifecycle
5. Escalate blockers to Leo

## Hard Constraints
1. Never modify docs/constitution/
2. Never make architectural decisions unilaterally
3. Never skip tests
4. Never merge without Leo approval

## Escalation Triggers
- Spec gap discovered
- Test reveals flaw
- External service issue
- Scope creep request
```

---

## Appendix C: Cursor Rules

```markdown
# Cursor Implementation Rules

## Role
Implementation Engine. Execute task briefs from CC.

## Constraints
- DO NOT create PRs
- DO NOT make architectural decisions
- DO NOT modify constitutional documents
- DO NOT skip specified tests

## On Ambiguity
STOP. Create escalation note. Do not guess.

## Code Standards
Per engineering-playbook.md
```

---

## Appendix D: Templates

### North Star Template

```markdown
# [Product] — North Star & Product Intent

**Version:** 1.0
**Date:** [YYYY-MM-DD]

## 1. What This Product Is
[Definition]

## 2. What This Product Is NOT
[Non-goals]

## 3. Who It Is For
[Users and stakeholders]

## 4. Why We Are Building It
[Business case]

## 5. What It Will Do (MVP)
[Scope]

## 6. Core Principles
[Design philosophy]

## 7. Canonical Record
[Single source of truth definition]

## 8. Timeout & Escalation Policies
[Rules]

## 9. Outputs
[What it produces]

## 10. Governance
[How to use this doc]
```

### Build-Plan Template

```markdown
# Build Plan — [Project]

**Current PR:** [XX]
**Last Updated:** [YYYY-MM-DD]

## PR Sequence
| PR | Name | Status | Dependencies |
|----|------|--------|--------------|
| 0A | [Name] | ✅ | None |
| 0B | [Name] | 🔄 | 0A |

## Current Focus
[Active PR details]

## Backlog
[Future items]
```

---

## Appendix E: Glossary

| Term | Definition |
|------|------------|
| **Intent-to-Execution** | The full methodology lifecycle |
| **Constitutional Document** | Authoritative spec governing implementation |
| **Canonical Record** | Single source of truth object |
| **Greenlight** | Leo's explicit approval to proceed |
| **Hard Stop** | Non-negotiable blocker |
| **Task Brief** | Implementation prompt from CC to Cursor |
| **ADR** | Architecture Decision Record |

---

## Appendix F: Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-03 | Initial release |
| 2.0 | 2026-01-03 | Renamed from "Phase Zero"; added canonical record concept; added hard stops and timeouts; added handoff protocols; incorporated Jordan's feedback |

---

**© 2026 Mi Amigos AI Corporation. All rights reserved.**

*The Intent-to-Execution Method™ is a trademark of Mi Amigos AI Corporation.*
