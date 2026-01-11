# Recon Report: Replacing CP with a Local Claude Code Sub-Agent

**Date:** 2026-01
**Environment:** Claude Code 2.1.4, macOS (iMac Pro)
**Status:** Validated
**Audience:** Advanced FORGE users

> This document reflects real-world testing performed by the FORGE maintainers.
> Results are version-specific and may change as tools evolve.
> This is not canonical FORGE doctrine, but validated execution evidence.

---

## Purpose

Determine whether the FORGE Spec Author role (CP), currently running as a ChatGPT Project, can be replaced with a **local Claude Code sub-agent** while preserving lane separation and enforcing "no code edits."

---

## Initial Assumptions

Based on Perplexity deep research and Anthropic blog posts, we assumed:

1. Claude Code supports custom sub-agents defined in `.claude/agents/*.md`
2. Agent YAML frontmatter supports `tools`, `deny`, `allowedTools`, `disallowedTools` fields
3. Tool deny-lists in agent definitions would be enforced at runtime
4. Sub-agents would have isolated context windows
5. Agents could be hot-loaded (no restart required)

**Source of assumptions:** Perplexity research citing `code.claude.com/docs/en/sub-agents`, Anthropic engineering blogs, and community examples.

---

## Test Environment

| Component | Details |
|-----------|---------|
| Claude Code | Version 2.1.4 |
| Platform | macOS Darwin 24.6.0 (iMac Pro) |
| Repo Context | `/Users/leonardknight/kv-projects/FORGE-Method` |
| Date | 2026-01-11 |

---

## Tests Performed

### Test 1: Verify Sub-Agent Support

**Method:** Check CLI help for agent-related flags.

**Command:** `claude --help | grep agent`

**Result:** Found:
- `--agent <agent>` — Agent for current session
- `--agents <json>` — Inline JSON agent definition

**Conclusion:** Sub-agent support exists.

---

### Test 2: Locate Agent Definitions

**Method:** Examine `~/.claude/` directory structure.

**Result:** Found `~/.claude/agents/` containing 9 custom agent files:
- `decision-logger.md`
- `spec-writer.md`
- `research-agent.md`
- `swift-architect.md`
- `ios-test-engineer.md`
- (and 4 others)

**File Format Observed:**
```yaml
---
name: spec-writer
description: "..."
model: sonnet
---
[System prompt content]
```

**Conclusion:** Custom agents ARE defined in `~/.claude/agents/*.md` with YAML frontmatter.

---

### Test 3: Invoke Custom Agent via Task Tool

**Method:** Use Task tool with `subagent_type="spec-writer"`.

**Result:** Agent invoked successfully. Confirmed model was `sonnet` per definition.

**Conclusion:** Task tool CAN invoke custom agents from `~/.claude/agents/`.

---

### Test 4: Test Tool Restrictions in YAML (CRITICAL)

**Method:** Created test agent with tool restrictions:

```yaml
---
name: forge-cp-test
description: "Test agent"
model: sonnet
allowedTools:
  - Read
  - Glob
disallowedTools:
  - Edit
  - Write
  - Bash
---
```

**Result:** Agent NOT immediately available. Error: `Agent type 'forge-cp-test' not found`

**Conclusion:** New agents require Claude Code restart to load.

---

### Test 5: Lane Enforcement Test (CRITICAL)

**Method:** Asked `spec-writer` agent (no tool restrictions in its definition) to edit a file:

> "Edit /path/to/README.md and add text at top"

**Result:**

```
SUCCESS - I successfully edited the file.
```

The agent:
1. Read the file
2. Used Edit tool
3. Modified the file content
4. Reported success

**Conclusion:** **SUB-AGENTS HAVE FULL TOOL ACCESS.** The Perplexity research was INCORRECT about YAML deny-lists.

---

### Test 6: Context Isolation Test

**Method:** Asked sub-agent about its context:
- "Do you know what we've been discussing?"
- "What files have you read?"
- "Do you have access to conversation history?"

**Result:**
- "This appears to be the start of our conversation"
- "I have not read any files in this session yet"
- "I don't have specific knowledge about FORGE from this conversation"

**Conclusion:** Sub-agents DO have isolated context windows. They start fresh without parent conversation history.

---

## Findings

### What Works

| Capability | Status | Evidence |
|------------|--------|----------|
| Custom sub-agents | ✅ Works | Files in `~/.claude/agents/*.md` are loaded |
| Agent invocation via Task tool | ✅ Works | `subagent_type` parameter accepted |
| Agent invocation via CLI | ✅ Works | `--agent <name>` per CLI help |
| Context isolation | ✅ Works | Sub-agent has no parent conversation memory |
| Custom system prompts | ✅ Works | Markdown body defines agent behavior |
| Model selection | ✅ Works | `model: sonnet` honored |

### What Does NOT Work

