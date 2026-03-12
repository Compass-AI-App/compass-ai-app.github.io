<p align="center">
  <img src="https://img.shields.io/badge/Compass-AI--Native%20Product%20Discovery-6C5CE7?style=for-the-badge&logoColor=white" alt="Compass" />
</p>

<h1 align="center">Compass</h1>

<p align="center">
  <strong>Cursor for Product Managers</strong><br/>
  AI-native product discovery that finds where your sources of truth disagree — and tells you what to build next.
</p>

<p align="center">
  <a href="https://github.com/Compass-AI-App/compass-AI/actions/workflows/ci.yml"><img src="https://github.com/Compass-AI-App/compass-AI/actions/workflows/ci.yml/badge.svg" alt="CI" /></a>
  <a href="https://github.com/Compass-AI-App/compass-AI/releases"><img src="https://github.com/Compass-AI-App/compass-AI/actions/workflows/release.yml/badge.svg" alt="Release" /></a>
  <img src="https://img.shields.io/badge/python-3.11+-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/Electron-React%2019-47848F?style=flat-square&logo=electron&logoColor=white" alt="Electron" />
  <img src="https://img.shields.io/badge/LLM-Anthropic%20Claude-D97757?style=flat-square" alt="Claude" />
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="License" />
</p>

<p align="center">
  <a href="https://compass-ai-app.github.io/compass-AI/">Website</a> · <a href="https://github.com/Compass-AI-App/compass-AI/releases/latest">Download</a> · <a href="https://github.com/Compass-AI-App/compass-AI">Source</a>
</p>

---

## The Problem

Cursor and Claude Code changed how teams build. But someone still has to figure out **what** to build. Product managers juggle strategy docs, user interviews, analytics dashboards, support tickets, and the reality of the codebase — often reaching different conclusions from each source. Decisions get made on gut feel instead of evidence.

## What Compass Does

Compass connects to your product's evidence sources and builds a **knowledge graph** across four sources of truth:

| Source | Question It Answers | Examples |
|--------|-------------------|----------|
| **Code** | What *can* happen? | Repos, APIs, feature flags, architecture, test coverage |
| **Docs** | What's *expected* to happen? | PRDs, strategy docs, roadmaps, RFCs, design specs |
| **Data** | What *is* happening? | Analytics, metrics, crash reports, usage patterns |
| **Judgment** | What *should* happen? | User interviews, support tickets, stakeholder feedback |

When these sources agree, things are working. When they disagree, that's where product opportunities hide.

---

## How It Works

```
Connect → Ingest → Reconcile → Discover → Act
```

### 1. Connect & Ingest

Point Compass at your product's evidence. 11 connectors out of the box:

| Connector | Source Type |
|-----------|-----------|
| **GitHub** | Code repos, PRs, issues |
| **Docs** | Markdown, text files, PDFs |
| **Analytics** | CSV metrics, dashboards |
| **Interviews** | User research transcripts |
| **Support** | Support tickets and feedback |
| **Jira** | Issues and sprint data |
| **Linear** | Project tracking |
| **Slack** | Channel conversations |
| **Confluence** | Wiki pages and docs |
| **Notion** | Pages and databases |
| **Zendesk** | Customer support tickets |

Evidence is embedded into a ChromaDB knowledge graph with semantic search across all sources.

### 2. Reconcile

Compass automatically detects **conflicts** between your sources of truth — across 6 source pairs (Code vs Docs, Code vs Data, Code vs Judgment, Docs vs Data, Docs vs Judgment, Data vs Judgment):

> *"Strategy doc says real-time sync is P0, but the codebase has no sync implementation. Last mentioned in sprint planning 6 weeks ago — likely stalled."*

Each conflict is ranked by severity and signal strength.

### 3. Discover

Conflicts and convergences are synthesized into **ranked product opportunities** with:

- **Confidence level** — based on how many sources agree
- **Evidence citations** — links to the exact docs, code, and data points
- **Lifecycle tracking** — see how opportunities evolve: `NEW` → `PERSISTENT` → `RESOLVED`
- **Impact estimates** — grounded in the data, not vibes

### 4. Act

Once you've found what to build, Compass helps you move:

| Action | What It Does |
|--------|-------------|
| **Generate Spec** | Agent-ready feature specs with task breakdowns, file paths, and acceptance criteria — paste directly into Cursor or Claude Code |
| **Write Brief** | Evidence-grounded product briefs with P0/P1/P2 requirements, success metrics, and risk analysis |
| **Write Update** | Stakeholder updates summarizing what changed across sources, new signals, and recommended next steps |
| **Challenge** | Structured devil's advocate — finds contradicting evidence, unsupported assumptions, and scores evidence quality (1-10) |
| **Design Experiment** | Validation experiment design with hypothesis, metrics, sample size, duration, and success criteria |
| **Analyze Data** | Interprets metrics, identifies trends, suggests investigative SQL queries, connects data to product implications |
| **Plan Week** | Weekly planning synthesized from evidence freshness, open opportunities, conflicts, and discovery history |

