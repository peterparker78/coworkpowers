# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

CoworkPowers is a **Claude Code plugin** (not a traditional software project). It consists entirely of markdown files that define skills, agent prompts, and standards. There is no build system, no tests, and no compiled code.

The plugin orchestrates a 4-phase compound knowledge work loop for pharma/biotech and consulting:
1. **Research** → 2. **Work** → 3. **Review** → 4. **Compound**

## Architecture

**Plugin entry point**: `.claude-plugin/plugin.json` — registers the plugin as `coworkpowers`.

**Four skills** (each a `SKILL.md` in `skills/`):
- `workflow-research` — Orchestrates parallel research agents, classifies stakes, produces an execution plan
- `workflow-work` — Matches plan steps to specialized work agents, assembles deliverables
- `workflow-review` — Runs independent reviewer agents in parallel, synthesizes findings by severity
- `workflow-compound` — Extracts patterns/templates/preferences/failures into `.context/learnings/`

**Agent prompts** (markdown files in `agents/`):
- `agents/research/` — 9 agents: context-gatherer (inline), literature-scout, clinical-landscape, competitive-intel, stakeholder-mapper, regulatory-scanner, constraint-analyzer, precedent-researcher, plan-synthesizer
- `agents/work/` — 9 agents: executive-writer, analyst, decision-architect, clinical-strategist, meeting-orchestrator, regulatory-writer, due-diligence-analyst, market-access-strategist, proposal-writer
- `agents/review/` — 8 agents: clarity-reviewer, completeness-auditor, scientific-rigor-reviewer, regulatory-compliance-reviewer, tone-calibrator, strategic-coherence-reviewer, devils-advocate, risk-assessor
- `agents/compound/` — 5 agents: pattern-extractor, template-creator, preference-learner, failure-analyzer, domain-insight-capturer

**Standards**: `standards/consulting-documents.md` — MBB (McKinsey/Bain/BCG) formatting and quality standards applied to all consulting deliverables.

**Claude.ai project instructions**: `claude-ai-project/` — 6 numbered files that mirror the plugin's behavior for use as claude.ai project knowledge files.

**Learnings store**: `.context/learnings/` — Discrete markdown files with YAML frontmatter, organized by category. The Research phase searches these automatically. See `.context/learnings/INDEX.md` for the schema.

## Key Design Decisions

- **Agents are launched via the Agent tool** with `subagent_type: "general-purpose"`. Each agent's `.md` file is passed as part of the prompt — the files are instructions, not executed code.
- **Progressive loading**: Stakes level (routine/standard/high-stakes/board-regulatory) controls how many agents are launched. Routine = context-gatherer only; board/regulatory = all agents.
- **Research agents run in parallel** (Phase 3); work agents run sequentially (since steps may depend on previous output).
- **Review agents run in parallel** and independently (no reviewer sees other reviewers' findings).
- **context-gatherer is not a separate agent** — its function is performed inline by the research skill in Phase 2.

## MCP Tool Wiring

Research agents use these MCP tools (see `CONNECTORS.md` for full mapping):
- **PubMed** → literature-scout
- **bioRxiv/medRxiv** → literature-scout
- **ClinicalTrials.gov** → clinical-landscape
- **ChEMBL** → competitive-intel
- **Open Targets** → competitive-intel
- **WebSearch/WebFetch** → all agents (fallback when MCP tools unavailable)

Phase 0 of the research skill auto-discovers available tools and passes the inventory to all agents.

## Editing Guidelines

- Agent `.md` files follow a consistent structure: role description, workflow steps, output format. Preserve this structure when editing.
- Skill `SKILL.md` files have YAML frontmatter (`name`, `description`) — these are required for plugin registration.
- The insight file format (YAML frontmatter with type/date/category/task/outcome/tags/takeaway) is a contract — the research phase's grep-based search depends on it.
- Consulting deliverables must follow Pyramid Principle, MECE, SCR structure, and action titles per `standards/consulting-documents.md`.

## Installation

```bash
claude --plugin-dir ./CoworkPowers
```

# currentDate
Today's date is 2026-03-05.
