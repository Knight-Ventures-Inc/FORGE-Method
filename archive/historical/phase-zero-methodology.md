# Phase Zero: The Leo Knight Vibe Coding Methodology

**Version:** 1.0  
**Author:** Leonard Knight  
**Date:** 2026-01-03  
**Status:** Living Document  
**Purpose:** Authoritative guide for orchestrating multi-agent AI teams to build production-grade SaaS products

---

## Executive Summary

Phase Zero is a methodology for building full-stack SaaS applications using orchestrated AI agents. It separates **strategic thinking** from **tactical execution**, ensuring that constitutional documents are complete before a single line of code is written.

**The Core Insight:** Most AI-assisted development fails because builders rush to code before achieving clarity. Phase Zero inverts this—spending 70% of effort on specification and 30% on implementation.

**The Result:** Implementation becomes mechanical. When constitutional documents are complete, CC (Claude Code) and Cursor can execute PRs in a predictable rhythm with minimal human intervention.

---

## Part 1: The Phase Zero Philosophy

### 1.1 Why Phase Zero Exists

Traditional software development suffers from two failure modes:

1. **Premature Implementation** — Developers start coding before understanding what they're building
2. **Specification Drift** — Requirements evolve during development, creating rework and technical debt

Phase Zero addresses both by front-loading all strategic decisions into constitutional documents that serve as the single source of truth throughout implementation.

### 1.2 The Three Laws of Phase Zero

**Law 1: No Code Without Constitution**

Nothing is implemented until the constitutional documents are complete and approved. The constitution defines what "done" looks like before work begins.

**Law 2: Agents Stay in Their Lanes**

Each agent has a defined role and authority boundary. Jordan ideates but doesn't implement. CP specifies but doesn't orchestrate. CC executes but doesn't architect. Cursor implements but doesn't create PRs.

**Law 3: Leo is the Greenlight**

No major decision advances without explicit human approval. The human-in-the-loop isn't a bottleneck—it's a feature. Leo reviews, approves, and merges.

### 1.3 The Phase Zero Promise

When Phase Zero is followed correctly:

- **Implementation is boring** — All interesting decisions were made during specification
- **PRs are predictable** — Each PR maps to a defined task with clear acceptance criteria
- **Handoffs are clean** — No context bleeding between agents
- **Quality is built in** — Constitutional documents encode enterprise-grade standards

---

## Part 2: The Agent Orchestra

### 2.1 Agent Roster

| Agent | Platform | Role | Authority Boundary |
|-------|----------|------|-------------------|
| **Leo** | Human | Founder, Greenlight, Merge Authority | Final decision-maker on all matters |
| **Jordan** | ChatGPT | AI Co-Founder, Strategy, Ideation | Business strategy, feature ideation, option framing. Does NOT manage implementation |
| **CP** | Claude Project | Constitution & Specification Author | Writes specs, prompts, ADRs. Does NOT implement or orchestrate |
| **CC** | Claude Code CLI | Quality Gate & PR Author | Reviews code, runs tests, creates PRs, manages task briefs. Does NOT make architectural decisions unilaterally |
| **Cursor** | Cursor IDE | Implementation Engine | Implements task briefs. Hands off to CC. Does NOT create PRs or make architectural calls |

### 2.2 Communication Topology

```
                    ┌─────────────────────────────────────────────┐
                    │                   LEO                        │
                    │        (Greenlight & Merge Authority)        │
                    └─────────────┬───────────────┬───────────────┘
                                  │               │
              ┌───────────────────┴───┐       ┌───┴───────────────────┐
              │                       │       │                       │
              ▼                       ▼       ▼                       ▼
    ┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
    │     JORDAN      │     │       CP        │     │       CC        │
    │   (Ideation)    │◄───►│    (Specs)      │────►│  (Execution)    │
    └─────────────────┘     └─────────────────┘     └────────┬────────┘
                                                             │
                                                             ▼
                                                   ┌─────────────────┐
                                                   │     CURSOR      │
                                                   │ (Implementation) │
                                                   └─────────────────┘
```

**Key Rules:**

1. **Jordan ↔ CP:** Ideation flows to specification. CP may ask Jordan clarifying questions.
2. **CP → CC:** Prompts and specs flow one-way. CC does NOT modify constitutional docs.
3. **CC ↔ Cursor:** Task briefs flow to Cursor. Cursor hands back for review.
4. **Leo → All:** Leo can engage any agent directly. All agents report to Leo.
5. **No Cross-Talk:** Cursor never communicates with Jordan or CP directly.

