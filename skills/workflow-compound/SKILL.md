---
name: workflow-compound
description: "Extract reusable learnings from completed work — patterns, templates, preferences, failures, and domain insights. Use after completing a task (post-Work or post-Review) to make the next similar task faster. Triggers on requests like 'capture learnings', 'what did we learn', 'compound this', or when finishing a significant piece of work."
---

# Compound: Learning Extraction Workflow

You are orchestrating the **Compound phase** of the Compound Knowledge Work loop. Your job is to extract reusable knowledge from completed work and store it as discrete, searchable insight files that make future similar work faster and better.

**This is where the compound effect happens.** Without this phase, every task starts from scratch. With it, your fourth competitive analysis takes a quarter of the time of your first.

## Process

### Phase 1: Gather the Work Product

1. **Read the completed deliverable** — the final output from Work (and Review, if it was run).
2. **Read the Research plan** — what was planned vs. what was actually delivered.
3. **Read the Review findings** (if Review was run) — what was flagged and what was fixed.
4. **Ask the user for outcome feedback**: "How did this land? Any feedback from the audience?"
   - If the user provides feedback (e.g., "Board loved it", "Client wanted more detail on X", "Regulator pushed back on Y"), incorporate it as the most valuable signal.
   - If no feedback yet, proceed with what we can extract — and note that outcome feedback should be added when available.

### Phase 2: Run Extraction Agents

Launch extraction agents in parallel using the Agent tool with `subagent_type: "general-purpose"`. Each agent examines the work from a different angle.

**Agent roster — always run all five for any non-routine task:**

| Agent | What It Extracts |
|-------|-----------------|
| **pattern-extractor** | Reusable approaches that worked (or didn't) — generalizable methods |
| **template-creator** | Structural templates from the deliverable that can be reused |
| **preference-learner** | User and stakeholder style/format/tone preferences discovered |
| **failure-analyzer** | What didn't work, what was harder than expected, what to avoid |
| **domain-insight-capturer** | Domain-specific knowledge worth remembering (scientific, regulatory, competitive facts) |

**Pass to each agent:**
- The completed deliverable
- The original plan and objectives
- Review findings (if available)
- User feedback (if provided)
- The work type and stakes classification
- The therapeutic area, indication, and other domain context

### Phase 3: Curate and Store

After agents return their findings, curate the insights:

1. **Deduplicate.** If multiple agents flagged the same insight, merge into one.
2. **Assess compound value.** For each insight:
   - **Frequency**: How often will similar situations arise?
   - **Impact**: How much will this improve future outcomes?
   - **Specificity**: Is this broadly applicable or narrowly useful?
   - Only store insights with Medium or High compound value. Don't store noise.
3. **Create category directories** if they don't exist.
4. **Write each insight as a separate file** in `.context/learnings/[category]/`.

**File naming convention**: `YYYY-MM-DD-[short-descriptive-name].md`

**File format** (YAML frontmatter + markdown body):

```markdown
---
type: pattern | template | preference | failure | insight
date: YYYY-MM-DD
category: clinical-development | literature-review | competitive-intelligence | communication | decision | meeting | regulatory-strategy | consulting | operations
task: Brief description of the original task
outcome: success | partial | failure
tags: [comma-separated: therapeutic-area, drug-names, companies, frameworks, stakeholders]
takeaway: One-sentence key learning
---

# Descriptive Title

## Context
[What task this came from — enough context to understand when this applies]

## The Learning
[The actual insight — specific and actionable, not vague]

## When to Apply
[Specific situations where this insight is relevant — trigger conditions]
```

5. **Update INDEX.md** if new categories were created.

### Phase 4: Present Summary

Show the user what was captured:

```markdown
## Compound Summary

### Learnings Captured: [N] insights

| # | Type | Category | Title | Takeaway | File |
|---|------|----------|-------|----------|------|
| 1 | pattern | ... | ... | ... | .context/learnings/[category]/[file].md |
| 2 | template | ... | ... | ... | ... |
| 3 | preference | ... | ... | ... | ... |

### High-Value Insights
[The 2-3 most impactful learnings — why they matter for future work]

### Outcome Feedback Needed
[If the user hasn't provided outcome feedback yet, remind them to add it when available — this is the most valuable compounding signal]

### Next Time This Type of Work Comes Up
[Concrete prediction: "Next time you do a [work type] for [audience], the Research phase will load these patterns and templates, saving approximately [X] of the research and [Y] of the execution time."]
```

## Compound Principles

### Granular Beats Monolithic
One insight per file. A 50-file learnings directory that's searchable by grep beats a single "lessons learned" document that nobody reads. The Research phase's context-gatherer searches by category, type, and keywords — granular files make retrieval work.

### Specific Beats Generic
"Be thorough" is not a useful learning. "For board-level competitive analyses, lead with the market size and pipeline count before diving into individual competitors — the board wants the 30,000-foot view first" is a useful learning.

### Failures Are the Most Valuable
A documented failure with clear context (what happened, why, how to avoid it) is more valuable than five success patterns. Failures prevent repeated mistakes.

### Preferences Compound Fastest
Capturing that "this user prefers bullet points over prose for internal comms" or "this client wants competitive analyses organized by mechanism class, not by company" means the next deliverable starts closer to right.

### Templates Are Force Multipliers
A structural template from a successful deliverable — the actual outline, section headings, table formats — is immediately reusable and dramatically accelerates future Work phase execution.

### Tag Generously
Tags make retrieval work. Include therapeutic area, drug names, company names, stakeholder names, frameworks used, and deliverable types. More tags = better future search results.
