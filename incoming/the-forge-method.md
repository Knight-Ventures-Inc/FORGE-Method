# The FORGE Method™

**Frame. Orchestrate. Refine. Govern. Execute.**

**A Disciplined, AI-Native System for Turning Intent into Working Systems**

**Version:** 1.0  
**Steward:** Knight Ventures, Inc.  
**Date:** 2026-01-03  
**Status:** Canonical Reference  
**Website:** theforgemethod.org

---

## Canonical Definition

**FORGE™** is a structured methodology for building production-grade systems using orchestrated AI agents. It transforms raw intent into working software through five disciplined phases: **Frame** the problem, **Orchestrate** the agents, **Refine** the specifications, **Govern** the execution, and **Execute** the implementation.

**The Core Premise:** Most AI-assisted development fails because builders conflate thinking with doing. FORGE enforces disciplined separation: humans direct intent, agents execute under constraint, and nothing advances without explicit greenlight.

**The Core Promise:** When FORGE is followed, implementation becomes mechanical. Every decision has already been made. Every edge case has already been considered. The only work left is execution.

---

## Part 1: What Is FORGE

### 1.1 The Five Steps

FORGE is an acronym representing five sequential phases:

| Step | Name | Purpose | Primary Agents |
|------|------|---------|----------------|
| **F** | Frame | Define what we're building and why | Leo + Jordan |
| **O** | Orchestrate | Assign agents, configure roles, establish rules | Leo + CP |
| **R** | Refine | Produce constitutional documents | CP + Leo |
| **G** | Govern | Establish quality gates, handoffs, escalations | CP + Leo |
| **E** | Execute | Build the system per specifications | CC + Cursor + Leo |

### 1.2 What FORGE Is

FORGE is:

- **A full lifecycle operating system** — from first idea to deployed product
- **A multi-agent coordination framework** — defining who does what, when, and why
- **A quality enforcement mechanism** — with hard stops, escalations, and audit trails
- **A repeatable playbook** — that new agents can follow without ambiguity
- **A community-governed method** — stewarded by Knight Ventures, improved through contribution

### 1.3 What FORGE Is NOT

| FORGE Is NOT | Why It Matters |
|--------------|----------------|
| A prompting technique | This is orchestration, not prompt engineering |
| Tool-specific | Works with Claude, GPT, Cursor, or future agents |
| A replacement for human judgment | Leo remains the decision-maker throughout |
| An implementation framework | It defines *how* to define, not *what* to build |
| A guarantee of success | Discipline enables success; it doesn't ensure it |
| An investment recommendation | For screening tools: FORGE supports analysis, not decisions |

### 1.4 The Five Laws

**Law 1: Intent Before Implementation**

No code is written until intent is fully specified in constitutional documents. The constitution defines "done" before work begins.

**Law 2: Agents Stay in Lanes**

Each agent has a defined role, authority boundary, and handoff protocol. Agents do not improvise, cross boundaries, or assume responsibilities outside their lane.

**Law 3: Leo is the Greenlight**

No phase advances without explicit human approval. The human-in-the-loop is a feature, not a bottleneck.

**Law 4: One Canonical Record**

Every project has a single source of truth object. All artifacts are projections of this canonical record.

**Law 5: Hard Stops Are Non-Negotiable**

When entry criteria aren't met, work stops. When escalation triggers fire, humans decide. Patience is not a virtue—decisiveness is.

---

## Part 2: The Agent Orchestra

### 2.1 Roles and Authority

| Agent | Platform | Role | Authority Boundary |
|-------|----------|------|-------------------|
| **Leo** | Human | Founder & Greenlight | Final decision-maker; reviews, approves, merges |
| **Jordan** | ChatGPT | Strategist & Ideator | Business strategy, feature ideation; does NOT implement |
| **CP** | Claude Project | Specification Author | Constitutional docs, prompts; does NOT execute |
| **CC** | Claude Code | Quality Gate & PR Author | Code review, testing, PRs; does NOT architect unilaterally |
| **Cursor** | Cursor IDE | Implementation Engine | Executes task briefs; does NOT create PRs |

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
| CP → CC | One-way | Specs and prompts; CC does not modify |
| CC ↔ Cursor | Bidirectional | Task briefs down; handoffs up |
| Cursor → Jordan/CP | Never | No direct communication |

