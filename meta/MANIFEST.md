# FORGE Method - Document Manifest

**Version:** 1.0
**Date:** 2026-01-07
**Purpose:** Canonical index of all FORGE methodology documents

---

## Overview

This manifest catalogs all FORGE methodology documents following the consolidation of 2026-01-07. The consolidation reduced 30+ overlapping files to a clean canonical set.

---

## Directory Structure

```
FORGE-Method/
+-- core/             # Canonical methodology documents
+-- profiles/         # Execution profiles (domain-specific)
+-- agents/           # Agent-specific operating guides
+-- templates/        # First-class artifact templates
+-- archive/          # Historical and development artifacts
+-- meta/             # Repository control documents
+-- incoming/         # Original downloaded artifacts (read-only snapshot)
```

---

## Core Documents

| File | Purpose | Version | Classification |
|------|---------|---------|----------------|
| `core/forge-core.md` | The FORGE Method - canonical methodology | 1.1 | **[UNIVERSAL]** |
| `core/forge-operations.md` | Operational procedures and The FORGE Cycle | 1.1.1 | **[UNIVERSAL]** |
| `core/forge-orientation.md` | New agent onboarding guide | 1.0 | **[UNIVERSAL]** |
| `core/forge-governance.md` | Versioning, contribution, licensing | 1.0 | **[UNIVERSAL]** |

---

## Profiles

| File | Purpose | Version | Classification |
|------|---------|---------|----------------|
| `profiles/forge-sd-profile.md` | Software Development execution profile | 1.1 | **[FORGE-SD]** |

*Future profiles: FORGE-BOOK, FORGE-SVC, FORGE-RE*

---

## Agents

| File | Purpose | Version | Classification |
|------|---------|---------|----------------|
| `agents/forge-agent-roles-handoffs.md` | Agent role definitions and handoff protocols | 1.0 | **[UNIVERSAL]** |
| `agents/forge-jordan-operating-guide.md` | Jordan (Strategist) operating instructions | 1.0 | **[SITUATIONAL]** |
| `agents/forge-core-essentials.md` | Jordan's condensed FORGE reference | 1.0 | **[SITUATIONAL]** |

---

## Templates

| File | Purpose | Version | Classification |
|------|---------|---------|----------------|
| `templates/forge-template-frame.md` | Frame Artifact template | 1.2 | **[UNIVERSAL]** |
| `templates/forge-template-kickoff-brief.md` | Kickoff Brief template | 1.1 | **[UNIVERSAL]** |
| `templates/forge-template-project-spec.md` | Project instantiation specification | 1.1 | **[UNIVERSAL]** |
| `templates/forge-template-project-identity.md` | CLAUDE.md / project identity template | 1.2 | **[UNIVERSAL]** |
| `templates/forge-template-repository-scaffold.md` | Repository structure specification | 1.0 | **[FORGE-SD]** |
| `templates/forge-template-cp-handoff-packet.md` | CP handoff packet template | 1.0 | **[SITUATIONAL]** |
| `templates/forge-templates.md` | Collection of operational templates | 1.1 | **[UNIVERSAL]** |

---

## Archive

### Historical (Superseded Methodology)

| File | Original Purpose | Status |
|------|-----------------|--------|
| `archive/historical/phase-zero-methodology.md` | Pre-FORGE methodology (v0) | **SUPERSEDED** by forge-core.md |
| `archive/historical/intent-to-execution-method.md` | Early FORGE iteration | **SUPERSEDED** by forge-core.md |
| `archive/historical/the-forge-method.md` | Intermediate FORGE version | **SUPERSEDED** by forge-core.md |
| `archive/historical/genesis-quick-start.md` | Early quick-start guide | **SUPERSEDED** by forge-orientation.md |

### Development Artifacts

| File | Purpose | Status |
|------|---------|--------|
| `archive/development/cc-forge-operations-validation-brief.md` | CC validation task | **DEV ARTIFACT** |
| `archive/development/cc-forge-review-task-brief.md` | CC review task | **DEV ARTIFACT** |
| `archive/development/cc-review-forge-instantiation-artifacts.md` | CC instantiation review | **DEV ARTIFACT** |

### Instances (Filled Examples)

| File | Purpose | Status |
|------|---------|--------|
| `archive/instances/forge-kickoff-brief.md` | Filled Kickoff Brief example | **INSTANCE** |

### Config (Agent Configuration)

| File | Purpose | Status |
|------|---------|--------|
| `archive/config/jordan-custom-instructions.json` | Jordan v1 config | **HISTORICAL** |
| `archive/config/jordan-custom-instructions-v3.json` | Jordan v3 config | **CURRENT** |

---

## Classification Legend

| Tag | Meaning |
|-----|---------|
| **[UNIVERSAL]** | Applies to all FORGE projects regardless of domain |
| **[FORGE-SD]** | Specific to Software Development profile |
| **[SITUATIONAL]** | Use when applicable; not mandatory |
| **SUPERSEDED** | Replaced by newer canonical document |
| **DEV ARTIFACT** | Development/testing artifact, not canonical |
| **INSTANCE** | Filled example, not a template |
| **HISTORICAL** | Preserved for reference only |
| **CURRENT** | Active configuration |

---

## Document Count

| Category | Count |
|----------|-------|
| Core | 4 |
| Profiles | 1 |
| Agents | 3 |
| Templates | 7 |
| Archive | 10 |
| Meta | 3 |
| **Total Canonical** | **15** |
| **Total (including archive)** | **28** |

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-07 | Initial manifest after consolidation |

---

**(c) 2026 Knight Ventures, Inc. All rights reserved.**

**FORGE(TM)** is a trademark of Knight Ventures, Inc.
