# Unverified and Conflicting Claims

## Conflicts

### Artificial Analysis private held-out weighting

- **Claim A:** Intelligence Index v4.2 uses 40% private held-out test sets.  
  **Source:** https://artificialanalysis.ai/articles/artificial-analysis-intelligence-index-v4-2, published 2026-09-04. [web:33]
- **Claim B:** Intelligence Index v4.3 uses 45% private-question/answer weighting.  
  **Source:** Artificial Analysis social post dated 2026-09-07. [web:44]
- **Resolution:** Not a true contradiction if versions differ. Store `index_version`, `private_holdout_weight`, and observation date together. Do not display a single timeless percentage.

### OpenRouter free-model count

- **Claim A:** OpenRouter pricing page says “25+ free models.” [web:6]
- **Claim B:** A third-party analysis reports that the API listed 19 free text models on 2026-10-05. [web:15]
- **Resolution:** Treat the official pricing page as authoritative for its marketing claim, but use the live `/api/v1/models` response as authoritative for the current machine-readable catalog. Record both count definitions and observation timestamps. [web:6][web:7][web:15]

## Unverified or incomplete

| Item | Missing evidence | Recommended resolution |
|---|---|---|
| OpenCode canonical repository, license, installation command, and plugin marketplace | Not captured in the initial source pass | Crawl `opencode.ai` repository links, GitHub organization, releases, package manifests, and docs |
| Exact Hugging Face rate-limit thresholds | Documentation states rate limits exist but does not provide the threshold in the reviewed page | Query official rate-limit documentation and account settings; do not infer limits |
| MCP Registry exact rate limits and redistribution terms | Not captured in the reviewed pages | Inspect API terms, OpenAPI spec, and GitHub repository |
| Claude Code current pricing and full bundled-skill inventory | Not captured in the extension-focused source pass | Crawl Anthropic pricing and Claude Code release notes |
| YouTube video-level evidence | No transcript/timestamp-level records collected yet | Perform dedicated YouTube searches, capture IDs/dates/durations, and corroborate claims with official documentation |
| Individual MCP servers, skills, and plugins beyond foundational ecosystem records | Not yet enumerated | Ingest MCP Registry API, Claude marketplaces, OpenCode repositories, and package registries |
| Provider SLAs, regional availability, and throughput | Not researched in this pass | Use official status pages, pricing/regions pages, and documented limits |

## Data-quality rules for the next agent

1. Never convert “source code is public” into “free to use.”
2. Never convert a model’s context limit into long-context quality.
3. Never treat an MCP server listing as a security review.
4. Never persist a free quota without its reset interval, eligibility rule, and observation date.
5. Never merge benchmark versions or benchmark component scores.
