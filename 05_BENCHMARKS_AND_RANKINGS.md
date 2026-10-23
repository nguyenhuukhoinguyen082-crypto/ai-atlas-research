# Benchmarks and Rankings

## Principles

- Never merge scores from benchmarks with different tasks, prompts, judges, sampling, or scales.
- Store every result with benchmark name, version, observation date, model version, provider/deployment, and source URL.
- Separate **measured benchmark result**, **provider claim**, **community opinion**, and **editorial recommendation**.
- A leaderboard is a presentation layer; the benchmark and its methodology are the evidence layer.

## Verified benchmark source

### Artificial Analysis Intelligence Index

- **Publisher:** Artificial Analysis. [web:31][web:32]
- **What it measures:** A composite of evaluations across agents, coding, general capability, and scientific reasoning. [web:31][web:32]
- **Version researched:** v4.3.2. [web:32]
- **Components:** AA-Briefcase v1.1, GDPval-AA v2.1, AutomationBench-AA, Terminal-Bench 4.0, SciCode, Humanity’s Last Exam, GDP.pdf, CritPt, AA-Omniscience, and AA-LCR v1.1. [web:32]
- **Weighting:** Agents 30%, Coding 20%, General 30%, Scientific Reasoning 20%. [web:31][web:44]
- **Methodology:** Standardized prompting and evaluation conditions, zero-shot instruction prompting, disclosed prompts/criteria/limitations, and consistent judge use for a given rubric. [web:31]
- **Anti-gaming design:** Private held-out test sets are part of the weighting; v4.2 stated that held-out data accounted for 40% of Index weighting, while a later Artificial Analysis post stated 45% for v4.3. [web:33][web:44]
- **Limitations:** Primarily text-based and English-language; image, speech, and multilingual performance are evaluated separately. [web:31]

**Conflict to preserve:** The v4.2 announcement says 40% private held-out weighting; the v4.3 social post says 45%. Treat this as version-specific rather than contradictory: record the exact Index version with each weight. [web:33][web:44]

## Proposed ranking framework

### Model leaderboards

Use separate boards, never one universal score:

| Board | Primary question | Candidate metrics | Required caveats |
|---|---|---|---|
| Coding | Which model performs best on coding tasks? | Benchmark-specific coding score, context support, cost per task, latency | Task type and scaffold matter |
| Agentic coding | Which model completes real repository/engineering tasks? | Terminal/task success, tool-use reliability, cost, repeat consistency | Agent scaffold can dominate model choice |
| Long context | Which model handles long inputs reliably? | Context limit, retrieval/synthesis benchmark, price per long task | Context limit is not comprehension quality |
| Free access | Which free option is most usable? | Usable daily quota, model quality, setup burden, reliability, data policy | “Free” is not production-ready by default |
| Local models | Which open-weight model fits local hardware? | Parameters, quantization, VRAM/RAM need, tokens/sec, license | Hardware and runtime strongly affect results |

### Tool, plugin, and MCP leaderboards

For resources without standardized benchmarks, use a transparent rubric:

- Task fit: 30%
- Documentation and installation clarity: 15%
- Maintenance and release activity: 15%
- Compatibility and integration breadth: 15%
- Security/permission transparency: 15%
- Usability and community evidence: 10%

Display subscores and evidence links. Do **not** infer security from popularity, absence of advisories, or star count.

## Refresh cadence

- Model catalogs and free-model availability: daily to weekly.
- Provider pricing and quotas: weekly, plus event-driven checks.
- MCP Registry: continuous or daily API sync.
- Claude/OpenCode extension ecosystems: weekly repository/docs crawl.
- Benchmarks: on version change; retain historical versions.