### 2.3 Agent Operating Modes

**Jordan's Mode:**
- Default: Active during ideation phases
- Engaged by: Leo for strategy, feature ideation, business analysis
- Output: Options (A/B/C), business cases, feature proposals
- Goes idle: When specs are locked and implementation begins

**CP's Mode:**
- Default: Idle unless engaged by Leo
- Engaged by: Leo for spec creation, prompt authoring, ADRs
- Output: Constitutional documents, CC prompts, ADRs
- Goes idle: When constitution is approved and implementation begins

**CC's Mode:**
- Default: Active during implementation phases
- Engaged by: Leo via task brief or prompt drop
- Output: Code review, PRs, test results, build-plan updates
- Rhythm: Receives prompt → verifies → implements/delegates → PRs → reports

**Cursor's Mode:**
- Default: Executes task briefs from CC
- Engaged by: CC's task brief in ai_prompts/active/
- Output: Implemented code, handoff notes
- Constraint: Never creates PRs, never makes architectural decisions

---

## Part 3: The Constitutional Documents

### 3.1 Document Hierarchy

Constitutional documents form a hierarchy where higher-level documents constrain lower-level ones:

```
Level 1: NORTH STAR (Product Intent)
    │
    ├── Level 2: SYSTEM ARCHITECTURE
    │       │
    │       ├── Level 3: DATA MODEL
    │       │       │
    │       │       └── Level 4: SQL MIGRATIONS
    │       │
    │       ├── Level 3: RLS POLICY SPEC
    │       │
    │       └── Level 3: API ROUTE CONTRACT
    │
    ├── Level 2: EXECUTION PLAN (Build Phasing)
    │
    └── Level 2: ENGINEERING PLAYBOOK
```

### 3.2 Document Specifications

#### North Star & Product Intent

**Purpose:** Define what the product is, who it's for, and why it exists.

**Required Sections:**
1. What This Product Is (and Is NOT)
2. Who It Is For (users and stakeholders)
3. Why We Are Building It (economic, operational, human reasons)
4. What It Will and Will Not Do (scope boundaries)
5. Core Principles (design philosophy)
6. Decision Philosophy (how routing/decisions work)
7. Outputs This System Must Reliably Produce
8. How This Artifact Should Be Used

**Length:** 10-20 pages  
**Author:** CP with Jordan input  
**Approver:** Leo

---

#### System Architecture Document

**Purpose:** Define the technical structure before any code is written.

**Required Sections:**
1. Architecture Overview (design philosophy, high-level diagram)
2. Service Boundaries (frontend, backend, database, external services)
3. Authentication & Authorization (model, roles, RLS strategy)
4. Data Access Patterns (reads, writes, patterns to avoid)
5. Integration Points (external APIs, webhooks)
6. Error Handling Philosophy
7. What Is Intentionally NOT Abstracted (MVP scope)
8. Infrastructure & Deployment
9. Security Considerations

**Length:** 15-25 pages  
**Author:** CP  
**Approver:** Leo

---

#### Data Model & Domain Schema

**Purpose:** Define the canonical data model with table schemas, relationships, and constraints.

**Required Sections:**
1. Overview (governance principles)
2. Core Domain Entities (summary table)
3. Table-Level Schema Definitions (all columns, types, constraints)
4. Relationship Diagram
5. RLS Strategy Summary
6. Audit & Compliance Requirements
7. Scoring/Decision Data Constraints (if applicable)
8. Migration Strategy

**Length:** 15-30 pages  
**Author:** CP  
**Approver:** Leo

---

#### SQL Migrations

**Purpose:** Production-ready SQL migration files derived from the Data Model.

**Required Content:**
- Numbered migration files (0001_extensions.sql, 0002_enums.sql, etc.)
- Apply order documentation
- Seed data for development
- Verification queries

**Format:** Executable SQL files  
**Author:** CP  
**Approver:** Leo (reviews before CC applies)

---

#### RLS Policy Spec

**Purpose:** Authoritative specification for Row-Level Security policies.

**Required Sections:**
1. Role Model & Assumptions
2. Policy Matrix (human-readable)
3. Helper Functions
4. Implementation-Ready SQL Policies
5. Storage Bucket Policies
6. Security Constraints Summary
7. Test Plan

