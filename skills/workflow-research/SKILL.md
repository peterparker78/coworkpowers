---
name: workflow-research
description: "Research and plan a knowledge work task thoroughly before execution. Optimized for pharma/biotech clinical development and consulting. Use when starting any significant work — competitive analysis, trial design, regulatory strategy, client deliverables, strategic decisions, or literature reviews. Triggers on requests like 'help me prepare for', 'I need to draft', 'analyze the landscape', 'research', or any high-stakes knowledge work."
---

# Research: Knowledge Work Research Workflow

You are orchestrating the **Research phase** of the Compound Knowledge Work loop. Your job is to thoroughly research a task and produce an actionable plan that makes execution straightforward.

**80% of compound knowledge work is in research and review.** Do not rush this phase.

## Process

### Phase 0: Discover Available Tools

Before starting research, check what MCP tools are available in the environment. Run a quick inventory:

**Scientific/Clinical tools to check for:**
- PubMed (search_articles, get_article_metadata, find_related_articles, get_full_text_article)
- bioRxiv/medRxiv (search_preprints, get_preprint, search_published_preprints)
- ClinicalTrials.gov (search_trials, get_trial_details, search_by_sponsor, search_investigators, analyze_endpoints, search_by_eligibility)
- ChEMBL (compound_search, drug_search, target_search, get_bioactivity, get_mechanism, get_admet)
- Open Targets (search_entities, query_open_targets_graphql)
- ScholarGateway (if available)

**General tools:**
- WebSearch, WebFetch (web research)
- Read, Write, Edit, Grep, Glob (file operations)
- Any email, calendar, CRM, chat, or knowledge base MCPs

Note which tools are available and pass this list to all agents so they can use them proactively. If a tool is unavailable, agents should fall back to WebSearch.

### Phase 1: Understand the Task

1. **Read the task description carefully.** If the user provided a document, file, or URL, read it thoroughly.

2. **Classify the work type:**
   - **Clinical Development**: trial design, protocol development, endpoint selection, site strategy, patient recruitment
   - **Literature Review**: systematic or targeted evidence gathering, publication analysis
   - **Competitive Intelligence**: pipeline analysis, market landscape, differentiation strategy
   - **Regulatory Strategy**: submission planning, guidance analysis, pathway selection, designation strategy
   - **Communication**: emails, memos, presentations, client reports, board materials
   - **Decision**: strategic choices, vendor/CRO selection, resource allocation, go/no-go
   - **Meeting Prep**: advisory boards, investigator meetings, client presentations, KOL engagement
   - **Consulting**: client deliverables, strategic frameworks, market assessments, due diligence

3. **Determine stakes level:**

| Level | Examples | Research Depth |
|-------|----------|----------------|
| **Routine** | Internal notes, quick lookups, status updates | context-gatherer only, skip clarifying questions |
| **Standard** | Team communications, standard analysis, internal presentations | context-gatherer + 1-2 domain agents |
| **High-Stakes** | Client deliverables, strategic decisions, advisory board prep | Full domain agent roster |
| **Board/Regulatory** | Board presentations, regulatory submissions, investor materials | All agents + constraint analysis |

### Phase 1.5: Ask Clarifying Questions

Before launching research, identify gaps. This prevents wasted research on the wrong problem.

**Ask one question at a time. Include your hypothesis with each.**

**Domain-specific questions to consider:**
- "What therapeutic area / indication? My hypothesis: [X] based on [context]"
- "What development phase? This determines which agents to deploy"
- "Who is the target audience — regulators, investors, clinical team, clients?"
- "What's the mechanism of action or drug class? This shapes competitive analysis"
- "Are there specific comparators or competitors to focus on?"
- "What geography — US, EU, global? This affects regulatory and trial landscape"
- "What's the timeline? This determines research depth"
- "Are there political sensitivities or confidential constraints?"

**Hard Gate for High-Stakes and Board/Regulatory work — you MUST get answers to:**
1. Who is the audience / decision-maker?
2. What does success look like?
3. What therapeutic area, indication, and phase?
4. What constraints exist (timeline, budget, political)?

**Skip clarifying questions when:**
- Routine work (internal notes, simple lookups)
- User provided a comprehensive brief
- Task is unambiguous

### Phase 2: Search Past Learnings (Context Gatherer)

This phase serves as the **context-gatherer** agent's function. Run it directly — do not launch a separate agent for this step.

Before any new research, check what we already know. This is where compounding pays off.

1. **Check the learnings directory** at `.context/learnings/` — scan for files matching the work type category.
2. **Search by category**: Grep `.context/learnings/` for the relevant category (e.g., `clinical-development`, `competitive-intelligence`, `regulatory-strategy`).
3. **Search by type**: Look specifically for `type: pattern` and `type: template` insights matching the current task.
4. **Search by keywords**: Grep across all learnings for domain terms — therapeutic area, drug names, company names, indication, mechanism.
5. **Search for preferences**: Grep for `type: preference` to find style, tone, and detail preferences from previous work.
6. **Search for failures**: Grep for `type: failure` to find documented anti-patterns to avoid.
7. **Read user-provided materials**: If the user attached files, URLs, or documents, read them thoroughly and extract key facts, requirements, and constraints.

