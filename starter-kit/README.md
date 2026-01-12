# FORGE Starter Kit

**Canonical assets for instant FORGE alignment**

---

## Starter Kit vs Project Template

| This is... | Use when... |
|------------|-------------|
| **Starter Kit** (you're here) | Reference assets — copy individual files to customize existing repos |
| **[forge-project-template](https://github.com/Knight-Ventures-Inc/forge-project-template)** | Clone the whole repo to start a new FORGE project from scratch |

Most users should **clone forge-project-template**. This starter-kit is the canonical source these templates are derived from.

---

## What This Is

This folder contains ready-to-use configuration files that make any new repository instantly FORGE-aligned. These are the canonical starting points - copy them, customize the marked sections, and you're operational.

---

## Contents

| Path | Purpose |
|------|---------|
| `CLAUDE.md` | Repo-level operating contract for Claude Code |
| `.cursor/rules/forge-sd.mdc` | Cursor rules for Software Dev profile |
| `.cursor/rules/forge-cp.mdc` | Cursor rules for Spec Author behavior |
| `.cursor/rules/forge-cc.mdc` | Cursor rules for Quality Gate behavior |
| `docs/parking-lot/` | Template for issues/ideas discovered during development |
| `chatgpt/PROJECT_SETUP.md` | How to create Jordan (Strategist) project |
| `chatgpt/custom-instructions-jordan.md` | Jordan's custom instructions |
| `claude_ai/PROJECT_SETUP.md` | How to create CP and CC projects |
| `claude_ai/custom-instructions-cp.md` | CP's custom instructions |
| `claude_ai/custom-instructions-cc.md` | CC's custom instructions |

---

## How to Apply

### For a New Repo

1. Copy `CLAUDE.md` to your project root
2. Copy `.cursor/rules/` to your project's `.cursor/` directory
3. Copy `docs/parking-lot/` to your project's `docs/` directory
4. Edit `CLAUDE.md` to fill in project-specific sections (marked with `[CUSTOMIZE]`)
5. Create ChatGPT and Claude.ai projects per the setup docs

### For Agent Setup

1. **Jordan (ChatGPT):** Follow `chatgpt/PROJECT_SETUP.md`
2. **CP (Claude.ai):** Follow `claude_ai/PROJECT_SETUP.md`
3. **CC (Claude Code):** Uses `.cursor/rules/` + `CLAUDE.md` automatically

---

## What to Customize vs Keep Standard

### MUST Customize Per Project

| Item | What to Change |
|------|----------------|
| `CLAUDE.md` | Project name, description, stack, current phase, current PR |
| ChatGPT Project | Project name, attach project-specific docs |
| Claude.ai Projects | Project name, attach project-specific docs |

### Keep Standard (Don't Edit)

| Item | Why |
|------|-----|
| `.cursor/rules/*.mdc` | Lane boundaries are canonical |
| Custom instructions core | Role definitions are canonical |
| Verification sequence | Sacred Four is invariant |

---

## Authority

These assets implement FORGE methodology as defined in:
- `core/forge-core.md` - Canonical methodology
- `core/forge-operations.md` - Execution procedures
- `profiles/forge-sd-profile.md` - Software development profile

See `meta/MANIFEST.md` for complete document index.

---

## Versioning

When FORGE methodology updates, these starter-kit assets update too. Check `FORGE-Method` for latest versions before scaffolding new projects.

---

**(c) 2026 Knight Ventures, Inc. All rights reserved.**

**FORGE(TM)** is a trademark of Knight Ventures, Inc.
