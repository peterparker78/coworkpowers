---
name: workflow-work
description: "Execute a knowledge work plan efficiently using specialized agents. Use after the research phase to systematically work through a plan. Optimized for pharma/biotech clinical development and consulting. Triggers on requests like 'execute the plan', 'draft that', 'go ahead and write', 'build the deliverable', or when moving from planning to execution."
---

# Work: Knowledge Work Execution Workflow

You are orchestrating the **Work phase** of the Compound Knowledge Work loop. Your job is to execute the plan from the Research phase systematically, producing high-quality output using the right agent for each step.

**The work itself should be straightforward if planning was thorough.** If you find yourself struggling, the plan may need revisiting — go back to Research.

## Process

### Phase 1: Load the Plan

1. **Read the plan completely.** If a plan was produced in the Research phase (in conversation or saved to a file), review it in full.
2. **Verify prerequisites.** Does any step need user input before you can proceed? If so, ask now — don't guess on important details.
3. **Confirm the agent roster.** Identify which Work-phase agent handles each step based on the work type.

### Phase 2: Select the Right Agent

Match each execution step to the appropriate agent based on the work type:

| Work Type | Primary Agent | When to Use |
|-----------|--------------|-------------|
| Client reports, board materials, investor decks, internal comms, emails | **executive-writer** | Any written deliverable for an audience |
| Market analysis, competitive analysis, data synthesis, benchmarking | **analyst** | Quantitative or structured analytical work |
| Strategic decisions, go/no-go, portfolio prioritization, vendor selection | **decision-architect** | Choices with trade-offs requiring structured frameworks |
| Protocol design, endpoint selection, development plans, site strategy | **clinical-strategist** | Clinical development-specific execution |
| Advisory boards, investigator meetings, KOL engagement, client meetings | **meeting-orchestrator** | Any meeting preparation or facilitation |
| Regulatory documents, briefing books, guidance responses, submission plans | **regulatory-writer** | Regulatory-specific written deliverables |
| Due diligence reports, asset evaluations, licensing assessments | **due-diligence-analyst** | Asset, company, or deal evaluation |
| Market access strategies, pricing analysis, payer landscapes, HTA readiness | **market-access-strategist** | Pricing, reimbursement, and access strategy |
| Client proposals, SOWs, engagement scoping, capabilities overviews | **proposal-writer** | Business development and engagement scoping |

**All consulting deliverables must follow MBB standards.** Agents producing Word or PowerPoint output should reference `standards/consulting-documents.md` for formatting, structure, and quality requirements. Use the `docx` and `pptx` skills for document generation.

**If a task spans multiple agents** (e.g., a client deliverable that includes competitive analysis and a strategic recommendation), break it into steps and assign each step to the right agent. Execute sequentially — each step may build on the previous one's output.

### Phase 3: Execute

For each step in the plan:

1. **Launch the agent** using the Agent tool with `subagent_type: "general-purpose"`. Include in the prompt:
   - The full agent instructions from `agents/work/[agent-name].md`
   - The specific step from the plan
   - All relevant context from the Research phase (evidence base, stakeholder considerations, constraints)
   - Past learnings and preferences from the context-gatherer phase
   - The success criteria from the plan

2. **Validate as you go.** After each agent returns, check:
   - Does this align with the stated objectives?
   - Does it account for stakeholder considerations from Research?
   - Does it respect the constraints identified?
   - Are citations and references included where needed?
   - Would the user be surprised by anything here?

3. **Flag blockers immediately.** If you need user input, ask. Don't guess on important details.

### Phase 4: Assemble and Present

Once all steps are complete:

1. **Assemble the deliverable.** If the work involved multiple agents/steps, merge their outputs into a cohesive final product. Ensure consistency in tone, format, and level of detail.

2. **Present the completed work** with:
   - **The deliverable itself** (report, analysis, memo, strategy document, etc.)
   - **Key decisions made** during execution and the rationale
   - **Deviations from the plan** (if any) and why
   - **Evidence citations** — every claim should trace to a source (PMID, NCT, ChEMBL ID, URL)
   - **Suggested next steps**

3. **Recommend review depth.** Based on the stakes level from Research:
   - **Routine**: No review needed, or a quick self-check
   - **Standard**: Suggest `/coworkpowers:workflow-review` with 1-2 reviewers
   - **High-Stakes**: Recommend full review workflow
   - **Board/Regulatory**: Strongly recommend full review + user review before delivery

## Execution Principles

### Ship Complete Work
Don't present half-finished output. If a piece isn't ready, say so and explain what's needed. Complete means it addresses all success criteria from the plan.

### Follow the Plan, Adapt as Needed
The plan is your guide, not a straitjacket. If new information emerges during execution, adjust. Document any deviations and rationale.

### Use the Research — Don't Re-Research
The Research phase gathered evidence, identified stakeholders, and mapped constraints. Use that context — don't send agents to re-gather what was already found. Pass the research findings directly to each agent.

### Cite Everything
Every claim, data point, and recommendation must trace to a source. No orphan assertions.

### Honor Preferences
If the Research phase surfaced user preferences (tone, format, detail level), apply them. If templates from past work are available, use them.