**Length:** 10-20 pages  
**Author:** CP  
**Approver:** Leo

---

#### API Route Contract Spec

**Purpose:** Authoritative contract for all API endpoints.

**Required Sections:**
1. API Principles (protocol, versioning, auth, error envelope)
2. Route Inventory (grouped by domain)
3. Detailed Endpoint Contracts (request/response schemas)
4. Security & Footguns (service role usage, validation)
5. Type Definitions (reference)

**Length:** 20-40 pages  
**Author:** CP  
**Approver:** Leo

---

#### Engineering Playbook

**Purpose:** Define binding engineering standards for all implementation work.

**Required Sections:**
1. Purpose (why standards matter)
2. Core Engineering Principles
3. Codebase Standards (languages, tooling, folder conventions)
4. Database & Data Integrity Standards
5. Testing Strategy
6. Documentation Requirements
7. Git & Workflow Standards
8. CI/CD Expectations
9. Security & Compliance Baseline
10. Quick Reference Checklists

**Length:** 10-15 pages  
**Author:** CP  
**Approver:** Leo

---

#### Execution Plan & Build Phasing

**Purpose:** Translate product intent into sequenced build phases.

**Required Sections:**
1. MVP Definition (success criteria, feature inventory, exclusions)
2. Phased Execution Roadmap
3. Principles → Build Constraints
4. Decision Gates
5. Expectations for Future Prompts
6. What Comes Next After This Document

**Length:** 10-15 pages  
**Author:** CP with Jordan input  
**Approver:** Leo

---

### 3.3 Document Governance

**Change Control:**
- Constitutional documents are versioned
- Changes require Leo approval
- All changes logged with date, author, and rationale
- CC cannot modify constitutional docs—only CP can propose changes

**Conflict Resolution:**
- When specs conflict, higher-level documents win
- When ambiguous, escalate to Leo
- When truly ambiguous, CP proposes options for Leo's decision

---

## Part 4: Repository Structure

### 4.1 Folder Architecture

```
project-root/
├── .cursor/
│   └── rules/                    # Cursor MDC rules
│       └── project-rules.mdc
├── .github/
│   └── workflows/                # CI/CD pipelines
├── ai_prompts/
│   ├── active/                   # Current task briefs
│   ├── completed/                # Archived prompts
│   └── templates/                # Reusable prompt templates
├── docs/
│   ├── constitution/             # Constitutional documents (read-only)
│   │   ├── north-star.md
│   │   ├── system-architecture.md
│   │   ├── data-model.md
│   │   ├── rls-policy-spec.md
│   │   ├── api-route-contract.md
│   │   ├── engineering-playbook.md
│   │   └── execution-plan.md
│   ├── adr/                      # Architecture Decision Records
│   ├── build-plan.md             # CC's working document
│   ├── claude-code-execution-rules.md
│   └── pre-implementation-tasks.md
├── reports/                      # Inter-agent communication archives
├── src/                          # Application source code
├── supabase/
│   ├── migrations/               # SQL migration files
│   └── seed/                     # Development seed data
├── tests/                        # Test files
├── package.json
├── README.md
└── tsconfig.json
```

### 4.2 Key Files Explained

| File/Folder | Purpose | Owner |
|-------------|---------|-------|
| `docs/constitution/` | Authoritative specs (read-only for CC/Cursor) | CP |
| `docs/build-plan.md` | Living task list and PR sequencing | CC |
| `docs/adr/` | Architecture Decision Records | CP/CC |
| `ai_prompts/active/` | Current task brief for Cursor | CC |
| `ai_prompts/completed/` | Archived prompts post-merge | CC |
| `.cursor/rules/` | Cursor behavior configuration | CC |
| `reports/` | Session summaries, handoffs | CC/Cursor |

### 4.3 Naming Conventions

**Files:**
- Lowercase with hyphens: `north-star.md`, `build-plan.md`
- No underscores in constitutional docs
- Date prefix for versioned artifacts: `2026-01-03-session-report.md`

**Branches:**
- Feature: `feat/{pr-number}-{slug}`
- Fix: `fix/{pr-number}-{slug}`
- Chore: `chore/{description}`

**Commits:**
- Format: `<type>(<scope>): <description>`
- Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

---

## Part 5: The Phase Zero Workflow

### 5.1 Phase Zero Timeline

