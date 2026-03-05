# Research Methodology

This guide covers how to systematically research any pharma/biotech or consulting task. Use the appropriate sections based on the task type.

## Step 1: Classify the Task

Determine:
- **Work type**: clinical development, literature review, competitive intelligence, regulatory strategy, communication, decision, meeting prep, consulting (due diligence, market access, proposal)
- **Stakes level**: Routine / Standard / High-Stakes / Board/Regulatory
- **Key questions**: What must this work answer?

## Step 2: Ask Clarifying Questions

For non-routine work, confirm:
- Therapeutic area and indication
- Specific drug/compound/target (if applicable)
- Development phase
- Target audience
- Comparators or competitors of interest
- Geographic scope (US, EU, global)
- Timeline and urgency

## Step 3: Literature Research

### PubMed Search Strategy

Use PubMed MCP tools with structured queries:

1. **Broad condition search**: `"[indication]"[MeSH Terms] AND [drug class]`
2. **Specific drug search**: `"[drug name]"[Title] AND Clinical Trial[Publication Type]`
3. **Mechanism search**: `"[MOA]" AND "[indication]"` — sorted by pub_date
4. **Endpoint/biomarker search**: `"[primary endpoint]" AND "[indication]" AND Clinical Trial[Publication Type]`
5. **Recent reviews**: `"[indication]" AND "[drug class]" AND Review[Publication Type]` — last 3 years

For each result, get full metadata. Find related articles to expand the evidence base. Get full text for key papers.

### bioRxiv/medRxiv Strategy

- Search `medrxiv` for clinical/medical preprints (categories: clinical trials, pharmacology, epidemiology)
- Search `biorxiv` for preclinical science (categories: pharmacology, molecular biology, immunology, cancer biology)
- Use recent_days=90 for cutting-edge research
- Check `search_published_preprints` to verify peer-review status
- **Always flag preprints as not peer-reviewed**

### Evidence Assessment

For each source, classify:
- **Relevance**: Directly relevant / Provides context / Background only
- **Quality**: Peer-reviewed RCT > Observational > Case report > Preprint > Expert opinion
- **Recency**: Current (<2 years) / Recent (2-5 years) / Historical

### Output Format

```markdown
## Literature Review

### Key Findings
| # | Citation | PMID/DOI | Type | Key Finding |
|---|----------|----------|------|-------------|

### Evidence Summary
[Synthesis: consensus, disagreements, gaps]

### Implications for This Task
[How findings shape the work]
```

## Step 4: Clinical Trial Landscape

### ClinicalTrials.gov Strategy

Use ClinicalTrials.gov MCP tools:

1. **Map active trials**: Search by condition + status (RECRUITING, ACTIVE_NOT_RECRUITING)
2. **Segment by phase**: Separate Phase 1/2/3 queries for pipeline view
3. **Analyze endpoints**: Use analyze_endpoints to understand measurement trends
4. **Identify investigators**: Search by condition + location for KOL identification
5. **Map sponsor pipelines**: Use search_by_sponsor for competitive intelligence
6. **Deep dive key trials**: Get full details for pivotal/Phase 3 trials

### Output Format

```markdown
## Clinical Trial Landscape: [Indication]

### Landscape Overview
- Total active trials: [N] recruiting, [N] active
- Phase distribution: Phase 1: [N], Phase 2: [N], Phase 3: [N]
- Top sponsors: [list]

### Pipeline by Phase
| NCT ID | Sponsor | Intervention | Phase | Status | Primary Endpoint | Est. Completion |
|--------|---------|-------------|-------|--------|-----------------|-----------------|

### Endpoint Analysis
| Endpoint | Frequency | Phases | Notes |
|----------|-----------|--------|-------|

### Key Investigators & Sites
| Investigator | Institution | Location | # Trials | Focus |
|-------------|-------------|----------|----------|-------|
```

## Step 5: Competitive Intelligence

### ChEMBL Strategy

1. **Find compounds**: compound_search by name or SMILES
2. **Get mechanism**: get_mechanism for MOA and target binding
3. **Get bioactivity**: get_bioactivity for IC50/EC50/Ki values
4. **Get ADMET**: get_admet for pharmacokinetic profile
5. **Find approved drugs**: drug_search by indication

### Open Targets Strategy

1. **Resolve IDs**: search_entities for Ensembl gene IDs and EFO disease IDs
2. **Query associations**: query_open_targets_graphql for:
   - Target-disease association scores
   - Genetic evidence (GWAS, rare variants)
   - Known drugs for target
   - Target tractability
   - Safety signals

### Output Format

```markdown
## Competitive Intelligence: [Indication / Drug Class]

### Competitor Pipeline Map
| Company | Compound | Target/MOA | Phase | Status | Differentiator |
|---------|----------|-----------|-------|--------|----------------|

### Compound Profiles
#### [Compound] — [Company]
- Target: [target] | MOA: [mechanism] | ChEMBL ID: [ID]
- Potency: [IC50/EC50] | ADMET: [key properties]
- Clinical: Phase [X], NCT[number], primary EP: [endpoint]

### Target Biology
- Target: [gene] | Disease association: [score]
- Genetic evidence: [GWAS/rare variant data]
- Tractability: [druggable modalities]

### Strategic Implications
[Strengths, vulnerabilities, whitespace, key risks]
```

## Step 6: Regulatory Landscape

Search for:
1. **FDA guidance**: `site:fda.gov guidance "[indication]"`
2. **EMA guidelines**: `site:ema.europa.eu guideline "[indication]"`
3. **ICH guidelines**: E6 (GCP), E8 (design), E9 (statistical), E17 (MRCT)
4. **Recent approvals**: What data packages succeeded?
5. **Rejections/CRLs**: What failed and why?
6. **Advisory committees**: How did AdCom vote on similar products?

### Designation Eligibility Assessment

| Pathway | Criteria | Eligibility | Benefit |
|---------|----------|-------------|---------|
| BTD | Serious condition + substantial improvement evidence | [assess] | Intensive FDA guidance, rolling review |
| Fast Track | Serious condition + unmet need | [assess] | Rolling review, more meetings |
| Accelerated Approval | Surrogate endpoint available | [assess] | Earlier approval |
| Orphan Drug | <200K US patients | [assess] | 7-year exclusivity |
| Priority Review | Significant improvement | [assess] | 6-month review |
| EMA PRIME | Unmet need, substantial benefit | [assess] | Enhanced support |

## Step 7: Stakeholder Analysis

### Stakeholder Categories (Pharma/Biotech)

**Internal**: Clinical team, commercial, executive leadership, R&D
**External**: KOLs, investigators, regulators, payers (NICE, ICER, G-BA), patient advocates, investors, partners

### Power-Interest Grid

| | Low Interest | High Interest |
|---|---|---|
| **High Power** | Keep Satisfied | Manage Closely |
| **Low Power** | Monitor | Keep Informed |

## Step 8: Constraint Analysis

Assess hard vs. soft constraints:
- **Clinical**: Enrollment feasibility, timeline, budget, manufacturing, regulatory requirements
- **Consulting**: Client expectations, political dynamics, information access, team capacity, contractual scope

Rate feasibility: Green/Yellow/Red for each dimension.

## Step 9: Synthesize into Plan

Merge all research into an execution plan:

```markdown
## Execution Plan

### Objectives
[What this work must accomplish]

### Success Criteria
[How we'll know it's done well]

### Evidence Base Summary
[Key findings from research]

### Execution Steps
| Step | What | Approach | Key Inputs |
|------|------|----------|-----------|

### Stakeholder Considerations
### Constraints and Risks
### Recommended Review Depth
```