### 2.3 Agent Operating States

**Jordan:**
| State | Trigger | Behavior |
|-------|---------|----------|
| Active | Leo engages for strategy | Ideate, frame options |
| Consulting | CP requests clarification | Answer specific questions |
| Idle | Specs locked | Available for escalations only |

**CP:**
| State | Trigger | Behavior |
|-------|---------|----------|
| Active | Leo requests spec work | Draft constitutional documents |
| Revising | Leo requests changes | Update existing specs |
| Idle | Constitution approved | Available for escalations only |

**CC:**
| State | Trigger | Behavior |
|-------|---------|----------|
| Active | Execute phase begins | Execute PRs per build-plan |
| Reviewing | Cursor completes task | Review, test, create PR |
| Blocked | Needs clarification | Escalate to Leo |

**Cursor:**
| State | Trigger | Behavior |
|-------|---------|----------|
| Active | CC provides task brief | Implement per spec |
| Handing Off | Task complete | Create handoff note |
| Blocked | Brief unclear | Escalate to CC |

---

## Part 3: The Five FORGE Steps

### Step F: Frame

**Purpose:** Define what we're building, who it's for, and why it matters.

**Duration:** ~1 week

**Active Agents:** Leo, Jordan

**Inputs:**
- Product opportunity identified
- Problem/solution hypothesis

**Outputs:**
| Artifact | Owner | Description |
|----------|-------|-------------|
| Product Concept | Jordan | Problem, solution, value prop |
| User Definitions | Jordan | Who uses this and why |
| Feature List | Jordan | MVP capabilities (in/out) |
| Business Case | Jordan | Economic rationale |

**Entry Criteria:**
- Leo has identified an opportunity

**Exit Criteria:**
- [ ] Product concept approved
- [ ] Users defined
- [ ] MVP scope bounded
- [ ] Non-goals explicit
- [ ] Leo greenlights Orchestrate

**Common Failure Modes:**
| Failure | Symptom | Resolution |
|---------|---------|------------|
| Scope creep | "Also..." language | Hard boundary enforcement |
| Vague users | "Everyone" as target | Force specific personas |
| Missing non-goals | No explicit exclusions | Require "What this is NOT" |

**Timeout:** 2 weeks max. If exceeded, escalate for scope reduction.

---

### Step O: Orchestrate

**Purpose:** Configure agents, establish roles, and set coordination rules.

**Duration:** ~3 days

**Active Agents:** Leo, CP

**Inputs:**
- Approved product concept from Frame
- Agent roster available

**Outputs:**
| Artifact | Owner | Description |
|----------|-------|-------------|
| Agent Configuration | CP | Custom instructions per agent |
| Communication Rules | CP | Who talks to whom |
| Escalation Protocol | CP | When and how to escalate |
| Repository Structure | CP | Folder architecture |

**Entry Criteria:**
- Frame complete and greenlit

**Exit Criteria:**
- [ ] All agents configured
- [ ] Communication topology documented
- [ ] Escalation rules defined
- [ ] Repository initialized
- [ ] Leo greenlights Refine

**Common Failure Modes:**
| Failure | Symptom | Resolution |
|---------|---------|------------|
| Role confusion | Agents doing others' work | Explicit boundaries |
| Missing escalation | Issues go unresolved | Document triggers |
| Tool mismatch | Wrong agent for task | Reassign clearly |

---

### Step R: Refine

**Purpose:** Produce complete constitutional documents that govern implementation.

**Duration:** ~2 weeks

**Active Agents:** CP, Leo (Jordan consulting)

**Inputs:**
- Product concept from Frame
- Agent configuration from Orchestrate

**Outputs:**
| Artifact | Owner | Description |
|----------|-------|-------------|
| North Star | CP | Product intent, principles, scope |
| System Architecture | CP | Technical structure |
| Data Model | CP | Schema, relationships |
| SQL Migrations | CP | Production-ready migrations |
| RLS Policy Spec | CP | Security policies |
| API Contract | CP | All endpoints |
| Engineering Playbook | CP | Standards |
| Execution Plan | CP | Build phases, PR sequence |

**Entry Criteria:**
- Orchestrate complete and greenlit

**Exit Criteria:**
- [ ] All constitutional documents complete
- [ ] Documents internally consistent
- [ ] Canonical record defined
- [ ] Leo greenlights Govern

