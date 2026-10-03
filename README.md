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

| | |
|---|---|
| [`devin-internals-spec`](https://github.com/Icaro0310/devin-internals-spec) | Devin's local stores, documented — schema detection, typed parsers, fixtures |
| [`devin-office`](https://github.com/Icaro0310/devin-office) | Live Devin activity as an animated SVG circuit board — sessions, subagents, tools |
| [`devin-doctor`](https://github.com/Icaro0310/devin-doctor) | `brew doctor` for a Devin install — stores, locks, config → concrete fixes |
| [`devin-history`](https://github.com/Icaro0310/devin-history) | Session history → Markdown, JSON, CSV, Obsidian-ready |
| [`poordjaevin`](https://github.com/Icaro0310/poordjaevin) | Calibrated decision layer — scores through Devin's own model via ACP |

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

## The private runtime — the pattern, not the code

The public repos are the **tools**. A private runtime
(`personal-agent-system`) drives them: hooks export session history on
`SessionEnd`, a learning loop promotes recurring lessons to `learned-*`
skills, an MCP memory store persists decisions, a heartbeat wakes a
persistent session on a checklist, and poordjaevin answers cheap
yes/no/rate questions through Devin's own model.

The code stays private (machine paths, credentials); the **pattern** is
public — every reusable piece is already in the catalog above.

<details>
<summary><b>Português (BR)</b></summary>

<br/>

**Ícaro Galvão — QA Engineer.** Construo ferramentas *local-first* que
tornam agentes de código mais observáveis, seguros e auditáveis.

Os vinte projetos `devin-*` transformam os dados de sessão do próprio Devin
em backups, busca, métricas, memória e QA — sem cloud, sem telemetria.
Funcionam **só com o Devin**: sem VM, sem túnel, sem servidor de modelos.

Instalação em **Windows e Linux**: Python ≥ 3.10 + `pipx`. Cada repo tem
README em EN/PT-BR com paths exatos e a secção *Funciona só com o Devin*.
O runtime pessoal não é publicado (credenciais/paths), mas o padrão está
documentado em *The private runtime* acima.

</details>

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=Icaro0310&show_icons=false&hide_border=true&hide_title=true&theme=transparent&count_private=true&include_all_commits=true" height="120" alt=""/>

<sub>Devin is a trademark of Cognition AI. Community project — not affiliated.</sub>

</div>
