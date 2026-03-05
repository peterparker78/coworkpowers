# Prompt Templates for Claude.ai

Copy-paste these prompts to trigger each workflow phase. Replace [bracketed items] with your specifics.

---

## Phase 1: Research

### Full Research Prompt

```
I need to research [topic/task] for [purpose].

Context:
- Therapeutic area: [indication]
- Drug/compound: [name, if applicable]
- Development phase: [Phase 1/2/3/filed/approved]
- Target audience: [board, client, clinical team, regulators]
- Key comparators: [competitor drugs/companies]
- Geographic scope: [US, EU, global]
- Stakes level: [routine/standard/high-stakes/board-regulatory]

Please follow the Research Methodology from project knowledge:
1. Search PubMed for relevant published literature
2. Check bioRxiv/medRxiv for recent preprints
3. Map the clinical trial landscape on ClinicalTrials.gov
4. Analyze competitor pipelines using ChEMBL and ClinicalTrials.gov sponsor search
5. Scan the regulatory landscape (guidances, precedents, designations)
6. Synthesize into a structured execution plan

For each finding, include citations (PMID, NCT, DOI, ChEMBL ID).
```

### Quick Literature Search

```
Search PubMed and bioRxiv for recent evidence on [topic].

Focus on:
- [Specific question 1]
- [Specific question 2]
- Clinical trials with results in [indication] for [drug class]

Provide a structured evidence table with citations, evidence level, and key findings.
```

### Competitive Landscape

```
Map the competitive landscape for [indication/drug class].

I need:
1. All active Phase 2 and Phase 3 trials (ClinicalTrials.gov)
2. Sponsor pipeline analysis for [company 1, company 2, ...]
3. Compound profiles from ChEMBL for key competitors
4. Target biology from Open Targets for [gene/target]
5. Competitive positioning analysis — who's ahead, who's differentiated, where's whitespace

Output as a competitor pipeline table + compound profiles + strategic implications.
```

### Regulatory Scan

```
Analyze the regulatory landscape for [product type] in [indication].

Cover:
1. Relevant FDA/EMA guidance documents
2. Regulatory precedents (recent approvals and rejections in this space)
3. Designation eligibility (BTD, Fast Track, Orphan, Accelerated Approval)
4. Advisory committee precedents
5. Key regulatory risks

Output as regulatory landscape summary with precedent table and designation assessment.
```

---

## Phase 2: Execute

### Client Report

```
Using the research findings above, draft a [report type] for [audience].

Follow MBB consulting standards from project knowledge:
- Pyramid Principle: lead with the answer
- SCR structure for the executive summary
- Action titles on every section heading
- Every claim cited with source
- Professional formatting

Structure:
1. Executive Summary (1 page, must stand alone)
2. [Section 2 topic]
3. [Section 3 topic]
...
N. Recommendations and Next Steps

Output as a complete, polished document ready for review.
```

### Due Diligence Report

```
Conduct a due diligence assessment of [asset/company] for [purpose: licensing/acquisition/partnership].

Use the Due Diligence template from project knowledge. Assess across:
1. Science & Mechanism
2. Clinical Development
3. Competitive Position
4. Commercial Potential
5. Risk Assessment

Provide an overall Go / Conditional Go / No-Go recommendation with scorecard.
Include risk-adjusted valuation and comparable transactions where possible.
```

### Market Access Strategy

```
Develop a market access strategy for [product] in [indication].

Cover all 5 dimensions:
1. Value Proposition
2. Payer Landscape (US + EU HTA bodies: NICE, G-BA, HAS, AIFA)
3. Pricing Strategy (with pricing corridor analysis)
4. Evidence Requirements (gap analysis)
5. Access Barriers & Mitigation

Include pricing corridor analysis table and evidence gap matrix.
Recommend launch sequencing strategy with reference pricing implications.
```

### Client Proposal

```
Draft a [full proposal / SOW / expansion proposal] for [client] regarding [project topic].

Project context:
- Client challenge: [what they're facing]
- Proposed scope: [what we'd do]
- Timeline: [duration]
- Team: [who would work on it]
- Budget range: [if known]

Follow the proposal template from project knowledge.
The "Understanding of the Challenge" section is the most important — show we understand their problem better than they do.
Use client-centric language throughout.
```

### Clinical Development Plan

```
Design a clinical development strategy for [compound] in [indication].

Include:
- Target Product Profile (minimum/target/aspirational)
- Phase [X] protocol concept (design, population, endpoints, sample size)
- Endpoint rationale with regulatory precedent
- Enrollment strategy and feasibility assessment
- Regulatory strategy (designations, pathway, pre-submission interactions)
- Timeline with key milestones
- Risk register

Ground every design decision in regulatory precedent and competitive benchmarks.
```

### Strategic Decision

```
Help me structure a decision about [decision topic].

Context: [background]
Options: [Option A vs. Option B vs. ...]
Constraints: [budget, timeline, political, regulatory]
Decision maker: [who decides]

Use the Decision Architecture approach from project knowledge:
1. Frame the problem
2. Apply the most relevant framework(s)
3. Quantify trade-offs
4. Make a recommendation with confidence level and kill criteria
```

---

## Phase 3: Review

### Full Review

```
Review the deliverable above for quality. Apply these checks from the Review & Quality guide:

1. **Clarity**: Structure, comprehension, scannability, precision
2. **Completeness**: All objectives addressed? Citations present? Gaps?
3. **Scientific Rigor**: Claims accurate? Evidence quality? Cross-trial caveats?
4. **Tone**: Appropriate for [target audience]?
5. **Strategic Coherence**: Logic chain sound? Recommendations follow from analysis?

Tag each finding as Critical / Important / Minor.
Provide specific fixes, not just descriptions of problems.
```

### Quick Review

```
Quick review of the above for:
- Any unsupported claims (needs citation)
- Clarity issues (confusing sections)
- Missing content
- Tone check for [audience]

Flag only Critical and Important issues.
```

### Stress Test (Board/Regulatory)

```
Stress-test this deliverable:

1. **Devil's Advocate**: What's the strongest counter-argument? What assumptions could be wrong? What's missing?
2. **Risk Assessment**: What could go wrong? Risk heat map with probability × impact.
3. **Pre-mortem**: Imagine this recommendation failed in 18 months. What went wrong?

Be genuine — construct real counter-arguments, not straw men.
```

---

## Phase 4: Compound (After Completing Work)

```
Now that this work is complete, help me capture learnings:

1. **What worked well?** (Approaches, frameworks, search strategies to reuse)
2. **What didn't work?** (Dead ends, failed approaches, things to avoid)
3. **Templates to save?** (Document structures, table formats worth reusing)
4. **Domain insights?** (Scientific facts, regulatory precedents, competitive intel worth remembering)
5. **Process preferences?** (Format, tone, detail level preferences to honor next time)

Summarize each learning in one sentence with context for when to apply it.
```
