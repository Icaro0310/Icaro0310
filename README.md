<div align="center">

<img src="assets/banner.svg" alt="Ícaro Galvão — devin-* ecosystem" width="100%"/>

<h1><a href="https://www.linkedin.com/in/ícaro-galvão-do-nascimento-663601280/">Ícaro Galvão</a></h1>

**Senior QA Engineer · Developer Tooling · AI Agents · Open Source**

I build tools that make AI coding agents easier to inspect, evaluate and trust.
Currently building the `devin-*` ecosystem — twenty local-first tools that turn
Devin's own session data into backups, search, metrics, memory and QA.

[Website](https://icaro0310.github.io) · [LinkedIn](https://www.linkedin.com/in/ícaro-galvão-do-nascimento-663601280/) · [Catalog](#catalog)

[![MIT](https://img.shields.io/badge/license-MIT-1d1d1f?style=flat-square)](https://github.com/Icaro0310/devin-powerups/blob/main/LICENSE)
[![local-first](https://img.shields.io/badge/local--first-zero%20telemetry-0071e3?style=flat-square)](#runs-on-devin-alone)

</div>

## Selected work

Five projects that tell one story — **understand → verify → measure → control → judge**:

| | | |
|---|---|---|
| [`devin-internals-spec`](https://github.com/Icaro0310/devin-internals-spec) | **Understand the system** | Devin's local stores, documented — schema detection, typed parsers, contract boundary against drift |
| [`devin-qa-pack`](https://github.com/Icaro0310/devin-qa-pack) | **Verify the agent** | Whether a session's claims are backed by actual tool-call evidence — PASS / PARTIAL / UNVERIFIED |
| [`devin-evals`](https://github.com/Icaro0310/devin-evals) | **Measure the agent** | Replay recorded sessions against deterministic rubrics; agent quality as a regression signal |
| [`devin-bridge`](https://github.com/Icaro0310/devin-bridge) | **Control the agent** | Drive Devin through ACP with explicit allow/deny/ask policies — enforcement in code, not instructions |
| [`poordjaevin`](https://github.com/Icaro0310/poordjaevin) | **Judge the decision** | Calibrated decision layer on Devin's own model via ACP — measurable confidence (ECE 0.170 → 0.071) |

<div align="center">

<a href="https://icaro0310.github.io/demos/devin-office.html"><img src="assets/office-demo.gif" alt="devin-office — live Devin sessions, subagents and tools as an animated circuit board" width="80%"/></a>

<sub>**devin-office** — live sessions, subagents and tools as an animated circuit board · [open the live demo](https://icaro0310.github.io/demos/devin-office.html)</sub>

</div>

<details>
<summary><b>Full catalog — 20 tools</b></summary>

<br/>

| Wave | Repo | What it does |
|---|---|---|
| **Foundation** | [`devin-internals-spec`](https://github.com/Icaro0310/devin-internals-spec) | Store internals documented — schema detection, typed parsers |
| | [`devin-redact`](https://github.com/Icaro0310/devin-redact) | Secret/PII redaction that understands tool-call semantics |
| **Insight** | [`devin-doctor`](https://github.com/Icaro0310/devin-doctor) | Diagnose a Devin install → concrete fixes |
| | [`devin-history`](https://github.com/Icaro0310/devin-history) | Sessions → Markdown, JSON, CSV |
| | [`devin-pm`](https://github.com/Icaro0310/devin-pm) | Project manager over sessions — rollups, milestones |
| **Safety** | [`devin-backup`](https://github.com/Icaro0310/devin-backup) | Snapshot, verify, restore — schema-version manifests |
| | [`devin-metrics`](https://github.com/Icaro0310/devin-metrics) | Cost, tokens, sessions per project/model/day |
| | [`devin-qa-pack`](https://github.com/Icaro0310/devin-qa-pack) | Claims vs. reality — PASS / PARTIAL / UNVERIFIED |
| **Memory** | [`devin-evals`](https://github.com/Icaro0310/devin-evals) | Replay sessions against rubric graders |
| | [`devin-graph`](https://github.com/Icaro0310/devin-graph) | Sessions ↔ projects ↔ files ↔ tools |
| | [`devin-search`](https://github.com/Icaro0310/devin-search) | FTS5 full-text search across sessions |
| **Agents** | [`devin-bridge`](https://github.com/Icaro0310/devin-bridge) | Policy-gated ACP client — allow / deny / ask |
| | [`devin-memory`](https://github.com/Icaro0310/devin-memory) | Anti-poisoning memory — provenance, versioning |
| **Ops** | [`devin-janitor`](https://github.com/Icaro0310/devin-janitor) | Session lifecycle — export-then-delete, dry-run first |
| | [`devin-orchestrator`](https://github.com/Icaro0310/devin-orchestrator) | Background-worker fan-out — deterministic planner |
| **Related** | [`poordjaevin`](https://github.com/Icaro0310/poordjaevin) | Calibrated decision layer via Devin's own model |
| | [`devin-powerups`](https://github.com/Icaro0310/devin-powerups) | Maintainer hub — registry, scaffolder, reports |
| | [`devin-office`](https://github.com/Icaro0310/devin-office) | Devin sessions and tools as an animated circuit board |
| | [`qwenpaw-suite`](https://github.com/Icaro0310/qwenpaw-suite) | Optional add-on for self-hosted model operators |

</details>

## The method

Every project adapts an existing, proven tool **plus** one Devin-specific extra
that must pass three tests:

1. does something the base tool *cannot* do
2. the extra disappears without Devin
3. explainable in one sentence

All tools are **read-only by default** on Devin's local stores and send
**zero telemetry**.

## Runs on Devin alone?

Yes — **no VM, no tunnel, no model server, no Slack, no Obsidian.** On a
locked-down corporate machine the whole catalog still works. The exceptions
are honest and documented per-repo: `devin-bridge` needs Node.js ≥ 20 (it is
an ACP client for the Devin CLI itself); `poordjaevin` has a fully offline
NLI fallback; `qwenpaw-suite` is a skippable add-on.

**Linux:** `pipx install "devin-doctor @ git+https://github.com/Icaro0310/devin-doctor.git"` —
requires Python ≥ 3.10.
**Windows:** same via `py -m pip install --user pipx`. Each README documents
the exact data paths and `--data-dir` overrides for both systems.

## Runs on a personal machine?

On a machine you control, the same tools can be wired into a standing
**personal agent runtime** — Devin plus a few optional companions, each
adding one capability:

| Optional piece | What it adds |
|---|---|
| **Hooks** (`SessionEnd`, `Stop`, `UserPromptSubmit`) | Automatic history export and lesson extraction after every session |
| **An MCP memory store** | Decisions and conventions that survive across sessions |
| **A notes vault** (e.g. Obsidian) | Curated long-term memory — decisions, learnings, session transcripts |
| **A scheduler** (cron / Task Scheduler) | A periodic "heartbeat" that wakes Devin with a checklist, and janitor runs |
| **A comms channel** (e.g. Slack) | Talk to your agent and get notified remotely |
| **`poordjaevin` as judge** | Cheap yes/no/rate answers — through Devin's own model via ACP, or a fully offline local model |

I run exactly this on my own machines — the driving repo
(`personal-agent-system`) stays private because it contains machine paths
and credentials, but the **pattern is the public part**: hooks + memory +
vault + scheduler + judge, all built from the catalog above.

## Português (BR)

**Ícaro Galvão — Senior QA Engineer.** Construo ferramentas *local-first*
que tornam agentes de código mais fáceis de inspecionar, avaliar e confiar.

O ecossistema `devin-*` são vinte utilitários open source (MIT) que leem os
dados locais do próprio Devin — sessões, stores SQLite, ACP — e os
transformam em diagnóstico, histórico, backup, métricas, memória,
verificação e dashboards. Tudo **sem cloud, sem telemetria, sem conta**.

### Funciona só com o Devin?

Sim. Nenhuma ferramenta exige VM, túnel, servidor de modelos, Slack ou
Obsidian — numa máquina corporativa travada o catálogo inteiro funciona.
Instalação em **Windows e Linux** com Python ≥ 3.10 + `pipx`; cada README
documenta os paths exatos (`~/.local/share/devin/cli/` no Linux,
`%APPDATA%\devin\` no Windows) e os overrides `--data-dir`.

### E numa máquina pessoal?

Os mesmos utilitários viram um runtime de agente persistente: hooks exportam
histórico e extraem lições ao fim de cada sessão, uma memória MCP guarda
decisões entre sessões, um vault acumula notas curadas, um agendador dispara
verificações periódicas, e um canal (Slack) permite falar com o agente à
distância. O meu repositório de runtime é privado por conter credenciais —
mas cada peça reutilizável está publicada no catálogo acima.

---

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=Icaro0310&show_icons=false&hide_border=true&hide_title=true&theme=transparent&count_private=true&include_all_commits=true" height="120" alt=""/>

<sub>Devin is a trademark of Cognition AI. Community project — not affiliated.</sub>

</div>
