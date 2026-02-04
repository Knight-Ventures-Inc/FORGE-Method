# Understanding FORGE Role Evolution

**Date:** 2026-02-03
**Status:** [CANON]

---

## Overview

This document clarifies the evolution from tool-based to role-based terminology in FORGE.

---

## Context

In the original Vantage FORGE workflow:
- **CC (Claude Code)** functioned as the coordination layer
- **Cursor** functioned as the execution engine

This created confusion because tool names were used as role names.

---

## Clarification

**FORGE is role-based, not tool-based.**

### Roles (Canonical)

| Letter | Role | Agent | Function |
|--------|------|-------|----------|
| **F** | Frame | Product Strategist | Define what to build |
| **O** | Orchestrate | Project Architect | Design how to build it |
| **R** | Refine | Human review | Clarify and approve specs |
| **G** | Govern | Ops Agent | Coordinate state, handoffs, validation, gating |
| **E** | Execute | Execution agents/humans | Implement code, infrastructure, tests |

### Tools (Implementation Detail)

| Tool | What It Is | What It Is NOT |
|------|------------|----------------|
| **CC (Claude Code)** | Infrastructure/runtime used by agents | A FORGE role |
| **Cursor** | Historical execution engine | A FORGE role |
| **IDE** | Development environment | A FORGE role |

---

## What Changed

| Before | After |
|--------|-------|
| "CC coordinates execution" | "Ops Agent (G) coordinates E" |
| "Cursor executes code" | "E agents/humans execute code" |
| "CC talks to human" | "G talks to human, E talks to G" |
| Tool-centric naming | Role-centric naming |

---

## Key Insight

**CC is NOT a FORGE role.** CC is infrastructure.

E agents may use CC internally as their runtime, but this is implementation detail. G coordinates **E** (the role), not CC (the tool).

---

## Ops Agent (G)

The Ops Agent is the explicit owner of the Govern phase:

| Attribute | Value |
|-----------|-------|
| **Name** | Ops Agent |
| **Lane** | G (Govern) |
| **Function** | State ownership, coordination, validation, gating |
| **Coordinates** | E (not CC) |

---

## Execution (E)

E represents any execution capability:

| What E Can Be | Example |
|---------------|---------|
| Human developer | Using IDE manually |
| E agent | Autonomous coding agent |
| Hybrid | Agent with human oversight |

E may use CC as infrastructure, but E is the FORGE role, not CC.

---

## Letter Shorthand

Using **F/O/R/G/E** in docs and UX is:
- **Intentional** — Reinforces role-based model
- **Encouraged** — Clear, concise reference
- **Consistent** — Same across all FORGE artifacts

---

## Why This Matters

1. **Clarity** — Roles have defined responsibilities
2. **Modularity** — Tools can change without changing roles
3. **Coordination** — G → E is clear; "CC → Cursor" was not
4. **Future-proof** — New tools fit into existing roles

---

## Practical Impact

### For New Projects

- Spawn with `inbox/30_ops/` for G-phase artifacts
- Ops Agent coordinates via Build Plan
- E (whatever form) receives task briefs from G

### For Existing Projects

- Migration optional but recommended
- See `docs/guides/inbox-migration-guide.md`
- Legacy terminology still works but is deprecated

### For Documentation

- Use role names (F/O/R/G/E) not tool names
- "G coordinates E" not "CC coordinates Cursor"
- Letter shorthand encouraged

---

## Summary

| Concept | Status |
|---------|--------|
| F/O/R/G/E roles | **Canonical** |
| Ops Agent owns G | **Canonical** |
| CC as infrastructure | **Canonical** |
| E as execution role | **Canonical** |
| Tool-based naming | **Deprecated** |

---

*This document clarifies the evolution from tool-based to role-based FORGE. No functionality changed; naming and roles are now explicit.*