---

## Four Interfaces

| Interface | Use Case |
|-----------|----------|
| **Desktop App** (Electron) | Visual workspace — knowledge graph explorer, opportunity cards, brief generator, weekly plan widget |
| **CLI** | `compass discover`, `compass challenge`, `compass experiment` — full pipeline from the terminal |
| **MCP Server** | 13 tools for Claude Code and Cursor — ask "what should we build next?" without leaving your editor |
| **HTTP API** | RESTful endpoints for building custom integrations |

### MCP Tools

```
compass_status        compass_ingest       compass_reconcile
compass_discover      compass_specify      compass_ask
compass_search        compass_refresh      compass_connect
compass_challenge     compass_experiment   compass_plan_week
compass_write_brief   compass_write_update compass_analyze
```

### CLI Commands

```
compass init          compass connect      compass ingest
compass reconcile     compass discover     compass specify
compass challenge     compass experiment   compass analyze
compass plan-week     compass write-brief  compass write-update
compass status        compass search       compass refresh
compass chat          compass demo         compass doctor
compass mcp-serve     compass configure    compass quickstart
```

---

## 8 Chat Modes

Compass includes specialized AI agent modes for different PM workflows:

| Mode | What It Does |
|------|-------------|
| **Default** | Evidence-grounded Q&A about your product |
| **Thought Partner** | Brainstorm and explore ideas with Socratic questioning |
| **Technical Analyst** | Understand systems and architecture in PM-friendly terms |
| **Devil's Advocate** | Stress-test assumptions and surface blind spots |
| **Writer** | Draft briefs, updates, emails, and strategy docs grounded in evidence |
| **Meeting Prep** | Prepare talking points, anticipate questions, structure discussions |
| **Experiment Designer** | Design and refine validation experiments with evidence-grounded metrics |
| **Data Analyst** | Explore metrics, interpret trends, generate investigative queries |

---

## 9 Engine Components

Every engine component follows the same pattern: `Constructor(KnowledgeGraph, model, prompt_version) → query KG → ask_json → Pydantic model → 4 interfaces`.

| Component | Purpose |
|-----------|---------|
| **Reconciler** | Detects conflicts between the four sources of truth |
| **Discoverer** | Synthesizes conflicts into ranked opportunities |
| **Specifier** | Generates agent-ready feature specs |
| **Writer** | Produces evidence-grounded briefs and stakeholder updates |
| **Challenger** | Structured devil's advocate with evidence quality scoring |
| **Experimenter** | Designs validation experiments grounded in data |
| **Planner** | Weekly planning from evidence freshness and opportunity tracking |
| **Analyst** | Data interpretation with SQL query generation |
| **Reporter** | Shareable HTML/Markdown insight reports |

All prompts are versioned (`v1`, `v2`, ...) via a prompt registry, enabling A/B testing of prompt quality.

---

## Quick Start

### Desktop App

Download the native app for your platform:

- **[macOS (.dmg)](https://github.com/Compass-AI-App/compass-AI/releases/latest)**
- **[Windows (.exe)](https://github.com/Compass-AI-App/compass-AI/releases/latest)**
- **[Linux (.AppImage)](https://github.com/Compass-AI-App/compass-AI/releases/latest)**

The app includes an onboarding wizard — create a workspace, enter your API key, connect sources, and start discovering.

### CLI

```bash
# Install
cd engine && pip install -e ".[dev]"

# Try the demo (no API key needed)
compass demo

# Or use with your own product
export ANTHROPIC_API_KEY=sk-ant-...
compass init "My Product"
compass connect code ./src
compass connect docs ./strategy/
compass connect analytics ./metrics.csv
compass ingest
compass reconcile
compass discover
```

### MCP Integration

```bash
compass mcp install
```

Adds Compass tools to Claude Code or Cursor. Ask "what should we build next?" and get evidence-grounded recommendations without leaving your editor.

---

## Architecture

```
┌───────────────────────────────────────────────────┐
│                   Interfaces                       │
│  Desktop App  │  CLI  │  MCP Server  │  HTTP API  │
└────────────────────┬──────────────────────────────┘
                     │
┌────────────────────▼──────────────────────────────┐
│            Engine (Python / FastAPI)                │
│                                                    │
│  ┌─────────────┐  ┌────────────┐  ┌────────────┐ │
│  │ Connectors  │→ │ Knowledge  │→ │ Engine     │ │
│  │ (11 types)  │  │ Graph      │  │ Components │ │
│  │ GitHub,Jira │  │ (ChromaDB) │  │ (9 engines)│ │
│  │ Slack,Notion│  │            │  │ Reconciler │ │
│  │ Linear,Docs │  │ Semantic   │  │ Discoverer │ │
│  │ Analytics   │  │ Search +   │  │ Specifier  │ │
│  │ Interviews  │  │ Evidence   │  │ Writer     │ │
│  │ Support     │  │ Store      │  │ Challenger │ │
│  │ Confluence  │  │            │  │ Experiment │ │
│  │ Zendesk     │  │            │  │ Planner    │ │
│  └─────────────┘  └────────────┘  │ Analyst    │ │
│                                    │ Reporter   │ │
│  ┌─────────────┐                  └────────────┘ │
│  │ Orchestrator│  LLM Provider (BYOK)            │
│  │ + Chat (8   │  Anthropic Claude / Cloud       │
│  │   modes)    │                                  │
│  └─────────────┘                                  │
└───────────────────────────────────────────────────┘
```

### Tech Stack

**Engine** — Python 3.11+, FastAPI, ChromaDB, Pydantic, Anthropic SDK, Typer (CLI), Rich (terminal UI)

**Desktop App** — Electron 33, React 19, TypeScript, Vite 6, Zustand, Tailwind CSS, React Router, Lucide icons

**Cloud** — FastAPI, JWT auth, Stripe billing (optional managed LLM access)

---

## Project Structure

```
compass-AI/
├── engine/              # Python engine
│   ├── compass/
│   │   ├── engine/      # 9 engine components + KG + orchestrator
│   │   ├── connectors/  # 11 evidence source connectors
│   │   ├── models/      # Pydantic models (evidence, specs, docs, experiments, analysis, planning)
│   │   ├── prompts/     # Versioned prompt registry (9 components × v1)
│   │   ├── server.py    # FastAPI HTTP server
│   │   ├── mcp_server.py # MCP server (15 tools)
│   │   └── cli.py       # Typer CLI (20+ commands)
│   └── tests/           # 73 tests
├── app/                 # Electron desktop app
│   ├── src/
│   │   ├── pages/       # Workspace, Discover, Evidence, Chat, Settings
│   │   ├── components/  # OpportunityCard, SpecView, DocumentView, WeeklyPlanWidget
│   │   └── stores/      # Zustand (workspace, opportunities, chat)
│   └── electron/        # Main process, preload, engine bridge
├── cloud/               # Cloud API (auth, LLM proxy, billing)
├── demo/                # Sample data for compass demo
├── docs/                # Roadmap, implementation plan, ADRs
└── site/                # Landing page (GitHub Pages)
```

---

## Development

### Prerequisites

- Python 3.11+
- Node.js 20+
- An Anthropic API key (for LLM features)

### Setup

```bash
# Engine
cd engine
python -m venv .venv && source .venv/bin/activate
pip install -e ".[dev]"
python -m pytest tests/ -v  # 73 tests, all pass

# App
cd app
npm ci
npm run dev  # launches Electron + Vite + engine sidecar
```

### Verify

```bash
# Engine starts
cd engine && python -c "from compass.server import app; print('OK')"

# App compiles
cd app && npx tsc --noEmit

# Lint
cd engine && ruff check .
```

---

## Design Principles

**Evidence-grounded or nothing.** Every recommendation cites specific evidence. No hallucinated insights. If the evidence is insufficient, Compass says so.

**Four sources of truth.** Code, Docs, Data, and Judgment. One source alone is unreliable. Compass finds convergence — and flags divergence.

**One pattern for everything.** Every engine component follows: `KG query → LLM call → Pydantic model → 4 interfaces`. No special cases, no separate abstractions.

**BYOK (Bring Your Own Key).** Your data stays on your machine. Nothing is sent anywhere except the LLM provider you configure.

**Prompt versioning from day one.** Every component uses versioned prompts via a registry. Ship prompt improvements without changing code.

---

## Repositories

| Repo | Description |
|------|-------------|
| [**compass-AI**](https://github.com/Compass-AI-App/compass-AI) | Main repository — engine, desktop app, cloud, and docs |
| [**.github**](https://github.com/Compass-AI-App/.github) | Organization profile (this page) |

---

<p align="center">
  <sub>Built for PMs who believe product decisions should be grounded in evidence, not opinion.</sub>
</p>
