# Learnings Index

This directory stores insights extracted from completed work. Each insight is a separate markdown file with YAML frontmatter.

## Structure

```
.context/learnings/
  INDEX.md              (this file)
  [category]/
    [descriptive-name].md
```

## Categories
- `clinical-development/`
- `literature-review/`
- `competitive-intelligence/`
- `regulatory-strategy/`
- `communication/`
- `decision/`
- `meeting/`
- `consulting/`
- `operations/`

## Insight Types
- `pattern` — Reusable approach that worked
- `template` — Structural template for reuse
- `preference` — User or stakeholder style preference
- `failure` — What didn't work and why
- `insight` — Domain knowledge worth remembering

## How to Search

By category:
```
Grep pattern="category: clinical-development" path=".context/learnings/"
```

By type:
```
Grep pattern="type: pattern" path=".context/learnings/"
```

By keyword:
```
Grep pattern="[keyword]" path=".context/learnings/"
```

## File Template

```markdown
---
type: [pattern|template|preference|failure|insight]
date: YYYY-MM-DD
category: [category]
task: Brief description of the original task
outcome: [success|partial|failure]
tags: [comma-separated keywords]
takeaway: One-sentence key learning
---

# Descriptive Title

## Context
[What task this came from]

## The Learning
[The actual insight — specific and actionable]

## When to Apply
[Specific situations where this is relevant]
```