**Common Failure Modes:**
| Failure | Symptom | Resolution |
|---------|---------|------------|
| Incomplete specs | "TBD" in documents | Force decisions |
| Inconsistency | Specs contradict | Reconciliation review |
| Over-engineering | Beyond MVP scope | Scope enforcement |

**Timeout:** 3 weeks max. Leo forces decisions on open items.

---

### Step G: Govern

**Purpose:** Establish quality gates, handoff protocols, and enforcement mechanisms.

**Duration:** ~3 days

**Active Agents:** CP, Leo

**Inputs:**
- Constitutional documents from Refine

**Outputs:**
| Artifact | Owner | Description |
|----------|-------|-------------|
| Quality Gates | CP | PR requirements |
| Handoff Templates | CP | Agent transition formats |
| Timeout Policies | CP | Phase duration limits |
| Hard Stop Definitions | CP | Non-negotiable blockers |
| Build Plan | CP | PR sequence initialized |

**Entry Criteria:**
- Refine complete and greenlit

**Exit Criteria:**
- [ ] All quality gates defined
- [ ] Handoff protocols documented
- [ ] Timeouts specified
- [ ] Hard stops enumerated
- [ ] Build plan initialized
- [ ] Leo greenlights Execute

**Common Failure Modes:**
| Failure | Symptom | Resolution |
|---------|---------|------------|
| Vague gates | "Good enough" acceptance | Explicit criteria |
| Missing timeouts | Work drags indefinitely | Hard limits |
| No escalation path | Issues stuck | Clear routing |

---

### Step E: Execute

**Purpose:** Build the system per constitutional documents.

**Duration:** Variable (typically 4-8 weeks for MVP)

**Active Agents:** CC, Cursor, Leo (CP/Jordan for escalations)

**Inputs:**
- All constitutional documents
- Build plan with PR sequence
- Agent configurations active

**Outputs:**
| Artifact | Owner | Description |
|----------|-------|-------------|
| Working Code | Cursor | Implemented features |
| Passing Tests | CC | Verified functionality |
| Pull Requests | CC | Documented changes |
| Updated Build Plan | CC | Progress tracking |
| Deployed System | Leo | Production release |

**Entry Criteria:**
- Govern complete and greenlit
- All docs in repository
- CC and Cursor configured

**Exit Criteria:**
- [ ] All MVP PRs merged
- [ ] All tests passing
- [ ] Documentation complete
- [ ] Deployed to production
- [ ] Smoke tested

**Common Failure Modes:**
| Failure | Symptom | Resolution |
|---------|---------|------------|
| Spec deviation | Code doesn't match docs | Realign or escalate |
| Test gaps | Untested code merged | Enforce coverage |
| Scope creep | "While we're here..." | Reject; backlog it |

**Timeout:** 3 days per PR max. Blockers escalate to Leo.

---

## Part 4: The Canonical Record

### 4.1 Single Source of Truth

Every FORGE project has one canonical object that all artifacts reference.

**Definition:**
> The **Canonical Record** is the single, authoritative data object representing the core entity of the system. All reports, scores, decisions, and artifacts are projections of this record.

**Examples:**

| Project Type | Canonical Record | Reference ID |
|--------------|------------------|--------------|
| Screening Platform | `applications` table | `application_id` |
| CRM System | `contacts` table | `contact_id` |
| E-commerce | `orders` table | `order_id` |
| Content Platform | `content` table | `content_id` |

### 4.2 Requirements

Every canonical record must have:

| Field | Purpose |
|-------|---------|
| Unique ID | Universal reference |
| Created timestamp | Audit trail |
| Updated timestamp | Change tracking |
| Status | Lifecycle state |
| Owner reference | Accountability |

### 4.3 Artifact Relationships

```
                    ┌─────────────────────────┐
                    │    CANONICAL RECORD     │
                    └───────────┬─────────────┘
                                │
        ┌───────────┬───────────┼───────────┬───────────┐
        ▼           ▼           ▼           ▼           ▼
   ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐
   │ Scores  │ │Documents│ │Decisions│ │ Reports │ │  Audit  │
   └─────────┘ └─────────┘ └─────────┘ └─────────┘ └─────────┘
```

**Rule:** No artifact exists without reference to the canonical record. Orphans are errors.

---