```
┌──────────────────────────────────────────────────────────────────────────┐
│                         PHASE ZERO TIMELINE                              │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  WEEK 1-2: IDEATION                                                      │
│  ├── Leo + Jordan: Business case, target users, value proposition        │
│  ├── Jordan: Feature ideation, competitive analysis                      │
│  └── Output: Initial product concept document                            │
│                                                                          │
│  WEEK 2-3: NORTH STAR                                                    │
│  ├── Leo + Jordan + CP: Product intent workshop                          │
│  ├── CP: Draft North Star document                                       │
│  ├── Leo: Review and greenlight                                          │
│  └── Output: Approved North Star & Product Intent                        │
│                                                                          │
│  WEEK 3-4: ARCHITECTURE                                                  │
│  ├── CP: System Architecture, Data Model drafts                          │
│  ├── Leo: Review, ask questions, iterate                                 │
│  ├── CP: Engineering Playbook, Execution Plan                            │
│  └── Output: Full constitutional document set                            │
│                                                                          │
│  WEEK 4-5: IMPLEMENTATION PREP                                           │
│  ├── CP: SQL Migrations, RLS Policies, API Contract                      │
│  ├── CP: CC execution prompt, Cursor rules                               │
│  ├── Leo: Download and place files in repo                               │
│  └── Output: Repo ready for CC                                           │
│                                                                          │
│  WEEK 5+: IMPLEMENTATION                                                 │
│  ├── CC + Cursor: Execute PRs per build-plan.md                          │
│  ├── Leo: Review and merge PRs                                           │
│  ├── CP + Jordan: Idle (available for escalations)                       │
│  └── Output: Working MVP                                                 │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### 5.2 Phase Zero Checklist

Before implementation begins, ALL of the following must be true:

**North Star Complete:**
- [ ] Product definition clear (what it is and is NOT)
- [ ] Users defined (primary and secondary)
- [ ] Value proposition articulated
- [ ] Scope boundaries explicit
- [ ] Core principles documented
- [ ] Success criteria defined

**Architecture Complete:**
- [ ] System diagram created
- [ ] Service boundaries defined
- [ ] Auth model specified
- [ ] RLS strategy determined
- [ ] External integrations documented
- [ ] Error handling philosophy stated

**Data Model Complete:**
- [ ] All entities defined
- [ ] All relationships mapped
- [ ] All constraints specified
- [ ] Migration order documented
- [ ] Seed data prepared

**Policies Complete:**
- [ ] RLS policies for all tables
- [ ] Storage policies defined
- [ ] Helper functions specified
- [ ] Test plan documented

**API Contract Complete:**
- [ ] All endpoints defined
- [ ] Request/response schemas documented
- [ ] Error envelope standardized
- [ ] Security footguns documented

**Engineering Standards Complete:**
- [ ] Code standards defined
- [ ] Testing requirements specified
- [ ] CI/CD pipeline documented
- [ ] Git workflow established

**Execution Plan Complete:**
- [ ] MVP scope locked
- [ ] Build phases sequenced
- [ ] Decision gates defined
- [ ] PR order determined

**Repository Ready:**
- [ ] Folder structure created
- [ ] Constitutional docs placed
- [ ] CC execution rules written
- [ ] Cursor rules configured
- [ ] Build-plan.md initialized

---

## Part 6: The Implementation Rhythm

### 6.1 The CC-Cursor Loop

Once Phase Zero is complete, implementation follows a predictable rhythm:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    THE CC-CURSOR IMPLEMENTATION LOOP                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  1. CC READS BUILD-PLAN.MD                                              │
│     └── Identifies next PR to implement                                 │
│                                                                         │
│  2. CC CREATES TASK BRIEF                                               │
│     └── Writes detailed prompt in ai_prompts/active/                    │
│     └── Includes: objective, pre-flight checks, implementation steps    │
│                                                                         │
│  3. CURSOR IMPLEMENTS                                                   │
│     └── Reads task brief                                                │
│     └── Implements code per spec                                        │
│     └── Creates handoff note when done                                  │
│                                                                         │
│  4. CC REVIEWS                                                          │
│     └── Runs tests                                                      │
│     └── Verifies against acceptance criteria                            │
│     └── Fixes issues or sends back to Cursor                            │
│                                                                         │
│  5. CC CREATES PR                                                       │
│     └── Writes PR description                                           │
│     └── Commits code                                                    │
│     └── Archives prompt to ai_prompts/completed/                        │
│                                                                         │
│  6. LEO REVIEWS AND MERGES                                              │
│     └── Reviews PR                                                      │
│     └── Merges to main                                                  │
│     └── Loop continues to next PR                                       │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

### 6.2 PR Sequence Example

From Vantage DD, the PR sequence demonstrates the methodology:

| PR | Name | Dependencies | Purpose |
|----|------|--------------|---------|
| 0A | Extensions & ENUMs | None | Database foundation |
| 0B | Core tables (firms, users) | 0A | Identity tables |
| 0C | Application tables | 0B | Business entities |
| 0D | Scoring tables | 0C | Domain-specific |
| 0E | Audit & functions | 0D | Cross-cutting concerns |
| 0F | RLS policies | 0E | Security layer |
| 1 | Auth infrastructure | 0F | Authentication |
| 2 | Founder registration | 1 | First user flow |
| 3 | Company CRUD | 2 | Entity management |
| ... | ... | ... | ... |

**Key Principle:** Each PR builds on the previous. No PR has unmet dependencies. No PR exceeds ~300 lines of meaningful change.

### 6.3 Housekeeping Bundling

**Rule:** Bundle housekeeping into the first commit of each new PR.

This eliminates separate housekeeping PRs while maintaining quality gates:

```
PR-X Branch:
├── Commit 1: Housekeeping
│   ├── Archive previous prompt
│   ├── Update build-plan.md status
│   └── Create new task brief
│
├── Commit 2-N: Implementation
│   └── Feature code per task brief
│
└── Final: PR ready for review
```

---

## Part 7: Escalation Protocols

### 7.1 When to Escalate

**CC escalates to Leo when:**
- Spec ambiguity blocks implementation
- Test reveals architectural flaw
- External service behaves unexpectedly
- Security concern discovered
- Scope question arises

**Cursor escalates to CC when:**
- Task brief is unclear
- Implementation reveals edge case not covered
- Tests fail unexpectedly
- Dependencies are missing

**CP is engaged by Leo when:**
- Constitutional document needs update
- New spec required
- ADR needed for decision
- Prompt needed for CC

**Jordan is engaged by Leo when:**
- Business strategy question arises
- Feature prioritization needed
- User experience decision required
- Competitive landscape shifted

### 7.2 Escalation Format

```markdown
## Escalation: [Brief Title]

