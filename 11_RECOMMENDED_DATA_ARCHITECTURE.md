# Recommended Data Architecture

## Canonical entity model

Use a normalized graph rather than a single flat table.

### Core nodes

- `Entity`: stable ID, canonical name, aliases, type, publisher, URLs, description, verification state.
- `Source`: URL, publisher, type, authority, access method, terms, cadence.
- `Claim`: normalized assertion, value, evidence location, observed_at, verification status.
- `Price`: provider, product, billing unit, amount, currency, tier, quota, restrictions, source, observed_at.
- `Installation`: target environment, command, prerequisites, environment variables, permissions, source.
- `BenchmarkResult`: benchmark, version, model/model_variant/deployment, score, metric, sample/methodology reference, observed_at.
- `Relationship`: subject ID, predicate, object ID, evidence, observed_at.

## Key relationships

- `Provider OFFERS Deployment`
- `Deployment SERVES ModelVariant`
- `ModelVariant INSTANCE_OF Model`
- `Application USES ModelVariant`
- `Application INTEGRATES_WITH Provider`
- `Skill PART_OF Plugin`
- `Plugin PROVIDES Skill`
- `Plugin INCLUDES McpServer`
- `McpServer EXPOSES McpTool`
- `Benchmark PRODUCES BenchmarkResult`
- `Leaderboard AGGREGATES BenchmarkResult`
- `Repository IS_SOURCE_FOR Entity`

## Provenance model

Every user-visible factual field should resolve to one or more claims:

```json
{
  "field": "free_access.daily_request_limit",
  "value": 1000,
  "condition": "account has purchased at least $10 of credits",
  "source_url": "https://openrouter.ai/pricing",
  "observed_at": "2026-10-23",
  "verification": "official",
  "confidence": "high"
}
```

## Refresh strategy

| Data domain | Method | Initial cadence | Failure policy |
|---|---|---|---|
| Hugging Face models/datasets | Hub API / OpenAPI endpoints | Daily incremental | Retry with backoff; mark stale after 7 days |
| OpenRouter models and pricing | Models API plus pricing/docs pages | Daily | Do not display stale free quotas |
| MCP servers | Official Registry REST API | Daily or continuous | Preserve prior version and flag registry preview risk |
| Claude/OpenCode extensions | Official docs, GitHub, package registries | Weekly | Require repository and manifest validation |
| Benchmarks | Methodology and result pages | On version change | Retain historical benchmark versions |
| YouTube | Search, channel, and caption/transcript inspection | Weekly for fast-moving tools | Mark video evidence time-bound |

## Search requirements

Implement in layers:

1. **Canonical resolution:** exact ID, slug, alias, package name, model ID, repository path.
2. **Lexical search:** BM25-style matching over names, aliases, descriptions, categories, and installation text.
3. **Fuzzy matching:** handles misspellings and near-name collisions, with disambiguation cards.
4. **Structured filters:** entity type, category, license, price, free classification, platform, modality, context, maintenance, and benchmark.
5. **Semantic retrieval:** embed descriptions and use cases for natural-language queries; use it to expand—not replace—structured filters.
6. **Intent routing:** classify queries into entity lookup, category search, comparison, how-to, alternatives, free-tier discovery, and leaderboard request.
7. **Result typing:** return the appropriate destination: entity page, comparison, directory, guide, or leaderboard.

Do not make an LLM call mandatory for every query. Use deterministic resolution and filters first; reserve generation for answer synthesis, comparison narratives, and ambiguous-query clarification.
