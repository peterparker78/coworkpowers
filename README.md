# CoworkPowers

**Knowledge work superpowers for pharma/biotech consulting and clinical development.**

CoworkPowers is a Claude Code plugin that gives Claude systematic capabilities for tackling knowledge work in pharma/biotech and consulting. Each completed task feeds insights back into the system, making the next similar task faster and better.

## The Compound Loop

1. **Research** (`/coworkpowers:workflow-research`) — Thoroughly research the task, search past learnings, gather scientific and competitive context
2. **Work** (`/coworkpowers:workflow-work`) — Execute the plan with specialized agents
3. **Review** (`/coworkpowers:workflow-review`) — Multi-agent quality review from multiple perspectives
4. **Compound** (`/coworkpowers:workflow-compound`) — Extract patterns, templates, and preferences for next time

## Domain Focus

Built for two overlapping worlds:

- **Pharma/Biotech Clinical Development**: trial landscape analysis, competitive intelligence, regulatory strategy, endpoint selection, investigator identification, literature reviews
- **Consulting**: strategic analysis, client deliverables, stakeholder management, decision frameworks

## MCP Tool Integration

Research agents are wired to use these scientific databases directly:

| Tool | What It Provides |
|------|-----------------|
| **PubMed** | Published biomedical literature, clinical trial results, systematic reviews |
| **bioRxiv / medRxiv** | Preprints — cutting-edge research before peer review |
| **ClinicalTrials.gov** | Trial landscape, sponsor pipelines, investigators, endpoints, eligibility |
| **ChEMBL** | Compound profiles, target biology, bioactivity data, drug mechanisms |
| **Open Targets** | Target-disease associations, genetic evidence, drug tractability |

No MCP connections are required — the plugin works with web search and local files alone. But connected tools make research dramatically richer.

## Research Phase — How It Works

### Phase 0: Tool Discovery
Automatically detects which MCP tools are available and passes the inventory to all agents.

### Phase 1: Task Classification
Classifies the work type (clinical development, literature review, competitive intelligence, regulatory strategy, communication, decision, meeting prep, consulting) and stakes level (routine, standard, high-stakes, board/regulatory).

### Phase 1.5: Clarifying Questions
For non-routine work, asks targeted domain questions: therapeutic area, phase, indication, audience, comparators, timeline.

### Phase 2: Past Learnings Search
Searches `.context/learnings/` for patterns, templates, preferences, and failures from previous work.

### Phase 3: Parallel Research Agents
Launches domain-specific agents scaled to stakes level:

| Agent | Role |
|-------|------|
| **context-gatherer** | Past learnings, user materials, gap identification |
| **literature-scout** | PubMed + bioRxiv/medRxiv literature search and synthesis |
| **clinical-landscape** | ClinicalTrials.gov trial mapping, endpoints, investigators |
| **competitive-intel** | Sponsor pipelines, ChEMBL compounds, Open Targets biology |
| **stakeholder-mapper** | Stakeholder interests, influence, communication strategy |
| **regulatory-scanner** | FDA/EMA guidance, precedents, pathway options |
| **constraint-analyzer** | Budget, timeline, feasibility, risk assessment |
| **precedent-researcher** | Internal learnings + industry best practices |

### Phase 4: Plan Synthesis
The **plan-synthesizer** merges all agent outputs into a structured execution plan.

## Work Phase — How It Works

After Research produces a plan, the Work phase executes it step by step using specialized agents:

| Agent | Role | When Used |
|-------|------|-----------|
| **executive-writer** | Client reports, board materials, investor decks, strategic memos | Any written deliverable for an audience |
| **analyst** | Competitive analysis, market sizing, data synthesis, benchmarking | Quantitative or structured analytical work |
| **decision-architect** | Strategic decisions, go/no-go, portfolio prioritization | Choices with trade-offs requiring frameworks |
| **clinical-strategist** | Protocol design, endpoint selection, development plans, site strategy | Clinical development-specific execution |
| **meeting-orchestrator** | Advisory boards, investigator meetings, KOL engagement | Meeting preparation or facilitation |
| **regulatory-writer** | Briefing documents, designation requests, submission plans | Regulatory-specific deliverables |
| **due-diligence-analyst** | Asset/company/deal evaluation, licensing assessments | Due diligence across clinical, regulatory, competitive, and commercial dimensions |
| **market-access-strategist** | Pricing strategy, payer landscape, HTA readiness, value dossiers | Market access, pricing, and reimbursement strategy |
| **proposal-writer** | Client proposals, SOWs, engagement scoping, capabilities overviews | Business development and engagement scoping |

Each step in the plan is matched to the right agent. The Work skill assembles outputs into a cohesive final deliverable and recommends review depth based on stakes level.

All consulting deliverables follow **MBB standards** (McKinsey, Bain, BCG) defined in `standards/consulting-documents.md` — Pyramid Principle, MECE frameworks, SCR structure, action titles, and professional formatting for both Word and PowerPoint output. Documents are generated using the `docx` and `pptx` skills.

