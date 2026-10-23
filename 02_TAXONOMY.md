# AI Ecosystem Taxonomy

## Entity-type distinctions

| Entity type | Definition | Example pattern | Must not be conflated with |
|---|---|---|---|
| `model` | A trained AI model or model family/variant | A coding LLM, image generator, embedding model | A provider or hosted endpoint |
| `model_variant` | A specific version, quantization, context variant, or free variant | `model-id:free` | The base model |
| `provider` | An organization offering API access, hosting, or inference | First-party model API, inference gateway | A model |
| `deployment` | A concrete accessible endpoint/configuration | A provider-hosted model endpoint | The abstract model |
| `tool` | Developer software, CLI, SDK, library, or framework | Agent framework, vector database | An end-user application |
| `application` | User-facing web, desktop, mobile, browser, or self-hosted product | AI chat app, image editor | A model or API |
| `skill` | Reusable instructions/knowledge/workflow package, often `SKILL.md` | Claude Code skill | An MCP server or plugin |
| `plugin` | Installable package bundling extensions | Claude Code plugin | A single skill |
| `mcp_server` | A server implementing Model Context Protocol | Browser-automation MCP server | An individual tool exposed by that server |
| `mcp_tool` | An individual capability exposed through an MCP server | A browser-click tool | The server |
| `benchmark` | A defined evaluation with tasks, scoring, and methodology | Coding or agent benchmark | A leaderboard |
| `leaderboard` | A ranked presentation of evaluation results | Composite intelligence index | The underlying benchmark |
| `dataset` | Curated data for training, evaluation, or retrieval | Evaluation dataset | A benchmark |
| `repository` | Source-code/project canonical home | GitHub repository | The product itself |

## Category hierarchy

### A. Models and model ecosystems
- General-purpose LLMs
- Reasoning and mathematics models
- Coding and agentic-coding models
- Open-weight and locally runnable models
- Small, distilled, and edge models
- Vision and multimodal models
- Image generation and editing models
- Video generation models
- Speech, transcription, audio, and music models
- Embeddings and rerankers
- OCR and document intelligence
- Retrieval and research models
- Scientific and domain-specific models

### B. Providers and infrastructure
- First-party model APIs
- Third-party inference providers
- Aggregators and gateways
- Cloud platforms
- Local inference runtimes
- GPU/cloud compute
- Serverless inference
- Dedicated endpoints
- Batch inference
- Model deployment and serving

### C. Pricing and free access
- Permanently free hosted offering
- Limited free tier
- Promotional credits
- Time-limited trial
- Free application with restricted capabilities
- Open-weight model requiring local compute
- Self-hosted software with infrastructure cost
- Paid product with free trial
- Free tier requiring payment verification
- Approval- or region-restricted access

### D. Coding agents and vibe-coding tools
- Terminal coding agents
- IDE assistants
- AI-native editors
- Autonomous software-engineering agents
- Browser-based app builders
- No-code/low-code generators
- Repository agents
- Code-review assistants
- Testing and debugging agents
- Deployment assistants

### E. Skills, plugins, extensions, and MCP
- Agent skills
- Claude Code skills
- Claude Code plugins
- Claude marketplaces
- OpenCode plugins
- OpenCode skills
- Cursor rules and extensions
- IDE extensions
- MCP servers
- MCP tools
- Tool-calling frameworks
- CLI plugins
- Workflow templates
- Automation connectors
- Browser/computer-use integrations

### F. General AI applications
- Chat assistants
- AI search engines
- Research assistants
- Writing tools
- Design tools
- Meeting assistants
- Productivity and office tools
- Browser agents
- Desktop assistants
- Mobile apps
- Workflow builders
- Image/video editors
- AI-native creative software

### G. Frameworks, SDKs, and development infrastructure
- Agent frameworks
- Orchestration libraries
- SDKs
- Vector databases
- RAG tools
- Observability
- Evaluation frameworks
- Prompt tools
- Model serving
- Training and fine-tuning
- Datasets and synthetic data
- AI security tooling

### H. Research and evaluation
- Independent benchmarks
- Human-preference evaluations
- Coding evaluations
- Reasoning evaluations
- Multimodal benchmarks
- Tool-use/agent benchmarks
- Leaderboards
- Latency/throughput measurements
- Cost-efficiency evaluations
- Reliability/task-completion evaluations

## Proposed relationships

- `model` **has variants** `model_variant`
- `provider` **offers** `deployment`
- `deployment` **serves** `model_variant`
- `application` **uses** `model_variant` and/or `provider`
- `skill` **may be packaged in** `plugin`
- `plugin` **may bundle** `skill`, `mcp_server`, `agent`, `hook`
- `mcp_server` **exposes** `mcp_tool`
- `benchmark` **produces** `benchmark_result`
- `leaderboard` **aggregates** `benchmark_result`
- `dataset` **may be used by** `benchmark`
- `repository` **is canonical source for** any software entity