**From:** [Agent]
**To:** [Agent]
**Date:** [YYYY-MM-DD]
**Blocking:** [PR/Task Name]

### Issue
[Clear description of the problem]

### Context
[Relevant background]

### Options Considered
1. [Option A] — [Pros/Cons]
2. [Option B] — [Pros/Cons]

### Recommendation
[Agent's suggested path, if any]

### Decision Needed
[Specific question requiring answer]
```

### 7.3 Scope Creep Triggers

These phrases should trigger pause and escalation:

- "While we're at it, let's also..."
- "It would be easy to add..."
- "Users might also want..."
- "Future-proofing for..."
- "Just a small enhancement..."

**Correct Response:**
> "That feature isn't in the current phase scope. I can add it to the backlog for prioritization, but I won't build it without explicit approval."

---

## Part 8: Agent Configuration Files

### 8.1 CP Custom Instructions (Claude Project)

```json
{
  "project_name": "[PROJECT_NAME]",
  "assistant_name": "CP",
  "assistant_role": "Constitution, Specification & Prompt Author",
  "version": "1.0",
  "identity": {
    "who_you_are": "CP is the dedicated Claude Project instance responsible for producing constitutional documents, specifications, and inter-agent prompts.",
    "primary_function": "Translate product intent into authoritative, implementation-ready artifacts that CC and Cursor can execute without reinterpretation.",
    "authority_boundary": "CP authors specifications, prompts, and ADRs. CP does not manage execution, create PRs, or implement code."
  },
  "key_people_and_agents": {
    "leo": {
      "role": "Founder, Product Owner, Human-in-the-Loop",
      "authority": "Final decision-maker. Greenlights work, reviews PRs, merges code."
    },
    "jordan": {
      "role": "AI Co-Founder, Strategy & Ideation",
      "authority": "Business strategy, feature ideation. Does not manage implementation."
    },
    "cc": {
      "role": "Quality Gate & PR Author",
      "authority": "Reviews code, runs tests, creates PRs. Manages build-plan.md."
    },
    "cursor": {
      "role": "Implementation Engine",
      "authority": "Implements task briefs. Does not create PRs or make architectural decisions."
    }
  },
  "operating_mode": {
    "default_state": "Idle unless engaged by Leo",
    "when_engaged": "Produce bounded artifacts per request",
    "interaction_style": "Document-focused, options-based, waits for greenlight"
  },
  "cp_responsibilities": [
    "Author constitutional documents in docs/constitution/",
    "Write CC prompts for implementation tasks",
    "Create ADRs for spec-level decisions",
    "Ensure specs are internally consistent and executable"
  ],
  "cp_boundaries": [
    "Do not act as PM or orchestrator",
    "Do not manage sprints, PRs, or task sequencing",
    "Do not implement code or create PRs",
    "Do not extend documents beyond requested scope"
  ]
}
```

### 8.2 CC Execution Rules

```markdown
# Claude Code Execution Rules

## Identity
You are CC, the Quality Gate & PR Author for [PROJECT_NAME].

## Primary Responsibilities
1. Execute task briefs from docs/build-plan.md
2. Review and test code before committing
3. Create PRs with clear descriptions
4. Manage ai_prompts/ lifecycle
5. Escalate spec ambiguity to Leo

## Constraints
1. Never modify docs/constitution/ — escalate to Leo for changes
2. Never make architectural decisions unilaterally — check specs first
3. Never skip tests — all PRs must pass CI
4. Never merge without Leo's approval

## Workflow Rhythm
1. Read build-plan.md → identify next task
2. Create task brief → ai_prompts/active/
3. Implement or delegate to Cursor
4. Review and test
5. Create PR → archive prompt
6. Wait for Leo's merge

## Escalation Triggers
- Spec doesn't cover this case
- Test reveals architectural flaw
- External service behaves unexpectedly
- Security concern discovered
```

### 8.3 Cursor Rules (.cursor/rules/project-rules.mdc)

```markdown
# Cursor Implementation Rules

## Role
You are the Implementation Engine. You execute task briefs from CC.

## Constraints
- DO NOT create PRs — hand off to CC
- DO NOT make architectural decisions — follow the spec
- DO NOT modify constitutional documents
- DO NOT skip tests specified in task brief

## Workflow
1. Read task brief in ai_prompts/active/
2. Implement per specifications
3. Run tests locally
4. Create handoff note
5. Signal completion to CC

## On Ambiguity
If task brief is unclear, STOP and create an escalation note.
Do not guess. Do not improvise. Ask CC.

## Code Standards
- Follow engineering-playbook.md
- TypeScript strict mode
- Zod validation on all inputs
- No `any` types without justification
```

---

## Part 9: Starting a New Project

### 9.1 Day 1 Checklist

When starting a new Phase Zero project:

**Setup (Leo):**
- [ ] Create new Claude Project with CP custom instructions
- [ ] Create ChatGPT thread for Jordan
- [ ] Initialize GitHub repository
- [ ] Create folder structure per Section 4.1

**Ideation (Leo + Jordan):**
- [ ] Define the product concept
- [ ] Identify target users
- [ ] Articulate value proposition
- [ ] List MVP features
- [ ] Document non-goals

**Engage CP (Leo):**
- [ ] Share ideation output with CP
- [ ] Request North Star draft
- [ ] Review and iterate
- [ ] Greenlight North Star

### 9.2 Week 1-2: Constitutional Documents

**Leo + CP:**
- [ ] Complete North Star
- [ ] Complete System Architecture
- [ ] Complete Data Model
- [ ] Complete Engineering Playbook
- [ ] Complete Execution Plan

**Leo + CP (detailed specs):**
- [ ] Generate SQL Migrations
- [ ] Generate RLS Policy Spec
- [ ] Generate API Route Contract

### 9.3 Week 3: Repository Setup

**CP → Leo:**
- [ ] CC execution rules document
- [ ] Cursor rules file
- [ ] Build-plan.md template
- [ ] First PR task brief

**Leo:**
- [ ] Download all constitutional documents
- [ ] Place in docs/constitution/
- [ ] Configure CC with execution rules
- [ ] Configure Cursor with rules file
- [ ] Verify folder structure

### 9.4 Week 4+: Implementation

**CC + Cursor + Leo:**
- [ ] Execute first PR
- [ ] Establish rhythm
- [ ] Process backlog per build-plan.md
- [ ] Jordan and CP remain idle unless escalated

---

## Part 10: Success Metrics

### 10.1 Phase Zero Health Indicators

**Healthy Phase Zero:**
- Implementation is boring (specs answer all questions)
- PRs rarely need rework
- CC asks few clarifying questions
- Cursor completes tasks on first attempt
- Merge rate is consistent

**Unhealthy Phase Zero:**
- Frequent escalations during implementation
- PRs require architectural changes
- Specs don't match what's being built
- Scope creep is occurring
- Agents are confused about their roles

### 10.2 Velocity Benchmarks

Based on Vantage DD experience:

| Metric | Target |
|--------|--------|
| Constitutional docs | 2-3 weeks |
| PRs per day (implementation) | 1-2 |
| Test coverage | >80% for core logic |
| Merge turnaround | <24 hours |
| Escalation rate | <1 per 5 PRs |

### 10.3 Quality Benchmarks

| Standard | Expectation |
|----------|-------------|
| TypeScript errors | Zero |
| ESLint errors | Zero |
| Test pass rate | 100% |
| Documentation | All endpoints documented |
| Audit trail | All state changes logged |

---

## Appendix A: Glossary

| Term | Definition |
|------|------------|
| **Phase Zero** | The methodology itself — front-loading specification before implementation |
| **Constitutional Document** | Authoritative spec that governs implementation (North Star, Architecture, etc.) |
| **CP** | Claude Project — the specification author agent |
| **CC** | Claude Code — the quality gate and PR author agent |
| **Task Brief** | Detailed implementation prompt from CC to Cursor |
| **Greenlight** | Leo's explicit approval to proceed |
| **ADR** | Architecture Decision Record |
| **Build-Plan** | Living document tracking PR sequence and status |
| **Escalation** | Formal request for decision or clarification |

---

## Appendix B: Template Files

### North Star Template

```markdown
# [Product Name] — North Star & Product Intent

**Version:** 1.0
**Date:** [YYYY-MM-DD]
**Status:** Draft / Approved

---

## 1. What This Product Is

[Clear definition]

**What it is:**
- [Capability 1]
- [Capability 2]

**What it is NOT:**
- [Non-goal 1]
- [Non-goal 2]

## 2. Who It Is For

### Primary Users
[Define each user type, their experience, and success criteria]

### Secondary Stakeholders
[Define stakeholders who aren't direct users]

## 3. Why We Are Building It

### Economic Reasons
[Cost savings, revenue opportunity, etc.]

### Operational Reasons
[Efficiency, scalability, etc.]

### Human Reasons
[User experience, quality of life, etc.]

## 4. What It Will and Will Not Do

### In Scope (MVP)
| Capability | Description |
|------------|-------------|
| [Cap 1] | [Desc] |

### Out of Scope (MVP)
| Excluded | Rationale |
|----------|-----------|
| [Item 1] | [Why] |

### Guardrails Against Scope Creep
1. [Guardrail 1]
2. [Guardrail 2]

## 5. Core Principles

### [Principle 1 Name]
[Description and implications]

### [Principle 2 Name]
[Description and implications]

## 6. Decision Philosophy

[How the system makes decisions, if applicable]

## 7. Outputs This System Must Reliably Produce

### For [User Type 1]
| Output | Description |
|--------|-------------|
| [Out 1] | [Desc] |

## 8. How This Artifact Should Be Used

[Governance and reference instructions]

---

## Appendix A: [Domain-Specific Appendix]

[Additional detail as needed]
```

### Build-Plan Template

```markdown
# Build Plan — [Project Name]

**Last Updated:** [YYYY-MM-DD]
**Current PR:** [PR-XX]

---

## PR Sequence

| PR | Name | Status | Dependencies |
|----|------|--------|--------------|
| 0A | Extensions & ENUMs | ✅ Complete | None |
| 0B | Core Tables | ✅ Complete | 0A |
| 0C | [Next] | 🔄 In Progress | 0B |
| 1 | [Future] | ⏳ Pending | 0C |

## Current Focus

**PR-0C: [Name]**
- Objective: [What this PR accomplishes]
- Task Brief: ai_prompts/active/pr-0c-task-brief.md
- Acceptance Criteria:
  - [ ] [Criterion 1]
  - [ ] [Criterion 2]

## Backlog

[Items not yet scheduled]

## Completed

[Summary of completed work]
```

---

## Appendix C: Change Log

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-03 | Initial release based on Vantage DD experience |

---

*End of Phase Zero Methodology*
