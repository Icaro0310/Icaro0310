# The `devin-*` ecosystem

Unofficial community tooling for [Devin](https://devin.ai) — Cognition AI's
coding agent. **Not affiliated with, endorsed by, or sponsored by Cognition.**

**[Português (BR)](#o-ecossistema-devin-)** · English

## The method

Every project adapts an existing, proven tool **plus** one Devin-specific
extra that must pass three tests:

1. does something the base tool *cannot* do
2. the extra disappears without Devin
3. explainable in one sentence

All tools are **read-only by default** on Devin's local stores and send
**zero telemetry**.

## Install

### Linux

```bash
# prerequisites: Python ≥ 3.10 + pipx
sudo apt install pipx python3-venv && pipx ensurepath        # Debian/Ubuntu

pipx install devin-doctor                                            # PyPI
pipx install "devin-backup @ git+https://github.com/Icaro0310/devin-backup.git"
```

Devin stores live under `~/.local/share/devin/cli/` (`sessions.db`) and
`~/.config/Devin/` (config, `acp-messages/`, `state.vscdb`).

### Windows

```powershell
# prerequisites: Python ≥ 3.10 + pipx
py -m pip install --user pipx && py -m pipx ensurepath

pipx install devin-doctor                                            # PyPI
pipx install "devin-backup @ git+https://github.com/Icaro0310/devin-backup.git"
```

Devin stores live under `%APPDATA%\devin\cli\` (`sessions.db`) and
`%APPDATA%\Devin\` (config, `acp-messages\`, `state.vscdb`).

### Both

`devin-bridge` is Node.js ≥ 20 — clone and `npm install -g .`
(works identically on Windows and Linux).

Most tools expect a **Devin Desktop** or Devin CLI install — they read its
local stores (`sessions.db`, `acp-messages/`, `state.vscdb`, `.devin/`).
Each repo's README documents the exact paths it uses and any `--data-dir`
override flags.

## Catalog

| Wave | Repo | What it does |
|---|---|---|
| **0 — Foundation** | [`devin-internals-spec`](https://github.com/Icaro0310/devin-internals-spec) | Documented internals of Devin's stores + schema-version detection + typed parsers/fixtures — the layer every tool builds on |
| | [`devin-redact`](https://github.com/Icaro0310/devin-redact) | Secret/PII redaction that understands tool-call semantics, in-place in SQLite, with a verify gate |
| **1 — Insight** | [`devin-doctor`](https://github.com/Icaro0310/devin-doctor) | `brew doctor` for a Devin install: stores, schema, locks, config, disk → concrete fixes |
| | [`devin-history`](https://github.com/Icaro0310/devin-history) | Export and audit session history → Markdown notes, JSON, CSV, Obsidian-ready |
| | [`devin-pm`](https://github.com/Icaro0310/devin-pm) | Project manager over sessions: per-repo rollups, milestones, status reports |
| **2 — Safety** | [`devin-backup`](https://github.com/Icaro0310/devin-backup) | Consistent snapshot/verify/restore/rotate of Devin stores, with schema-version manifests |
| | [`devin-metrics`](https://github.com/Icaro0310/devin-metrics) | Local-only usage metrics: cost, tokens, sessions per project/model/day |
| | [`devin-qa-pack`](https://github.com/Icaro0310/devin-qa-pack) | Verifies what a session *claims* it did against what tool calls *actually* did — PASS/PARTIAL/UNVERIFIED |
| **3 — Memory & Recall** | [`devin-evals`](https://github.com/Icaro0310/devin-evals) | Deterministic eval harness: replay recorded sessions against rubric graders |
| | [`devin-graph`](https://github.com/Icaro0310/devin-graph) | Queryable knowledge graph: sessions ↔ projects ↔ files touched ↔ tools used |
| | [`devin-search`](https://github.com/Icaro0310/devin-search) | FTS5 full-text search across all sessions — role-tagged, project-filtered |
| **4 — Agent plumbing** | [`devin-bridge`](https://github.com/Icaro0310/devin-bridge) | Policy-gated ACP client: isolated sessions per repo with allow/deny/ask rules |
| | [`devin-memory`](https://github.com/Icaro0310/devin-memory) | Anti-poisoning memory store: provenance, versioning, quarantine gate |
| **5 — Ops** | [`devin-janitor`](https://github.com/Icaro0310/devin-janitor) | Session lifecycle: export-then-delete pipeline, tiered classification, pluggable judge |
| | [`devin-orchestrator`](https://github.com/Icaro0310/devin-orchestrator) | Background-worker fan-out policy: deterministic planner, worker caps, no nesting |
| related | [`poordjaevin`](https://github.com/Icaro0310/poordjaevin) | Djævin — local-first calibrated decision layer: typed questions (Choice/Score/Noul) with calibrated confidence, no API key. The cheap local judge |
| related | [`devin-powerups`](https://github.com/Icaro0310/devin-powerups) | Maintainer hub: repo registry, scaffold template, weekly reports, ecosystem scout — fork it to run your own devin-* family |
| related | [`devin-office`](https://github.com/Icaro0310/devin-office) | Pixel-art office rendering live Devin activity (sessions, subagents, MCP calls) as animated characters — zero-dep hub + probe |
| related | [`qwenpaw-suite`](https://github.com/Icaro0310/qwenpaw-suite) | Small-VM LLM ops suite: Flask bridge (Ollama ↔ OpenAI-compatible API), healthcheck orchestrator, sync docs |

## The private runtime — the pattern, not the code

The repos above are the **tools**. They get *driven* by a private repo,
`personal-agent-system` — a personal agent runtime built on Devin Desktop.
The code stays private because it is full of my machine's paths, tokens and
credentials, but the **pattern** is public and replicable:

```
you ──► Devin Desktop (IDE / ACP sessions)
          │
          ├─ hooks: SessionEnd → export history → Obsidian notes
          │          PromptSubmit/Stop → lesson extractor → learned-* skills
          │
          ├─ MCP servers: persistent memory · vault · unified tools
          │
          ├─ Slack gateway: DM poll → mailbox → wakes a persistent
          │   Devin session → replies land back in Slack
          │
          ├─ heartbeat (cron): every 30 min wakes the session with a
          │   checklist; notifies only if something is urgent
          │
          └─ local judge: poordjaevin (public above) + a tiny model
              (qwen2.5 on a satellite VM via SSH tunnel) answers cheap
              yes/no/rate questions — zero cloud quota
```

Rebuilding your own ≈ hooks + one MCP memory store + one comms channel +
one scheduled checklist. Every reusable piece is already in the public
catalog above.

---

*Devin is a trademark of Cognition AI. This is a community project.*

---

## O ecossistema `devin-*`

Ferramentas de comunidade para o [Devin](https://devin.ai), agente de código
da Cognition AI. **Sem afiliação com a Cognition.**

Cada projeto adapta uma ferramenta existente **mais** um extra específico do
Devin. Instalação em **Windows e Linux**: Python ≥ 3.10 + `pipx` (ver a
secção *Install* acima); cada repo tem README próprio em EN/PT-BR com
instruções completas para os dois sistemas.

O runtime pessoal (`personal-agent-system`) não é publicado — contém
credenciais e paths da minha máquina — mas o **padrão** está documentado em
*"The private runtime"* acima: hooks que exportam sessões e extraem lições,
memória MCP, gateway Slack→mailbox, heartbeat agendado e um juiz local
barato numa VM satélite. Cada peça reutilizável já está no catálogo público.