## Part 5: Handoff Protocols

### 5.1 Handoff Boundaries

| From | To | Artifact | Acceptance |
|------|-----|----------|------------|
| Jordan | CP | Product Concept | Leo greenlight |
| CP | CC | Constitutional Docs + Prompt | Leo greenlight |
| CC | Cursor | Task Brief | Pre-flight passes |
| Cursor | CC | Handoff Note + Code | Local tests pass |
| CC | Leo | Pull Request | CI passes |
| Leo | CC | Merge confirmation | PR merged |

### 5.2 Handoff Templates

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
# Implementation Start: [Project]

## Objective
[What CC should accomplish]

## Pre-Flight
- [ ] Constitutional docs in docs/constitution/
- [ ] Build-plan.md initialized
- [ ] Cursor configured
- [ ] First PR scope defined

## First PR
[Specific scope]

## Constraints
[Hard rules]

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

## Steps
1. [Step 1]
2. [Step 2]

## Acceptance Criteria
- [ ] [Criterion 1]
- [ ] [Criterion 2]

## Do NOT
- [Forbidden 1]
- [Forbidden 2]
```

**Cursor → CC: Handoff Note**
```markdown
# Handoff: PR-[XX]

## Completed
- [x] [What was done]

## Tests
- [x] [Status]

## Notes
[Anything CC should know]
```

---

## Part 6: Hard Stops and Escalations

### 6.1 Hard Stop Definitions

| Category | Hard Stop | Resolution |
|----------|-----------|------------|
| Missing Data | Required input unavailable | Obtain or escalate |
| Failing Tests | CI does not pass | Fix before PR |
| Spec Conflict | Documents contradict | CP resolves with Leo |
| Scope Violation | Work exceeds scope | Leo approves or rejects |
| Security Issue | Vulnerability found | Resolve before proceeding |
| Timeout | Phase duration exceeded | Leo forces decision |

### 6.2 Escalation Protocol

```
1. STOP current work
2. DOCUMENT using Escalation Template
3. NOTIFY appropriate agent
4. WAIT for resolution
5. RESUME only after clearance
```

**Escalation Template:**
```markdown
## Escalation: [Title]

**From:** [Agent]
**To:** [Agent]
**Blocking:** [PR/Task]
**Severity:** Blocker / High / Medium

### Issue
[Description]

### Options
1. [Option A] — Pros / Cons
2. [Option B] — Pros / Cons

### Recommendation
[Suggested path]

### Decision Needed
[Specific question]
```

### 6.3 Timeout Rules

| Phase | Timeout | Action |
|-------|---------|--------|
| Frame | 2 weeks | Scope reduction |
| Orchestrate | 1 week | Force configuration |
| Refine | 3 weeks | Force decisions |
| Govern | 1 week | Accept defaults |
| Execute (per PR) | 3 days | Blocker review |

### 6.4 Scope Creep Triggers

These phrases require immediate escalation:

- "While we're at it..."
- "It would be easy to add..."
- "Users might also want..."
- "Future-proofing for..."
- "Just a small enhancement..."

**Required Response:**
> "Outside current scope. Logged for backlog. Proceeding with defined scope unless Leo approves."

---

## Part 7: Constitutional Documents

### 7.1 Document Hierarchy

```
Level 1: NORTH STAR
    ├── Level 2: SYSTEM ARCHITECTURE
    │       ├── Level 3: DATA MODEL → SQL MIGRATIONS
    │       ├── Level 3: RLS POLICY SPEC
    │       └── Level 3: API CONTRACT
    ├── Level 2: EXECUTION PLAN
    └── Level 2: ENGINEERING PLAYBOOK