## Review Phase — How It Works

After Work produces a deliverable, the Review phase runs independent quality checks in parallel. Each reviewer examines the work from a different angle, tags findings by severity (Critical/Important/Minor), and suggests specific fixes.

**Core reviewers (always included):**

| Reviewer | What They Check |
|----------|----------------|
| **clarity-reviewer** | Structure, readability, scannability — can someone skim it in 2 minutes? |
| **completeness-auditor** | Plan objectives addressed, citations present, no content gaps |

**Domain reviewers (selected by work type):**

| Reviewer | What They Check | Include For |
|----------|----------------|-------------|
| **scientific-rigor-reviewer** | Evidence quality, statistical claims, cross-trial comparison caveats | Clinical, literature, data-heavy work |
| **regulatory-compliance-reviewer** | Agency terminology, claim appropriateness, format compliance | Regulatory documents, clinical plans |
| **tone-calibrator** | Audience-appropriate formality, confidence calibration | Client deliverables, board materials |
| **strategic-coherence-reviewer** | Logic chain, narrative consistency, actionable recommendations | Strategy, consulting, decisions |

**Stress-test reviewers (Board/Regulatory only):**

| Reviewer | What They Check |
|----------|----------------|
| **devils-advocate** | Strongest counter-argument, blind spots, untested assumptions |
| **risk-assessor** | What could go wrong, probability x impact, missing mitigations |

**Progressive loading by stakes:**

| Stakes | Reviewers |
|--------|-----------|
| Routine | None |
| Standard | 2-3 (core + 1 domain) |
| High-Stakes | 5-6 (core + domain) |
| Board/Regulatory | All 8 |

## Compound Phase — How It Works

After Work and Review complete, the Compound phase extracts reusable knowledge:

| Agent | What It Extracts |
|-------|-----------------|
| **pattern-extractor** | Reusable approaches that worked (or anti-patterns that didn't) |
| **template-creator** | Document skeletons, table formats, outlines ready for reuse |
| **preference-learner** | User and stakeholder style, format, tone preferences |
| **failure-analyzer** | What went wrong, root causes, prevention strategies |
| **domain-insight-capturer** | Scientific facts, regulatory precedents, competitive intel worth remembering |

Each insight is stored as a separate markdown file in `.context/learnings/[category]/` with YAML frontmatter (type, date, category, tags, takeaway). The Research phase searches these automatically on future tasks — loading patterns, applying templates, honoring preferences, and avoiding documented failures.

**The practical effect**: Your first competitive landscape might take the full Research > Work > Review cycle. Your fourth loads the template, applies your preferred format, reuses the search strategy that worked, and avoids the mistakes from the first three.

## Match Rigor to Stakes

| Stakes | When | Agents |
|--------|------|--------|
| **Routine** | Internal notes, quick lookups | context-gatherer only |
| **Standard** | Team comms, standard analysis | + 1-2 domain agents |
| **High-Stakes** | Client deliverables, strategic decisions | Full domain roster |
| **Board/Regulatory** | Board presentations, submissions | All agents + constraints |

## Insight Storage

Each insight is a self-contained markdown file:

```markdown
---
type: pattern | template | preference | failure | insight
date: 2026-03-05
category: clinical-development | competitive-intelligence | regulatory-strategy | ...
task: Brief description
outcome: success | partial | failure
tags: therapeutic-area, drug-name, company, framework
takeaway: One-sentence key learning
---

# Title

## Context
## The Learning
## When to Apply
```

## Installation

```bash
# In Claude Code
claude --plugin-dir ./CoworkPowers
```

## Plugin Structure

```
CoworkPowers/
  .claude-plugin/
    plugin.json
  skills/
    workflow-research/SKILL.md
    workflow-work/SKILL.md
    workflow-review/SKILL.md
    workflow-compound/SKILL.md
  agents/
    research/
      context-gatherer.md
      literature-scout.md
      clinical-landscape.md
      competitive-intel.md
      stakeholder-mapper.md
      regulatory-scanner.md
      constraint-analyzer.md
      precedent-researcher.md
      plan-synthesizer.md
    work/
      executive-writer.md
      analyst.md
      decision-architect.md
      clinical-strategist.md
      meeting-orchestrator.md
      regulatory-writer.md
      due-diligence-analyst.md
      market-access-strategist.md
      proposal-writer.md
    review/
      clarity-reviewer.md
      completeness-auditor.md
      scientific-rigor-reviewer.md
      regulatory-compliance-reviewer.md
      tone-calibrator.md
      strategic-coherence-reviewer.md
      devils-advocate.md
      risk-assessor.md
    compound/
      pattern-extractor.md
      template-creator.md
      preference-learner.md
      failure-analyzer.md
      domain-insight-capturer.md
  standards/
    consulting-documents.md
  .context/
    learnings/
      INDEX.md
  .gitignore
  CLAUDE.md
  CONNECTORS.md
  README.md
```

## License

MIT
