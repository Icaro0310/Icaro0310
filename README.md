<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/banner-dark.png"/>
  <img src="assets/banner.png" alt="Ícaro Galvão — devin-* ecosystem" width="100%"/>
</picture>

<h1><a href="https://www.linkedin.com/in/ícaro-galvão-do-nascimento-663601280/">Ícaro Galvão</a></h1>

I build tools that make AI coding agents easier to inspect, evaluate and trust.
Currently building the `devin-*` ecosystem — twenty-plus local-first tools that turn
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

<a id="catalog"></a>

<details>
<summary><b>Full catalog — 23 entries</b></summary>

<br/>

| Wave | Repo | What it does |
|---|---|---|
| **Foundation** | [`devin-internals-spec`](https://github.com/Icaro0310/devin-internals-spec) | Store internals documented — schema detection, typed parsers |
| | [`devin-redact`](https://github.com/Icaro0310/devin-redact) | Secret/PII redaction that understands tool-call semantics |
| **Insight** | [`devin-doctor`](https://github.com/Icaro0310/devin-doctor) | Diagnose a Devin install → concrete fixes |
| | [`devin-history`](https://github.com/Icaro0310/devin-history) | Sessions → Markdown, JSON, CSV |
| | [`devin-pm`](https://github.com/Icaro0310/devin-pm) | Project manager over sessions — rollups, milestones |
| | [`devin-skill-catalog`](https://github.com/Icaro0310/devin-skill-catalog) | Inventory, lint and quarantine for `.devin/skills` and rules |
| **Assurance** | [`devin-backup`](https://github.com/Icaro0310/devin-backup) | Snapshot, verify, restore — schema-version manifests |
| | [`devin-metrics`](https://github.com/Icaro0310/devin-metrics) | Cost, tokens, sessions per project/model/day |
| | [`devin-qa-pack`](https://github.com/Icaro0310/devin-qa-pack) | Claims vs. reality — PASS / PARTIAL / UNVERIFIED |
| | [`devin-evals`](https://github.com/Icaro0310/devin-evals) | Replay sessions against rubric graders |
| | [`devin-dream`](https://github.com/Icaro0310/devin-dream) | Synthetic sessions with known verdicts — test judges and graders |
| **Memory** | [`devin-graph`](https://github.com/Icaro0310/devin-graph) | Sessions ↔ projects ↔ files ↔ tools |
| | [`devin-search`](https://github.com/Icaro0310/devin-search) | FTS5 full-text search across sessions |
| | [`devin-memory`](https://github.com/Icaro0310/devin-memory) | Anti-poisoning memory — provenance, versioning |
| **Control** | [`devin-bridge`](https://github.com/Icaro0310/devin-bridge) | Policy-gated ACP client — allow / deny / ask |
| **Ops** | [`devin-janitor`](https://github.com/Icaro0310/devin-janitor) | Session lifecycle — export-then-delete, dry-run first |
| | [`devin-orchestrator`](https://github.com/Icaro0310/devin-orchestrator) | Background-worker fan-out — deterministic planner |
| | [`devin-switch`](https://github.com/Icaro0310/devin-switch) | Config profile swaps — snapshot, dry-run, rollback |
| **Related** | [`poordjaevin`](https://github.com/Icaro0310/poordjaevin) | Calibrated decision layer via Devin's own model |
| | [`devin-powerups`](https://github.com/Icaro0310/devin-powerups) | Maintainer hub — registry, scaffolder, reports |
| | [`devin-office`](https://github.com/Icaro0310/devin-office) | Devin sessions and tools as an animated circuit board |
| | [`qwenpaw-suite`](https://github.com/Icaro0310/qwenpaw-suite) | Optional add-on for self-hosted model operators |
| | [`awesome-devin`](https://github.com/Icaro0310/awesome-devin) | Curated list — official resources + the whole ecosystem |

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

The catalog composes into a standing **agent runtime** when the machine is
yours. Each optional piece adds one capability — none is required:

| Optional piece | What it adds |
|---|---|
| **Hooks** (`SessionEnd`, `Stop`, `UserPromptSubmit`) | Automatic history export and lesson extraction after every session |
| **An MCP memory store** | Decisions and conventions that survive across sessions |
| **A notes vault** (e.g. Obsidian) | Curated long-term memory — decisions, learnings, transcripts |
| **A scheduler** (cron / Task Scheduler) | Periodic checklists — heartbeat, janitor, scheduled reports |
| **A comms channel** (e.g. Slack) | Talk to the agent and get notified remotely |
| **`poordjaevin` as judge** | Cheap yes/no/rate answers — via Devin's own model (ACP), or a fully offline local model |

### On a corporate machine

On a locked-down machine the catalog runs **on demand** and most of the
runtime can still be reconstructed locally:

- **Memory and learning are unaffected.** Hooks are event-driven
  (`UserPromptSubmit`, `Stop`, `SessionEnd`), so prompt logging, lesson
  extraction and history export keep working without any scheduler. The
  MCP memory store and `learned-*` skills only need a writable Devin
  config directory.
- **Proactivity is mostly recoverable.** Instead of a cron heartbeat,
  elapsed-time checks can piggyback on `UserPromptSubmit` — a checklist
  runs whenever you are active, which is when it matters. A persistent
  background loop (`while sleep; do devin acp …`) is equivalent while the
  machine is on.
- **Outbound restrictions are a non-issue** — nothing in the catalog makes
  a network call.

What a corporate machine genuinely cannot provide:

- **Wake-while-idle.** With no scheduler and the session closed, nothing
  ticks — a suspended laptop has no heartbeat.
- **Remote reach.** Without Slack (or any comms channel), the agent can
  detect something urgent but cannot reach you. Deferred notification —
  flag files read on your next prompt — works, but late.
- **Offload.** Heavy work (browser automation, builds) runs locally and
  competes for the machine's RAM.
- **Multi-machine topology.** No tunnel means `devin-office` probes and
  hubs are confined to loopback.

The runtime is an enhancement, never a dependency — roughly 90% of it
survives a locked-down machine.

## Português (BR)

**Ícaro Galvão — Senior QA Engineer.** Construo ferramentas *local-first*
que tornam agentes de código mais fáceis de inspecionar, avaliar e confiar.

O ecossistema `devin-*` são mais de vinte utilitários open source (MIT) que leem os
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

Os mesmos utilitários compõem um runtime de agente permanente: hooks
exportam histórico e extraem lições ao fim de cada sessão, uma memória MCP
guarda decisões entre sessões, um vault (ex.: Obsidian) acumula notas
curadas, um agendador dispara checklists periódicos, e um canal como o
Slack permite falar com o agente à distância.

### Numa máquina corporativa

O catálogo funciona sob demanda e a maior parte do runtime se reconstrói
localmente: memória e aprendizado são intocados (hooks são disparados por
eventos, não por tempo), a proatividade se recupera com verificações de
tempo decorrido dentro dos próprios prompts ou um loop em background, e
nada exige rede externa.

As perdas reais são quatro: **acordar em idle** (máquina suspensa não tem
heartbeat), **alcance remoto** (sem Slack o agente detecta o urgente mas
não te avisa em tempo real — notificação diferida via flag lida no próximo
prompt), **offload** (trabalho pesado compete pela RAM local) e
**topologia multi-máquina** (probes do `devin-office` ficam em loopback).
O runtime é um upgrade, nunca uma dependência.

---

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=Icaro0310&show_icons=false&hide_border=true&hide_title=true&theme=transparent&count_private=true&include_all_commits=true" height="120" alt=""/>

<sub>Devin is a trademark of Cognition AI. Community project — not affiliated.</sub>

</div>
