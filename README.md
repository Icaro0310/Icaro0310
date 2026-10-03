<div align="center">

<img src="assets/banner.svg" alt="devin-* — community tooling for Devin" width="100%"/>

[![MIT](https://img.shields.io/badge/license-MIT-1d1d1f?style=flat-square)](https://github.com/Icaro0310/devin-powerups/blob/main/LICENSE)
[![20 tools](https://img.shields.io/badge/tools-20-0071e3?style=flat-square)](#catalog)
[![Windows · Linux](https://img.shields.io/badge/windows_%C2%B7_linux-supported-86868b?style=flat-square)](#install)
[![zero telemetry](https://img.shields.io/badge/telemetry-zero-34c759?style=flat-square)](#runs-on-devin-alone)

**Twenty local-first tools that turn Devin's own session data into backups,
search, metrics, memory and QA — no cloud, no telemetry, nothing to sign up for.**

Unofficial community project. Not affiliated with, endorsed by, or sponsored by Cognition AI.

</div>

<br/>

## The method

Every project adapts an existing, proven tool **plus** one Devin-specific extra
that must pass three tests:

1. does something the base tool *cannot* do
2. the extra disappears without Devin
3. explainable in one sentence

All tools are **read-only by default** on Devin's local stores and send
**zero telemetry**.

## Install

**Linux**

```bash
sudo apt install pipx python3-venv && pipx ensurepath     # Debian/Ubuntu
pipx install "devin-doctor @ git+https://github.com/Icaro0310/devin-doctor.git"
```

**Windows**

```powershell
py -m pip install --user pipx && py -m pipx ensurepath
pipx install "devin-doctor @ git+https://github.com/Icaro0310/devin-doctor.git"
```

Requires Python ≥ 3.10. Devin stores live at `~/.local/share/devin/cli/` +
`~/.config/Devin/` (Linux) or `%APPDATA%\devin\` (Windows). `devin-bridge` is
Node.js ≥ 20 — clone and `npm install -g .`. Each repo documents the exact
paths it uses and its `--data-dir` override flags.

## Catalog

| Wave | Repo | What it does |
|---|---|---|
| **Foundation** | [`devin-internals-spec`](https://github.com/Icaro0310/devin-internals-spec) | Devin's store internals, documented — schema detection, typed parsers, fixtures |
| | [`devin-redact`](https://github.com/Icaro0310/devin-redact) | Secret/PII redaction that understands tool-call semantics, in-place in SQLite |
| **Insight** | [`devin-doctor`](https://github.com/Icaro0310/devin-doctor) | `brew doctor` for a Devin install — stores, locks, config → concrete fixes |
| | [`devin-history`](https://github.com/Icaro0310/devin-history) | Session history → Markdown, JSON, CSV, Obsidian-ready |
| | [`devin-pm`](https://github.com/Icaro0310/devin-pm) | Project manager over sessions — rollups, milestones, status reports |
| **Safety** | [`devin-backup`](https://github.com/Icaro0310/devin-backup) | Snapshot, verify, restore, rotate — with schema-version manifests |
| | [`devin-metrics`](https://github.com/Icaro0310/devin-metrics) | Cost, tokens, sessions per project/model/day — local only |
| | [`devin-qa-pack`](https://github.com/Icaro0310/devin-qa-pack) | Claims vs. reality — PASS / PARTIAL / UNVERIFIED |
| **Memory** | [`devin-evals`](https://github.com/Icaro0310/devin-evals) | Replay recorded sessions against rubric graders, deterministically |
| | [`devin-graph`](https://github.com/Icaro0310/devin-graph) | Knowledge graph — sessions ↔ projects ↔ files ↔ tools |
| | [`devin-search`](https://github.com/Icaro0310/devin-search) | FTS5 full-text search across every session |
| **Agents** | [`devin-bridge`](https://github.com/Icaro0310/devin-bridge) | Policy-gated ACP client — allow / deny / ask rules |
| | [`devin-memory`](https://github.com/Icaro0310/devin-memory) | Anti-poisoning memory — provenance, versioning, quarantine |
| **Ops** | [`devin-janitor`](https://github.com/Icaro0310/devin-janitor) | Session lifecycle — export-then-delete, tiered, dry-run first |
| | [`devin-orchestrator`](https://github.com/Icaro0310/devin-orchestrator) | Background-worker fan-out — deterministic planner, caps, no nesting |
| **Related** | [`poordjaevin`](https://github.com/Icaro0310/poordjaevin) | Djævin — calibrated decision layer; scores through Devin's own model via ACP |
| | [`devin-powerups`](https://github.com/Icaro0310/devin-powerups) | Maintainer hub — registry, scaffolder, weekly reports; fork it for your own family |
| | [`devin-office`](https://github.com/Icaro0310/devin-office) | Pixel-art office rendering live Devin activity as animated characters |
| | [`qwenpaw-suite`](https://github.com/Icaro0310/qwenpaw-suite) | Optional add-on — Ollama ↔ OpenAI bridge for operators who run their own model server |

## Runs on Devin alone?

Yes. Every tool reads Devin's own local stores and needs **no VM, no tunnel,
no model server, no Slack, no Obsidian**. On a locked-down corporate machine
where none of those can be installed, the whole catalog still works.

- `devin-bridge` needs Node.js ≥ 20 — it is an ACP client for the Devin CLI
  itself, so its dependency is still just Devin.
- `poordjaevin` defaults to scoring through Devin's own model via ACP — no
  model download, no extra key. `POORDJAEVIN_BACKEND=nli` switches to a fully
  offline local model (~400 MB, one download).
- `devin-powerups`' scheduled workflows (weekly report, email) are optional —
  the registry and scaffolder run locally, and reports can be written to disk
  from cron/Task Scheduler with no email at all.
- `qwenpaw-suite` is for operators who already run their own model server.
  Skip it freely.

Each README has a *Works with Devin alone* section with the exact
Windows/Linux paths it touches and honest caveats — `devin-janitor` deletes
only under `--apply`; `devin-history` exports may contain prompts.

## The private runtime — the pattern, not the code

The repos above are the **tools**. They get *driven* by a private repo,
`personal-agent-system` — a personal agent runtime built on Devin Desktop.
The code stays private (machine paths, tokens, credentials), but the
**pattern** is public and replicable:

```
you ──► Devin Desktop (IDE / ACP sessions)
          │
          ├─ hooks: SessionEnd → export history → notes
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
          └─ local judge: poordjaevin (public above) answers cheap
              yes/no/rate questions through Devin's own model
```

Rebuilding your own ≈ hooks + one MCP memory store + one comms channel +
one scheduled checklist. Every reusable piece is already in the public
catalog above.

<br/>

<details>
<summary><b>Português (BR)</b></summary>

<br/>

Ferramentas de comunidade para o [Devin](https://devin.ai), agente de código
da Cognition AI. **Sem afiliação com a Cognition.**

Vinte utilitários *local-first* que transformam os dados de sessão do próprio
Devin em backups, busca, métricas, memória e QA — sem cloud, sem telemetria.
Funcionam **só com o Devin**: sem VM, sem túnel, sem servidor de modelos,
sem Slack, sem Obsidian.

Instalação em **Windows e Linux**: Python ≥ 3.10 + `pipx` (ver *Install*
acima). Cada repo tem README em EN/PT-BR com instruções completas e uma
secção *Funciona só com o Devin* com os paths exatos de cada sistema.

O runtime pessoal (`personal-agent-system`) não é publicado — contém
credenciais e paths da minha máquina — mas o **padrão** está documentado em
*The private runtime* acima. Cada peça reutilizável já está no catálogo.

</details>

<br/>

---

<div align="center">

<sub>Devin is a trademark of Cognition AI. This is a community project.</sub>

</div>