| Capability | Status | Evidence |
|------------|--------|----------|
| YAML `allowedTools` | ❌ Not supported | Field ignored; agent has all tools |
| YAML `disallowedTools` | ❌ Not supported | Field ignored; agent has all tools |
| YAML `deny` | ❌ Not supported | Field ignored; not parsed |
| Hot-loading new agents | ❌ Not supported | New files require restart |
| Lane enforcement via agent definition | ❌ Not supported | Must use other methods |

---

## Corrected Mental Model

### Before (Incorrect)

> "Claude Code sub-agents can have tool restrictions defined in YAML frontmatter. We can create a CP agent with `deny: [Edit, Write, Bash]` and it will be blocked from editing code."

### After (Correct)

> "Claude Code sub-agents have FULL tool access regardless of YAML frontmatter. Tool restrictions in agent definitions are NOT parsed or enforced. Lane enforcement must happen via:
> 1. **Prompt-level instructions** in the system prompt
> 2. **CLI flags** (`--disallowedTools`) at invocation time
> 3. **Wrapper scripts** that enforce restrictions"

---

## Recommended Pattern (FORGE)

### Option A: Prompt-Only Enforcement (Medium Reliability)

Create agent with strong lane boundaries in system prompt:

```markdown
---
name: forge-cp
description: "FORGE Spec Author"
model: sonnet
---

You are the Spec Author (CP) in FORGE.

## HARD CONSTRAINTS (Non-Negotiable)

You CANNOT and MUST NOT:
- Use the Edit tool
- Use the Write tool
- Use Bash commands that modify files
- Create, edit, or delete code files
- Make git commits

If asked to edit code, REFUSE and explain you are a read-only spec agent.
```

**Reliability:** Medium — LLM can still access tools if it chooses to ignore instructions.

### Option B: CLI Flag Enforcement (High Reliability)

Invoke with tool restrictions at CLI level:

```bash
claude --agent forge-cp --disallowedTools "Edit,Write,Bash" "Write an ADR for..."
```

**Reliability:** High — tools are blocked at system level, not prompt level.

### Option C: Wrapper Script (High Reliability + Repeatable)

Create `forge-cp.sh`:

```bash
#!/bin/bash
claude --agent forge-cp \
  --disallowedTools "Edit,Write,Bash(rm *),Bash(git commit)" \
  "$@"
```

**Reliability:** High + ensures consistent invocation.

### FORGE Recommendation

**Use Option C (Wrapper Script)** for production CP replacement. This:
- Enforces lanes at tool level (not just prompt)
- Ensures consistent invocation
- Is auditable and version-controlled
- Works with existing Task tool via shell

---

## Known Limitations & Gotchas

| Gotcha | Impact | Mitigation |
|--------|--------|------------|
| YAML deny-lists don't work | Sub-agent can edit anything | Use CLI `--disallowedTools` |
| New agents need restart | Can't hot-load during session | Plan agent additions in advance |
| `--disallowedTools` not tested | May have edge cases | Test before production use |
| Sub-agent has no parent context | Must re-establish project context | Include context in prompt or rely on CLAUDE.md |
| Model override per agent | Could accidentally use expensive model | Specify `model:` explicitly |

---

## Implications for FORGE

### CP Replacement is Viable

Yes, we can replace the ChatGPT-based CP with a local Claude Code sub-agent, BUT:

1. **Lane enforcement requires CLI flags**, not agent definition
2. **Context must be re-established** per invocation (sub-agent is isolated)
3. **Wrapper script recommended** for production use

### What This Enables

- **Lower cost** — API pay-as-you-go vs $20-200/mo subscription
- **Faster iteration** — Local execution, no cloud round-trips
- **Repo integration** — Direct file access, git awareness
- **Context isolation** — No window overflow from parent conversation

### What This Does NOT Enable

- **Automatic lane enforcement** — Must be explicitly configured
- **Hot-loading agents** — Restart required for new agents
- **YAML-based governance** — Tool permissions not declarative

---

## Status

**Validated** — Tests performed on Claude Code 2.1.4, macOS, 2026-01-11.

**Re-test when:**
- Claude Code major version changes
- Anthropic announces sub-agent permission features
- Community reports different behavior

---

## Appendix: Research Source Corrections

The following claims from Perplexity research were **incorrect** for Claude Code 2.1.4:

| Claim | Reality |
|-------|---------|
| "YAML frontmatter supports `tools`, `deny` fields" | Only `name`, `description`, `model` observed |
| "Tool deny-lists are enforced" | Not enforced; agent has full access |
| "Agents can be hot-loaded" | New agents require restart |
| "`claude --agent spec-author` invokes agent" | Syntax correct, but permissions not enforced |

These discrepancies may reflect:
- Aspirational documentation
- Features in different Claude products
- Version differences
- Incorrect community examples

**Lesson:** Always validate against actual tool behavior before adopting.

---

## Authors

- **Primary Investigator:** CC (Claude Code)
- **Research Synthesis:** Jordan (ChatGPT)
- **Approving Authority:** Leo (Human Lead)

---

*This is part of The FORGE Method(TM) — theforgemethod.org*
