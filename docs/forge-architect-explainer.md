# The Forge-Architect Agent: Project Spawner

**For:** Jordan (Human Lead / Product Owner)
**What:** A specialized AI agent that scaffolds new FORGE projects
**Why:** Eliminates manual setup, ensures consistency, enables immediate handoff to project governance

---

## What It Does (One Sentence)

The forge-architect takes a project brief from you and creates a complete, ready-to-govern FORGE repository with all the scaffolding, templates, and a project-specific architect agent—then hands off to that new agent for ongoing work.

---

## The Problem It Solves

Before forge-architect, starting a new project meant:
- Manually creating 15+ directories and files
- Copy-pasting templates and forgetting pieces
- Inconsistent project structures across repos
- No built-in governance from day one
- Time spent on setup instead of thinking

Now: You describe what you want to build, forge-architect creates everything, and you're immediately in Frame phase with a project-architect ready to work.

---

## How to Use It

### Step 1: Invoke the Agent

In Claude Code, use the Task tool:
```
Task tool with subagent_type="forge-architect"
```

Or simply tell Claude Code: "I want to start a new FORGE project" and it will invoke forge-architect.

### Step 2: Provide Your Project Brief

Give forge-architect:
- **Project name** — What's it called?
- **Domain** — FORGE-SD (software) or FORGE-BOOK (book/writing)
- **One-liner** — What does it do in one sentence?
- **Target users** — Who is this for?
- **Core features** — 3-5 key capabilities
- **Stack choices** (for software) — Framework, database, hosting, etc.
- **Constraints** — What's explicitly NOT in scope?

**Example brief:**
> "I want to build a VC deal screening tool called Vantage. It's for early-stage VCs to quickly assess inbound deals using AI. Core features: intake form, AI analysis, scoring dashboard. Stack: Next.js, Supabase, Vercel. Not building: CRM integration, portfolio management, or investor-facing features."

### Step 3: Review the Scaffold

Forge-architect will create your repo structure and confirm:
```
Project scaffolded successfully at ~/kv-projects/[project-name]/

Created:
- CLAUDE.md (project identity)
- docs/constitution/ (PRODUCT.md, TECH.md, GOVERNANCE.md templates)
- .claude/agents/project-architect.md (your project's governance agent)
- inbox/ (task brief system)
- .cursor/rules/ (implementation lane rules)
- First task brief for Frame phase

Next: Restart Claude Code, navigate to the project, invoke project-architect.
```

### Step 4: Hand Off to Project-Architect

1. Restart Claude Code (so it loads the new agent)
2. `cd ~/kv-projects/[project-name]`
3. Invoke: `Task tool with subagent_type="project-architect"`
4. The project-architect now owns ongoing governance for this project

---

## What Gets Created

```
[project]/
├── CLAUDE.md                          # Project identity, agent lanes, commands
├── .cursor/rules/
│   ├── forge-sd.mdc                   # Implementation lane rules
│   └── forge-cc.mdc                   # Quality gate rules
├── .claude/agents/
│   └── project-architect.md           # THIS PROJECT's governance agent
├── docs/
│   ├── constitution/
│   │   ├── PRODUCT.md                 # [CUSTOMIZE] Product intent
│   │   ├── TECH.md                    # [CUSTOMIZE] Technical architecture
│   │   └── GOVERNANCE.md              # [CUSTOMIZE] Security & policies
│   ├── parking-lot/
│   │   ├── known-issues.md
│   │   └── future-work.md
│   ├── build-plan.md                  # Sprint/PR tracking
│   └── adr/                           # Architecture Decision Records
├── inbox/
│   ├── active/                        # Current task brief lives here
│   ├── completed/                     # Archived briefs
│   └── templates/
│       └── task-brief.template.md
├── src/                               # Empty, ready for code
├── tests/                             # Empty, ready for tests
└── .github/
    └── PULL_REQUEST_TEMPLATE.md
```

---

## The Two Architect Agents

| Agent | Scope | Lives At | Role |
|-------|-------|----------|------|
| **forge-architect** | Global | `~/.claude/agents/forge-architect.md` | Creates new projects, one-time scaffolding |
| **project-architect** | Per-project | `[project]/.claude/agents/project-architect.md` | Governs that specific project ongoing |

**Think of it like:**
- forge-architect = General contractor who builds houses
- project-architect = Property manager who runs one specific building

---

## Why This Architecture?

### 1. Separation of Concerns
forge-architect knows how to scaffold ANY FORGE project. project-architect knows everything about ONE specific project. Neither steps on the other's toes.

### 2. Constitutional Documents Are Pre-Staged
The templates with `[CUSTOMIZE]` markers ensure you don't forget critical decisions. You can't skip governance—it's baked into the scaffold.

### 3. Immediate Handoff
No gap between "project created" and "project governed." The project-architect is ready to work the moment scaffolding completes.

### 4. Consistent Quality
Every project gets the same verified structure. No forgotten files, no inconsistent naming, no missing templates.

---

## Domains Supported

### FORGE-SD (Software Development)
Full structure with:
- `src/` and `tests/` directories
- Cursor rules for implementation lane
- CI/CD templates
- API and database documentation slots

### FORGE-BOOK (Book/Writing Projects)
Simplified structure:
- Chapter organization
- Research notes
- No code artifacts
- Writing-focused templates

---

## Example Workflow

```
┌─────────────────────────────────────────────────────────────┐
│  JORDAN: "I want to build a habit tracker app called Streaks" │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  FORGE-ARCHITECT:                                            │
│  - Asks clarifying questions (stack? users? constraints?)    │
│  - Creates ~/kv-projects/streaks/                            │
│  - Scaffolds all directories and templates                   │
│  - Creates project-architect agent for Streaks               │
│  - Creates first task brief: "Complete PRODUCT.md"           │
│  - Reports: "Project scaffolded. Restart and invoke          │
│              project-architect to begin Frame phase."        │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  PROJECT-ARCHITECT (for Streaks):                            │
│  - Owns PRODUCT.md, TECH.md, GOVERNANCE.md                   │
│  - Works with Jordan to complete constitutional docs         │
│  - Creates task briefs for CC to execute                     │
│  - Enforces lanes and scope throughout project               │
└─────────────────────────────────────────────────────────────┘
```

---

## Key Points to Remember

1. **One-time use per project** — forge-architect scaffolds, then you never call it again for that project

2. **Restart required** — Claude Code needs to restart to load the new project-architect agent

3. **Templates need customization** — Look for `[CUSTOMIZE]` markers in constitutional docs

4. **Frame phase is next** — After scaffolding, you're in Frame phase. Complete constitutional docs before Execute.

5. **Inbox-driven workflow** — Everything goes through `inbox/`. No verbal agreements.

---

## Quick Reference

**To scaffold a new project:**
```
"Start a new FORGE project" → Claude Code invokes forge-architect → Provide brief → Get scaffold
```

**To continue working on an existing project:**
```
cd ~/kv-projects/[project] → Invoke project-architect → Work within that project's governance
```

**Location of forge-architect:**
```
~/.claude/agents/forge-architect.md
```

**Location of project-architect (after scaffolding):**
```
~/kv-projects/[project]/.claude/agents/project-architect.md
```