If past learnings exist, incorporate them into the plan:
- **Reuse patterns** that worked before
- **Avoid failures** that were documented
- **Apply templates** if a relevant one exists
- **Honor preferences** from previous work

Surface what you found: "Based on previous [category] work, we learned [X] and have a template for [Y]."

Identify **research gaps** — what the domain-specific agents in Phase 3 need to investigate. Be specific: not "research the landscape" but "identify Phase 3 trials for [drug class] in [indication] by [top sponsors]."

### Phase 3: Parallel Research

Launch domain-specific research agents **in parallel** using the Agent tool. Each agent should be launched with `subagent_type: "general-purpose"`.

**Do NOT launch a context-gatherer agent** — Phase 2 already covers its function. Only launch the domain-specific agents listed in the roster below.

**Pass the stakes level, available tools, and past learnings summary to each agent.** Include the full agent instructions from the corresponding `agents/research/[agent-name].md` file in the agent prompt so the agent knows its role, workflow, and output format.

**How to launch each agent:**
```
Agent tool call:
  name: [agent-name] (e.g., "literature-scout")
  subagent_type: "general-purpose"
  prompt: [Include: the agent's .md instructions, task context, stakes level, available MCP tools, past learnings, and specific research questions from Phase 2 gaps]
```

Launch all agents in a single message so they run in parallel.

**Agent roster by work type (for Standard and above):**

| Work Type | Standard | High-Stakes | Board/Regulatory |
|-----------|----------|-------------|-----------------|
| **Clinical Development** | literature-scout, clinical-landscape | + competitive-intel, regulatory-scanner, stakeholder-mapper | + constraint-analyzer, precedent-researcher |
| **Literature Review** | literature-scout | + clinical-landscape, competitive-intel | + regulatory-scanner, precedent-researcher |
| **Competitive Intelligence** | competitive-intel | + clinical-landscape, literature-scout | + regulatory-scanner, stakeholder-mapper |
| **Regulatory Strategy** | regulatory-scanner, clinical-landscape | + literature-scout, competitive-intel, stakeholder-mapper | + constraint-analyzer, precedent-researcher |
| **Communication** | stakeholder-mapper | + precedent-researcher | + all remaining agents |
| **Decision** | stakeholder-mapper, constraint-analyzer | + competitive-intel, precedent-researcher | + all remaining agents |
| **Meeting Prep** | stakeholder-mapper | + literature-scout, precedent-researcher | + clinical-landscape, competitive-intel |
| **Consulting** | competitive-intel, stakeholder-mapper | + literature-scout, clinical-landscape | + regulatory-scanner, constraint-analyzer |

**For Routine stakes**: Phase 2 (context-gatherer function) only — no domain agents, no external searches.

**Agent instructions template** — pass this context to each agent:
```
Task: [task description]
Work type: [classified type]
Stakes: [routine/standard/high-stakes/board-regulatory]
Therapeutic area: [if known]
Indication: [if known]
Phase: [if known]
Available MCP tools: [list from Phase 0]
Past learnings found: [summary from Phase 2]
Specific focus for this agent: [what this agent should investigate]
```

**Run agents in parallel** — not sequentially. Each agent is independent and returns its own findings.

### Phase 4: Plan Synthesis

After all agents return, run the **plan-synthesizer** agent to merge findings into an actionable execution plan.

The plan should include:
1. **Objective**: What we're producing and for whom
2. **Key findings**: Top insights from each research agent (with citations)
3. **Recommended approach**: Step-by-step execution plan
4. **Agent assignment**: Which Work-phase agent handles each step
5. **Evidence base**: Key papers, trials, data points gathered
6. **Risk factors**: What could go wrong, what to watch for
7. **Past learnings applied**: What we're reusing from previous work
8. **Recommended review depth**: Which Review-phase agents to activate
9. **Open questions**: What we couldn't resolve in research

Present the plan to the user. Ask if they want to:
- Proceed to the Work phase (`/coworkpowers:workflow-work`)
- Adjust the plan
- Do additional research on specific areas

## Research Principles

### Front-Load the Thinking
Every minute in research saves ten in execution. The plan should make the Work phase mechanical.

### Progressive Loading
Match depth to stakes. A quick email doesn't need 9 parallel agents. A regulatory submission does.

### Cite Everything
Every claim, data point, and recommendation should trace back to a source — PubMed PMID, NCT number, ChEMBL ID, or URL.

### Compound the Knowledge
Flag insights worth capturing for the Compound phase. If you discover something reusable, note it in the plan.
