<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/banner-dark.png"/>
  <img src="assets/banner.png" alt="Ícaro Galvão — devin-* ecosystem" width="100%"/>
</picture>

<h1><a href="https://www.linkedin.com/in/ícaro-galvão-do-nascimento-663601280/">Ícaro Galvão</a></h1>

I build local-first tools for understanding, verifying, controlling and
extending AI coding agents — a public `devin-*` ecosystem organized around
four jobs: **Understand · Verify · Control · Build**. Distributed through a
profile-based DevKit, with a maintainer hub and related artifacts in the
catalog.

[Website](https://icaro0310.github.io) · [LinkedIn](https://www.linkedin.com/in/ícaro-galvão-do-nascimento-663601280/) · [Catalog](#catalog)

[![MIT](https://img.shields.io/badge/license-MIT-1d1d1f?style=flat-square)](https://github.com/Icaro0310/devin-powerups/blob/main/LICENSE)
[![local-first](https://img.shields.io/badge/local--first-zero%20telemetry-0071e3?style=flat-square)](#runs-on-devin-alone)
[![profile views](https://komarev.com/ghpvc/?username=Icaro0310&style=flat-square&color=0071e3)](https://github.com/Icaro0310)
[![followers](https://img.shields.io/github/followers/Icaro0310?style=flat-square&color=1d1d1f)](https://github.com/Icaro0310?tab=followers)
[![stars](https://img.shields.io/github/stars/Icaro0310/awesome-devin?style=flat-square&label=ecosystem%20stars)](https://github.com/Icaro0310/awesome-devin/stargazers)

</div>

## Selected work

The ecosystem by job — the flagship of each track:

| Track | | |
|---|---|---|
| **Understand** | [`devin-internals-spec`](https://github.com/Icaro0310/devin-internals-spec) | Devin's local stores, documented — schema detection, typed parsers, contract boundary against drift |
| **Verify** | [`devin-qa-pack`](https://github.com/Icaro0310/devin-qa-pack) | Flagship evidence gate — PASS / PARTIAL / UNVERIFIED from recorded tool calls |
| **Verify** | [`devin-evals`](https://github.com/Icaro0310/devin-evals) | Replay recorded sessions against deterministic rubrics; agent quality as a regression signal |
| **Verify** | [`poordjaevin`](https://github.com/Icaro0310/poordjaevin) | Calibrated yes/no/score answers for agentic workflows — measured ECE 0.170 → 0.071 on the shipped eval set |
| **Control** | [`devin-bridge`](https://github.com/Icaro0310/devin-bridge) | Policy-gated ACP client — allow / deny / ask, fail-closed, per-repo session isolation |
| **Control** | [`devin-redact`](https://github.com/Icaro0310/devin-redact) | Secret/PII redaction that understands tool-call semantics before exports leave the machine |
| **Build** | [`devin-devkit`](https://github.com/Icaro0310/devin-devkit) | Profile-based distribution: registry-driven installs for Linux, Personal Windows and Corporate Windows |

<div align="center">

<a href="https://icaro0310.github.io/demos/devin-office.html"><img src="assets/office-demo.gif" alt="devin-office demo: Devin sessions, subagents and tools as an animated circuit board (synthetic data)" width="80%"/></a>

<sub>**devin-office**: local session dashboard. Live view when a Devin session source is available; demo mode uses synthetic data. Circuit board (above) and a session kanban (RUNNING · BLOCKED · REVIEW · CLOSED) · [open the kanban demo](https://icaro0310.github.io/demos/devin-office-kanban.html)</sub>

</div>

## Install the ecosystem

One registry ([`devin-powerups`](https://github.com/Icaro0310/devin-powerups)) is
the source of truth; [`devin-devkit`](https://github.com/Icaro0310/devin-devkit)
is the distribution layer that installs it under three declared environments:

| Environment | Runtime | Install |
|---|---|---|
| **Linux** | Extended | `devin-devkit install full --environment linux` |
| **Personal Windows** | Extended | `devin-devkit install full --environment personal-windows` |
| **Corporate Windows** | Local-only | `devin-devkit install full --environment corporate-windows` |

Extended mode runs locally plus optional Devin VM/QwenPaw delegation where a
tool supports it. Corporate Windows is **local-only**: no VM, QwenPaw, Slack
dependency, external compute or workload delegation — and it is selected
explicitly, because the OS alone cannot distinguish a personal Windows machine
from a restricted one. The registry records per-tool compatibility; the DevKit
previews the plan before installing (`--apply` to commit).

**See the ecosystem in action** → [reproducible agent-assurance demo](https://github.com/Icaro0310/devin-qa-pack/tree/main/examples/agent-assurance): synthetic sessions with known defects → schema check → claim audit → rubric grading, end to end.

<a id="catalog"></a>

<details>
<!-- DEVIN-CATALOG:BEGIN -->
<summary><b>The ecosystem — 19 first-party tools · 3 distribution layers · 1 registry hub · 2 related artifacts (25 entries)</b></summary>

<br/>

| Group | Repo | What it does |
|---|---|---|
| **Understand** | [`devin-internals-spec`](https://github.com/Icaro0310/devin-internals-spec) | Documented internals of Devin Desktop/CLI stores + schema-version detection + fixtures + devin-inspect CLI. |
| **Control** | [`devin-redact`](https://github.com/Icaro0310/devin-redact) | Secret/PII redaction that understands Devin tool-call semantics, in-place in SQLite, with a verification gate. |
| **Understand** | [`devin-history`](https://github.com/Icaro0310/devin-history) | Export and audit Devin session history — markdown notes, JSON, CSV, Obsidian-ready. |
| **Understand** | [`devin-doctor`](https://github.com/Icaro0310/devin-doctor) | Diagnose a Devin Desktop installation: stores, schema, locks, config, disk — with fix suggestions. |
| **Operations** | [`devin-pm`](https://github.com/Icaro0310/devin-pm) | Project manager over sessions: per-repo rollups, milestones, status reports, registry.json. |
| **Verify** | [`devin-qa-pack`](https://github.com/Icaro0310/devin-qa-pack) | Flagship QA audit: verifies session deliverable claims against tool-call ground truth and reports PASS/PARTIAL/UNVERIFIED. |
| **Verify** | [`devin-metrics`](https://github.com/Icaro0310/devin-metrics) | Local-only session observability: activity, context size, and token peaks per project/model/day; zero telemetry. Devin does not persist cost fields, so cost is not claimed. Includes an optional dashboard subpackage and command. |
| **Control** | [`devin-backup`](https://github.com/Icaro0310/devin-backup) | Safe snapshot/verify/restore/rotate of Devin stores with schema-version manifests. |
| **Understand** | [`devin-search`](https://github.com/Icaro0310/devin-search) | FTS5 full-text search across all Devin sessions, role-tagged and project-filtered. |
| **Understand** | [`devin-graph`](https://github.com/Icaro0310/devin-graph) | Knowledge graph: sessions, projects, files touched, tools used — queryable edges. |
| **Verify** | [`devin-evals`](https://github.com/Icaro0310/devin-evals) | Deterministic eval harness: replay recorded sessions against rubric graders; the `dream` subgroup generates synthetic sessions with known verdicts (D01-D09, absorbs devin-dream). |
| **Control** | [`devin-memory`](https://github.com/Icaro0310/devin-memory) | Anti-poisoning memory store: provenance, versioning, quarantine gate, and session-learning utilities. |
| **Control** | [`devin-janitor`](https://github.com/Icaro0310/devin-janitor) | Session lifecycle janitor: export-then-delete pipeline, tiered classification, pluggable judge, pending-retry for locked stores. |
| **Control** | [`devin-bridge`](https://github.com/Icaro0310/devin-bridge) | Policy-gated ACP client (Node.js, CI matrix Node 22 + 24): isolated sessions per repo with allow/deny/ask permission policy. |
| **Control** | [`devin-orchestrator`](https://github.com/Icaro0310/devin-orchestrator) | Background-worker fan-out policy: deterministic planner enforcing worker caps (max 3), no nesting, read-only profiles for review, collect-before-report. Skill + always-on rule. |
| **Understand** | [`devin-office`](https://github.com/Icaro0310/devin-office) | Local-first Devin session and subagent dashboard with standalone and optional split modes. |
| **Verify** | [`poordjaevin`](https://github.com/Icaro0310/poordjaevin) | Djævin: calibrated local-first decision layer with typed questions and honest confidence. The Devin ACP backend reuses the model your Devin CLI already runs (no extra download, no API key); the local NLI backend stays as a fully-offline fallback. |
| **Control** | [`devin-switch`](https://github.com/Icaro0310/devin-switch) | Switch between Devin configuration profiles (hooks, MCP, models) with snapshot, sha256 verify, atomic write, journal and rollback. Dry-run by default; secrets never printed. |
| **Build** | [`devin-skill-catalog`](https://github.com/Icaro0310/devin-skill-catalog) | Lifecycle + quality gates for .devin skills/rules: scan, lint, diff, G1/G2 gates, quarantined→approved→active lifecycle, sha256-verified export/import bundles (imports land quarantined). |
| **Distribution** | [`devin-devkit`](https://github.com/Icaro0310/devin-devkit) | Profile-based installer for the public Devin tools across Linux, Personal Windows and Corporate Windows; reads the registry manifest and installs isolated CLIs with uv, plus the Node bridge with npm. |
| **Distribution** | [`homebrew-tap`](https://github.com/Icaro0310/homebrew-tap) | Homebrew tap with formulas for the public devin-* CLIs; install on Linux or macOS via `brew install Icaro0310/tap/<tool>`. Content is written by release automation, consumed read-only. |
| **Distribution** | [`scoop-bucket`](https://github.com/Icaro0310/scoop-bucket) | Scoop bucket with manifests for the public devin-* CLIs on Windows; install via `scoop install Icaro0310/<tool>`. Content is written by release automation, consumed read-only. |
| **Maintainer hub** | [`devin-powerups`](https://github.com/Icaro0310/devin-powerups) | Public maintainer hub: registry, roadmap, project template, scaffolder, release checks, and community catalog generators. |
| **Related Suite** | [`qwenpaw-suite`](https://github.com/Icaro0310/qwenpaw-suite) | Optional QwenPaw add-on for self-hosted model operators. Includes the local-model bridge, health checks, and GitHub/local documentation sync. |
| **Related Resource** | [`awesome-devin`](https://github.com/Icaro0310/awesome-devin) | Curated awesome-list of Devin tooling and resources (CC0). |
<!-- DEVIN-CATALOG:END -->

</details>

## The method

Every project adapts an existing, proven tool **plus** one Devin-specific extra
that must pass three tests:

1. does something the base tool *cannot* do
2. the extra disappears without Devin
3. explainable in one sentence

Tools are **local-first** and send **zero telemetry**. Destructive or
mutating operations are explicit, guarded, and dry-run by default where
applicable.

## Runs on Devin alone?

Yes — **no VM, no tunnel, no model server, no Slack, no Obsidian.** The
DevKit-installable catalog still works on a locked-down corporate machine.
The exceptions are explicit in the registry: `devin-bridge` needs Node.js
≥ 20 (it is an ACP client for the Devin CLI itself); `poordjaevin` has a
fully offline NLI fallback; `qwenpaw-suite` is an optional related suite and
is unsupported in Corporate Windows.

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
- **Outbound restrictions are a non-issue** — the read/audit tools run
  fully offline. Only explicit opt-ins touch the network: `devin-devkit`
  downloads installs over HTTPS and `devin-bridge` speaks ACP to the
  local Devin CLI.

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

## Windows and Linux documentation

The public tools target Linux, Personal Windows and Corporate Windows. Shared
purpose and usage stay in `README.md`; each repository's Windows and Linux
guides carry platform-specific installation, Devin paths, PATH setup,
scheduling, and troubleshooting. The DevKit additionally documents the
corporate local-only mode and a registry-generated compatibility matrix.
macOS is planned but not yet claimed as tested.

---

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=Icaro0310&show_icons=false&hide_border=true&hide_title=true&theme=transparent&count_private=true&include_all_commits=true&cache_seconds=1800" height="120" alt=""/>
<img src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.github.com%2Fusers%2FIcaro0310&query=%24.public_repos&label=public%20repos&style=flat-square&color=555&labelColor=555&cacheSeconds=1800" height="22" alt="public repos"/>

<sub>Devin is a trademark of Cognition AI. Community project — not affiliated.</sub>

</div>
