# CoworkPowers: Knowledge Work Superpowers for Pharma/Biotech & Consulting

A system that makes knowledge work compound over time. Four skills orchestrate specialized agents across research, execution, review, and learning capture phases — tuned for pharma/biotech clinical development and consulting.

## Skills

- **`/coworkpowers:workflow-research`** — Research and plan before execution. Discovers MCP tools, classifies stakes, asks clarifying questions, searches past learnings, runs parallel domain-specific research agents, synthesizes into an actionable plan.
- **`/coworkpowers:workflow-work`** — Execute the plan with specialized agents. Matches each step to the right agent (executive-writer, analyst, decision-architect, clinical-strategist, meeting-orchestrator, regulatory-writer, due-diligence-analyst, market-access-strategist, proposal-writer), validates output against success criteria, assembles the final deliverable. All consulting deliverables follow MBB standards defined in `standards/consulting-documents.md`.
- **`/coworkpowers:workflow-review`** — Multi-agent quality review from independent perspectives. Progressive loading: routine work skips review, standard gets 2-3 reviewers, high-stakes gets 5-6, board/regulatory gets all 8. Reviewers: clarity, completeness, scientific rigor, regulatory compliance, tone, strategic coherence, devil's advocate, risk assessment. Findings tagged Critical/Important/Minor.
- **`/coworkpowers:workflow-compound`** — Extract reusable learnings from completed work. Runs 5 extraction agents (pattern-extractor, template-creator, preference-learner, failure-analyzer, domain-insight-capturer). Stores each insight as a discrete markdown file in `.context/learnings/` with YAML frontmatter for searchability. This is where the compound loop closes.

## Domain Focus

This plugin is optimized for:
- **Pharma/Biotech Clinical Development**: trial design, competitive landscape, regulatory strategy, endpoint selection, investigator identification
- **Consulting**: strategic analysis, stakeholder management, decision frameworks, client deliverables, due diligence, market access & pricing, proposals & SOWs

## MCP Tool Integration

Research agents are wired to use these MCP tools directly:
- **PubMed**: Literature search, article metadata, related articles, full text
- **bioRxiv/medRxiv**: Preprint search, published preprint tracking
- **ClinicalTrials.gov**: Trial search, sponsor pipelines, investigators, endpoint analysis, eligibility matching
- **ChEMBL**: Compound search, target search, bioactivity data, drug mechanisms, ADMET
- **Open Targets**: Target-disease associations, genetic evidence, drug tractability

## Insight Storage

Past learnings are stored in `.context/learnings/` as individual markdown files with YAML frontmatter. Each insight is self-contained and searchable by type, category, tags, and keywords.

### Insight Types
- `pattern`: Reusable approach that worked
- `template`: Structural template for reuse
- `preference`: User/stakeholder style preferences
- `failure`: What didn't work and why
- `insight`: Domain knowledge worth remembering

### Categories
`clinical-development` | `literature-review` | `competitive-intelligence` | `communication` | `decision` | `meeting` | `regulatory-strategy` | `consulting` | `due-diligence` | `market-access` | `operations`

## Match Rigor to Stakes

- **Routine** (internal notes, quick lookups): context-gatherer only
- **Standard** (team comms, standard analysis): + 1-2 domain agents
- **High-stakes** (client deliverables, strategic decisions): + full domain agent roster
- **Board/Regulatory** (board presentations, regulatory submissions): All agents + constraint analysis
