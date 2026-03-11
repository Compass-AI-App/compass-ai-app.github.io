<p align="center">
  <img src="https://img.shields.io/badge/Compass-AI--Native%20Product%20Discovery-6C5CE7?style=for-the-badge&logoColor=white" alt="Compass" />
</p>

<h1 align="center">🧭 Compass</h1>

<p align="center">
  <strong>Cursor for Product Managers</strong><br/>
  AI-native product discovery that connects your code, docs, data, and judgment into one source of truth.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/python-3.11+-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/Electron-React%2019-47848F?style=flat-square&logo=electron&logoColor=white" alt="Electron" />
  <img src="https://img.shields.io/badge/LLM-Anthropic%20Claude-D97757?style=flat-square" alt="Claude" />
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="License" />
</p>

---

## The Problem

Product managers drown in fragmented information. Strategy lives in Google Docs, reality lives in code, user pain lives in support tickets, and metrics live in dashboards. No one sees the full picture — so decisions are made on gut feel instead of evidence.

## What Compass Does

Compass connects to all your product's evidence sources and builds a **knowledge graph** across four sources of truth:

| Source | What It Tells You | Examples |
|--------|-------------------|----------|
| **Code** | What *can* happen | Repos, APIs, feature flags, architecture |
| **Docs** | What's *expected* to happen | PRDs, strategy docs, roadmaps, RFCs |
| **Data** | What *is* happening | Analytics, metrics, dashboards, experiments |
| **Judgment** | What *should* happen | User feedback, support tickets, PM notes |

### Conflict Detection

Compass automatically surfaces contradictions between sources:

> *"Strategy doc says real-time sync is P0, but the codebase has no sync implementation. Last mentioned in sprint planning 6 weeks ago — likely stalled."*

### Evidence-Ranked Opportunities

Every recommendation comes with:

- **Confidence level** — based on how many sources agree
- **Evidence citations** — links to the exact docs, code, and data points
- **Lifecycle tracking** — see how opportunities evolve: `NEW` → `PERSISTENT` → `RESOLVED`

### Agent-Ready Output

Compass generates feature specs that AI coding tools can execute directly:

```
compass spec "Add real-time sync" | cursor apply
```

It also produces evidence-grounded **product briefs** and **stakeholder updates** — no more starting from a blank page.

---

## Interfaces

| Interface | Use Case |
|-----------|----------|
| **Desktop App** (Electron) | Primary PM interface — visual knowledge graph, opportunity explorer, brief generator |
| **CLI** | Power user interface for scripting and automation |
| **MCP Server** | Use Compass inside Claude Code or Cursor as a tool |
| **HTTP API** | Build integrations with your existing workflow |

---

## Quick Start

```bash
pip install compass-ai
compass demo
```

This launches a guided demo with a sample product, pre-loaded evidence sources, and example conflict detection — no API key needed.

For real usage, bring your own Anthropic API key:

```bash
export ANTHROPIC_API_KEY=sk-ant-...
compass init my-product
compass connect repo ./my-repo
compass connect docs ./specs/
compass analyze
```

---

## Tech Stack

**Engine** — Python backend powering all intelligence

- FastAPI for the HTTP and MCP server
- ChromaDB for vector storage and knowledge graph persistence
- Anthropic Claude for LLM reasoning

**Desktop App** — Electron frontend for product managers

- React 19 with TypeScript
- Vite for builds
- Tailwind CSS for styling
- Zustand for state management

---

## Principles

**Evidence-grounded or nothing.** Every recommendation cites specific evidence. No hand-waving, no hallucinated insights. If there isn't enough evidence, Compass says so.

**Four sources of truth.** Code, Docs, Data, and Judgment. One source alone is unreliable. Compass looks for convergence — and flags divergence.

**BYOK (Bring Your Own Key).** Compass uses your own Anthropic API key. Your data stays on your machine. Nothing is sent anywhere except the LLM provider you configure.

---

<p align="center">
  <sub>Built for PMs who believe product decisions should be grounded in evidence, not opinion.</sub>
</p>