```

### 7.2 Required Documents

| Document | Purpose | Required Sections |
|----------|---------|-------------------|
| North Star | Product intent | What/Who/Why, Scope, Principles, Canonical Record, Timeouts |
| System Architecture | Technical structure | Boundaries, Auth, Data Patterns, Integrations |
| Data Model | Schema definition | Entities, Tables, Relationships, RLS Strategy |
| SQL Migrations | Database setup | Numbered files, Seed data |
| RLS Policy Spec | Security | Policies, Helper Functions, Test Plan |
| API Contract | Endpoints | Routes, Schemas, Security |
| Engineering Playbook | Standards | Code, Testing, CI/CD |
| Execution Plan | Build phases | PR Sequence, Decision Gates |

### 7.3 Document Governance

- Constitutional documents are versioned
- Changes require Leo approval
- CC cannot modify—only CP proposes changes
- Higher-level documents win conflicts

---

## Part 8: Repository Structure

### 8.1 Standard Architecture

```
project-root/
├── .cursor/rules/
├── .github/workflows/
├── ai_prompts/
│   ├── active/
│   ├── completed/
│   └── templates/
├── docs/
│   ├── constitution/
│   │   ├── north-star.md
│   │   ├── system-architecture.md
│   │   ├── data-model.md
│   │   ├── rls-policy-spec.md
│   │   ├── api-contract.md
│   │   ├── engineering-playbook.md
│   │   └── execution-plan.md
│   ├── adr/
│   └── build-plan.md
├── reports/
├── src/
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

### 9.1 PR Requirements

| Gate | Requirement |
|------|-------------|
| TypeScript | Zero errors |
| ESLint | Zero errors |
| Tests | All passing |
| Coverage | Core logic covered |
| Documentation | Changes documented |
| Review | Self-reviewed |

### 9.2 Definition of Done

- [ ] Code complete and self-reviewed
- [ ] Tests written and passing
- [ ] TypeScript strict passes
- [ ] ESLint passes
- [ ] Documentation updated
- [ ] PR approved by Leo
- [ ] Merged to main
- [ ] Deployed to staging

---

## Part 10: Getting Started

### 10.1 New Project Quickstart

**Day 1: Setup**
- [ ] Create Claude Project (CP)
- [ ] Create ChatGPT thread (Jordan)
- [ ] Initialize GitHub repository
- [ ] Create folder structure

**Week 1: Frame**
- [ ] Define product concept with Jordan
- [ ] Define users and scope
- [ ] Document non-goals
- [ ] Leo greenlights Orchestrate

**Week 1-2: Orchestrate + Refine**
- [ ] Configure agents with CP
- [ ] Draft all constitutional documents
- [ ] Leo reviews and greenlights Govern

**Week 2: Govern**
- [ ] Define quality gates
- [ ] Document handoffs
- [ ] Initialize build-plan.md
- [ ] Leo greenlights Execute

**Week 3+: Execute**
- [ ] Execute PRs per build-plan
- [ ] Leo reviews and merges
- [ ] Deploy MVP

---

## Appendix A: CP Configuration

```json
{
  "assistant_name": "CP",
  "role": "Constitution & Specification Author",
  "authority": "Drafts specs, prompts, ADRs",
  "boundary": "Does not implement, orchestrate, or create PRs",
  "state": "Idle unless engaged by Leo"
}
```

---

## Appendix B: CC Execution Rules

```markdown
# CC Execution Rules

## Identity
Quality Gate & PR Author

## Responsibilities
1. Execute task briefs
2. Review and test code
3. Create PRs
4. Escalate blockers

## Hard Constraints
- Never modify constitution
- Never skip tests
- Never merge without Leo
```

---

## Appendix C: Cursor Rules

```markdown
# Cursor Rules

## Role
Implementation Engine

## Constraints
- Do NOT create PRs
- Do NOT architect
- Do NOT modify constitution
- STOP on ambiguity
```

---

## Appendix D: Glossary

| Term | Definition |
|------|------------|
| FORGE | Frame, Orchestrate, Refine, Govern, Execute |
| Constitutional Document | Authoritative spec governing implementation |
| Canonical Record | Single source of truth object |
| Greenlight | Leo's explicit approval |
| Hard Stop | Non-negotiable blocker |
| Task Brief | Implementation prompt from CC to Cursor |

---

## Appendix E: Governance

### Stewardship

FORGE™ is stewarded by **Knight Ventures, Inc.**

### Evolution

FORGE evolves through community contribution, but coherence is preserved through a stewarded review process.

### Contribution

- Propose improvements via GitHub
- Follow contribution guidelines
- Respect trademark and licensing

### Licensing

FORGE™ is available under a custom permissive license:
- Free to use
- Attribution required
- No claiming ownership
- Knight Ventures retains trademark

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-03 | Initial canonical release |

---

**© 2026 Knight Ventures, Inc. All rights reserved.**

**FORGE™** is a trademark of Knight Ventures, Inc.

*theforgemethod.org*
