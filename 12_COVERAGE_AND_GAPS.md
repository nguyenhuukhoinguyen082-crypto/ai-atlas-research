# Coverage and Gaps

## Categories researched at baseline depth

- MCP registries and server metadata
- Model aggregators, pricing, and free-access mechanics
- Claude Code skills, plugins, marketplaces, and extension model
- OpenCode plugin/skill extension surface
- Model/dataset hosting and Hub APIs
- Composite model benchmark methodology
- Search intent and data architecture

## Sources searched

- Official MCP Registry documentation, FAQ, terms, API reference, and GitHub repository. [web:1][web:2][web:3][web:4][web:5][web:14]
- OpenRouter pricing, FAQ, free-router documentation, free-variant documentation, Discover page, and cookbook. [web:6][web:7][web:8][web:9][web:10][web:11][web:12]
- Claude Code plugin, skills, installation, marketplace, and Anthropic skills documentation. [web:16][web:17][web:18][web:19][web:20][web:21][web:22]
- OpenCode plugin documentation. [web:30]
- Artificial Analysis methodology, Index page, v4.2 announcement, and related social post. [web:31][web:32][web:33][web:44]
- Hugging Face Hub documentation and API documentation. [web:34][web:35][web:36][web:37][web:40]

## Known coverage gaps

- No complete inventory of individual MCP servers, skills, plugins, IDE extensions, or coding agents.
- No comprehensive model catalog: families, versions, licenses, context limits, deprecations, and modality coverage remain incomplete.
- No complete provider matrix: regions, throughput, SLAs, SDKs, batch inference, and rate limits.
- No YouTube transcript/timestamp dataset.
- No direct GitHub repository crawl for releases, dependencies, licenses, security advisories, and maintenance signals.
- No full benchmark ingestion beyond Artificial Analysis methodology.
- No legal review of redistribution, attribution, database rights, or API terms.

## High-value next tasks

1. **MCP ingestion sprint:** Pull all public servers from `https://registry.modelcontextprotocol.io/v0/servers`, normalize `server.json`, and resolve repositories/packages/licenses.
2. **OpenRouter catalog snapshot:** Ingest `/api/v1/models`, preserve pricing, context, modality, provider, and `:free` fields with timestamps.
3. **Claude ecosystem crawl:** Enumerate official and major community marketplaces, then validate each plugin manifest and component.
4. **OpenCode ecosystem crawl:** Identify canonical repository, releases, plugin format, skill format, and package distribution.
5. **Provider pricing crawl:** Build official-source adapters for major first-party APIs and inference providers.
6. **Benchmark ingestion:** Add SWE-style coding, terminal/agent, long-context, multimodal, and human-preference evaluations with methodology records.
7. **YouTube evidence sprint:** Search official channels, maintainer channels, and technical educators; extract IDs, dates, durations, captions, timestamps, and corroboration status.
8. **Security and permissions enrichment:** Capture required scopes, credentials, filesystem/network access, and known advisories for executable extensions.

## Completion statement

This deliverable is an **initial verified research baseline**, not a completed ecosystem database. It provides enough verified source structure, taxonomy, entity examples, pricing rules, benchmark methodology, and search architecture for the auditor and implementation agent to begin scalable ingestion without fabricating coverage.
