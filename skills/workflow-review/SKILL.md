---
name: workflow-review
description: "Multi-agent quality review of completed work from multiple perspectives. Use after the work phase to ensure deliverables are clear, accurate, complete, and appropriate before delivery. Triggers on requests like 'review this', 'check my work', 'quality check', or when moving from execution to delivery."
---

# Review: Multi-Agent Quality Review Workflow

You are orchestrating the **Review phase** of the Compound Knowledge Work loop. Your job is to run the completed deliverable through multiple independent reviewers, each examining it from a different angle, then synthesize their findings into a prioritized list of improvements.

**Progressive loading beats uniform rigor.** Not every deliverable needs 8 reviewers. Match review depth to stakes.

## Process

### Phase 1: Load the Deliverable

1. **Read the completed work** from the Work phase — the full deliverable.
2. **Recall the context** from Research: objectives, success criteria, audience, stakeholder considerations, constraints.
3. **Confirm the stakes level** (from Research classification):
   - **Routine**: Quick self-check only — skip this workflow entirely
   - **Standard**: 2-3 reviewers (clarity + completeness + 1 domain reviewer)
   - **High-Stakes**: 5-6 reviewers (core set + domain-specific)
   - **Board/Regulatory**: All 8 reviewers

### Phase 2: Select the Review Panel

Based on stakes level and work type, select reviewers from the roster:

**Core reviewers (always included for Standard+):**

| Reviewer | What They Check |
|----------|----------------|
| **clarity-reviewer** | Is this understandable? Is the structure logical? Can someone skim it? |
| **completeness-auditor** | Is anything missing? Are all plan objectives addressed? Are citations complete? |

**Domain reviewers (added for High-Stakes+, selected by work type):**

| Reviewer | What They Check | Include For |
|----------|----------------|-------------|
| **scientific-rigor-reviewer** | Are claims evidence-based? Are statistics correct? Are limitations noted? | Literature reviews, clinical strategy, any data-heavy deliverable |
| **regulatory-compliance-reviewer** | Does this meet agency expectations? Is terminology correct? Are precedents cited? | Regulatory documents, clinical development plans, designation requests |
| **tone-calibrator** | Does the tone match the audience? Is it appropriately formal/informal? | Client deliverables, board materials, communications |
| **strategic-coherence-reviewer** | Does this align with the bigger picture? Are recommendations consistent with strategy? | Strategy documents, portfolio decisions, consulting deliverables |

**Stress-test reviewers (added for Board/Regulatory):**

| Reviewer | What They Check |
|----------|----------------|
| **devils-advocate** | What's the strongest counter-argument? What are we missing? |
| **risk-assessor** | What could go wrong? What are the unintended consequences? |

**Review panel by stakes level:**

| Stakes | Reviewers |
|--------|-----------|
| **Routine** | None (self-check in Work phase suffices) |
| **Standard** | clarity-reviewer + completeness-auditor + 1 domain reviewer |
| **High-Stakes** | clarity + completeness + 2-3 domain reviewers |
| **Board/Regulatory** | All 8 reviewers |

**Domain reviewer selection by work type:**

| Work Type | Domain Reviewers |
|-----------|-----------------|
| Clinical Development | scientific-rigor-reviewer, regulatory-compliance-reviewer |
| Literature Review | scientific-rigor-reviewer |
| Competitive Intelligence | strategic-coherence-reviewer |
| Regulatory Strategy | regulatory-compliance-reviewer, scientific-rigor-reviewer |
| Communication | tone-calibrator, strategic-coherence-reviewer |
| Decision | strategic-coherence-reviewer, devils-advocate |
| Meeting Prep | tone-calibrator, completeness-auditor |
| Consulting | strategic-coherence-reviewer, tone-calibrator |

### Phase 3: Run Reviews in Parallel

Launch all selected reviewers simultaneously using the Agent tool with `subagent_type: "general-purpose"`. Each reviewer receives:
- The full deliverable text
- The original objectives and success criteria from Research
- The audience and stakeholder context
- Their specific review instructions from `agents/review/[reviewer-name].md`

**Each reviewer returns findings tagged by severity:**

| Severity | Definition | Action |
|----------|-----------|--------|
| **Critical** | Must fix before delivery. Factual errors, missing key content, regulatory non-compliance, wrong audience tone | Fix immediately |
| **Important** | Should fix. Strengthens the deliverable. Gaps in logic, weak citations, unclear sections | Fix unless time-constrained |
| **Minor** | Nice to fix. Polish items. Word choice, formatting, optional additions | Fix if time permits |

### Phase 4: Synthesize and Prioritize

After all reviewers return:

1. **Deduplicate findings.** If multiple reviewers flag the same issue, consolidate and note agreement (stronger signal).
2. **Sort by severity.** Critical first, then Important, then Minor.
3. **Group by section.** Organize findings by which part of the deliverable they affect.
4. **Assess conflicts.** If reviewers disagree (e.g., tone-calibrator says "too formal" but regulatory-compliance says "appropriate"), flag for user decision.

Present the review summary:

```markdown
## Review Summary

### Review Panel
[List of reviewers activated and why]

### Critical Findings (Must Fix)
| # | Finding | Reviewer(s) | Section | Recommended Fix |
|---|---------|------------|---------|----------------|
| 1 | ... | ... | ... | ... |

### Important Findings (Should Fix)
| # | Finding | Reviewer(s) | Section | Recommended Fix |
|---|---------|------------|---------|----------------|
| 1 | ... | ... | ... | ... |

### Minor Findings (Nice to Fix)
| # | Finding | Reviewer(s) | Section | Recommended Fix |
|---|---------|------------|---------|----------------|
| 1 | ... | ... | ... | ... |

### Reviewer Conflicts
[Where reviewers disagreed — both perspectives, recommendation for resolution]

### Overall Assessment
**Delivery readiness**: [Ready / Ready with fixes / Needs revision]
**Confidence level**: [High / Medium / Low]
**Strongest sections**: [What's working well]
**Weakest sections**: [Where the most work is needed]
```

### Phase 5: Apply Fixes

After presenting the review:

1. **Ask the user** if they want to:
   - Apply all Critical + Important fixes automatically
   - Review each fix individually
   - Apply only Critical fixes
   - Skip fixes and proceed to delivery

2. **Apply approved fixes** to the deliverable.

3. **Present the revised deliverable** with a change summary.

4. **Recommend the Compound phase** (`/coworkpowers:workflow-compound`) to capture learnings from this work.

## Review Principles

### Independence Matters
Each reviewer operates independently — they don't see other reviewers' findings. This prevents anchoring and ensures diverse perspectives.

### Severity Discipline
Reviewers must tag every finding with a severity. This prevents "everything is important" syndrome. If a reviewer can't distinguish severity levels, their review is too shallow.

### Fix, Don't Just Flag
Every finding should include a recommended fix, not just a description of the problem. "Section 3 is unclear" is a flag. "Section 3 should lead with the conclusion, then support with data" is a fix.

### Respect the Audience
The review should serve the audience, not the reviewer's preferences. A board memo should be brief even if the completeness-auditor wants more detail.
