# Connectors

CoworkPowers research agents are wired to use specific MCP tools. The research skill runs a Phase 0 discovery step to detect which tools are available in the current environment.

## Connected MCP Tools

| Category | MCP Tools | Used By |
|----------|-----------|---------|
| Literature | `mcp__plugin_bio-research_pubmed__search_articles`, `get_article_metadata`, `find_related_articles`, `get_full_text_article` | literature-scout |
| Preprints | `mcp__plugin_bio-research_biorxiv__search_preprints`, `get_preprint`, `search_published_preprints` | literature-scout |
| Clinical Trials | `mcp__claude_ai_Clinical_Trials__search_trials`, `get_trial_details`, `search_by_sponsor`, `search_investigators`, `analyze_endpoints`, `search_by_eligibility` | clinical-landscape |
| Compounds | `mcp__plugin_bio-research_chembl__compound_search`, `drug_search`, `get_bioactivity`, `get_mechanism`, `target_search`, `get_admet` | competitive-intel |
| Targets | `mcp__plugin_bio-research_ot__search_entities`, `query_open_targets_graphql` | competitive-intel |
| Web | `WebSearch`, `WebFetch` | all agents |
| Files | `Read`, `Write`, `Edit`, `Grep`, `Glob` | all agents |
| Document Generation | `docx` skill, `pptx` skill | executive-writer, analyst, due-diligence-analyst, market-access-strategist, proposal-writer |

## Adding New Connectors

When new MCP tools become available (e.g., ScholarGateway, Slack, email, calendar), agents will discover them in Phase 0 and use them opportunistically. No configuration changes needed — the research skill's tool discovery handles it automatically.

## Optional Future Connectors

| Category | Example MCPs | Would Enhance |
|----------|-------------|---------------|
| Email | Gmail, Microsoft 365 | context-gatherer, stakeholder-mapper |
| Calendar | Google Calendar, Microsoft 365 | constraint-analyzer |
| Meeting Notes | Granola, Otter | precedent-researcher |
| CRM | Salesforce, HubSpot | stakeholder-mapper, competitive-intel |
| Knowledge Base | Notion, Confluence | context-gatherer, precedent-researcher |
| Chat | Slack, Teams | stakeholder-mapper |
| Scholar | ScholarGateway | literature-scout |
