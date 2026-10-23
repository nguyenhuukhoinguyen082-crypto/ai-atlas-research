# Research Executive Summary

**Research date:** 2026-10-23  
**Scope:** Initial, evidence-grounded baseline for an AI-ecosystem search, directory, comparison, and leaderboard product. This is **not** an exhaustive census of the AI ecosystem; it establishes verified source foundations, entity distinctions, data contracts, and a prioritized research backlog.

## Major findings

1. **MCP has an official, machine-readable registry.** The official MCP Registry at `https://registry.modelcontextprotocol.io` provides a REST API, standardized `server.json` metadata, installation/configuration fields, namespace management, and an OpenAPI specification. It is in preview and may have breaking changes or data resets. [web:1][web:2][web:3][web:5]

2. **OpenRouter is a high-value structured source for models, pricing, and free access.** Its public model API and documentation expose model IDs, per-million-token pricing, context lengths, endpoints, `:free` variants, and the `openrouter/free` router. Free-model availability and rate limits change frequently and must be refreshed from the API rather than cached as static facts. [web:6][web:7][web:8][web:9][web:10][web:11][web:12]

3. **“Free” requires multi-dimensional classification.** OpenRouter free models are zero-cost per token but rate-limited: 20 requests/minute and 50 requests/day by default, rising to 1,000/day after a user has purchased at least $10 of credits; failed requests count toward the daily cap. [web:6][web:7] Free variants can also have different availability, context, and provider data policies from paid equivalents. [web:9][web:15]

4. **Claude Code has a formal extension model.** A **skill** is a `SKILL.md` instruction/workflow package; a **plugin** bundles skills, agents, hooks, and MCP servers behind `.claude-plugin/plugin.json`; marketplaces are catalogs, not hosted stores. These distinctions should be preserved as separate entity types. [web:16][web:17][web:18][web:19][web:20]

5. **OpenCode exposes a plugin/skill extension surface.** Its plugin documentation describes programmatic modification of OpenCode behavior and skill listing/transformation through a plugin context API. OpenCode-specific plugin records require direct inspection of repository manifests and current documentation. [web:30]

6. **Benchmarks need methodology-level normalization, not score merging.** Artificial Analysis Intelligence Index v4.3.2 aggregates ten evaluations and weights agents, coding, general capability, and scientific reasoning; its methodology page documents standardized conditions, judge use, private held-out components, and task-specific metrics. [web:31][web:32][web:33][web:44]

7. **Hugging Face is the broadest initial model/dataset discovery backbone.** The Hub hosts more than 2M models, 1.5M datasets, and 1.5M Spaces, with open Hub API endpoints, Python/JS clients, webhooks, and an OpenAPI specification. API access is subject to Hub-wide rate limits. [web:34][web:36][web:37]

## Product opportunities

- **Canonical entity resolution:** Distinguish models, model variants, providers, deployments, applications, skills, plugins, MCP servers, tools, benchmarks, and datasets.
- **Free-access explorer:** Rank by usable quota, setup burden, model quality, reliability, data-handling policy, and commercial-use terms—not merely a Boolean “free” flag.
- **MCP/skill/plugin directory:** Ingest the official MCP Registry API and Claude/OpenCode ecosystems while retaining security, permissions, maintenance, and installation metadata.
- **Transparent leaderboards:** Present benchmark-specific scores with version, date, sample/methodology, license, and comparability warnings; never combine incomparable scales into one universal score.
- **Installation intelligence:** Extract exact commands, environment variables, package names, runtime requirements, and permission implications from official docs and registry metadata.

## Important risks

- **Freshness risk:** Model catalogs, free quotas, extension APIs, and benchmark versions change quickly. OpenRouter explicitly notes that free-model availability changes frequently. [web:8][web:10][web:11]
- **Registry instability:** The MCP Registry is preview software and warns of possible breaking changes or data resets. [web:2][web:3]
- **Free-tier ambiguity:** Public-source models are not necessarily free to run; hosted free endpoints may impose rate limits, approval requirements, or data-training policies. [web:6][web:9][web:15]
- **Benchmark gaming and comparability:** Composite leaderboards can obscure task-specific differences; Artificial Analysis uses private held-out evaluations partly to reduce gaming, but users still need benchmark-level transparency. [web:32][web:33][web:44]
- **Security risk for extensions:** Skills, plugins, hooks, and MCP servers can execute instructions, access credentials, or connect to external systems. Installation metadata must be paired with permission, provenance, and maintenance signals.

## Coverage limitations

This baseline verifies foundational sources and taxonomy but does **not** yet provide complete coverage of:
- All model families, versions, licenses, context limits, and deprecations.
- All first-party and third-party inference providers, regional availability, SLAs, and rate limits.
- The full MCP server ecosystem, Claude marketplace, OpenCode plugin ecosystem, IDE extensions, and agent frameworks.
- YouTube evidence at transcript/timestamp depth.
- Independent benchmark ingestion beyond the initial methodology review.

## Recommended initial scope

Build the first production slice around five high-confidence, structured domains:

1. Models and model variants via Hugging Face and OpenRouter.
2. Providers, pricing, and free access via official provider pricing pages and OpenRouter.
3. MCP servers via the official MCP Registry API.
4. Claude Code skills/plugins and OpenCode plugins via official documentation and canonical repositories.
5. Benchmarks and rankings via methodology-first ingestion of Artificial Analysis and selected public benchmarks.

## Handoff instruction

The auditor should treat every record as **partially verified** unless it has an official primary source, an observation date, and no unresolved conflict. The implementation agent should ingest `03_ENTITY_CATALOG.jsonl` as the canonical entity seed, use `04_SOURCE_REGISTRY.csv` for ingestion priorities, and implement refresh jobs before exposing time-sensitive pricing, quota, availability, or leaderboard fields.
