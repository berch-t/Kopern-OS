# Kopern-OS — AI Operating System starter kit for Claude Code

A free, MIT-licensed starter kit that turns Claude Code into your personal **AI Operating System (AIOS)**. Audience : anyone building automations — solopreneurs, small business operators, managers, creators, AI consultants, in-house ops teams.

The kit ships with :

- **8 skills** that personalize, audit, level up, activate squads, orchestrate workflows, search the catalog, track cost, snapshot sessions.
- **224 specialized agents** organized in 14 divisions.
- **8 Squads** — activable bundles of 5-15 agents mapped to your projects.
- **Kopern Conductor** — multi-agent orchestration doctrine with **5 runbooks** (MVP, contenu, incident, feature, cinq-phases).
- **Two opinionated frameworks** : the **3M Operator Lens** (Mindset · Method · Machine) and the **4C AIOS Architecture** (Context · Connections · Capabilities · Cadence).

You run `/onboard` once. The kit then personalizes itself to you and gives you a weekly compounding rhythm to keep building leverage.

---

## The litmus test

> **"While you're not at your desk, your AIOS observes one real-world event and produces an output that's faster and more accurate than what you'd produce yourself."**

Every design decision in this kit rolls up to that test. If a layer, skill, or template doesn't contribute to it, it doesn't ship.

---

## How you'll know it's working

Three felt **success indicators** tell you the AIOS is actually changing how you work. Not KPIs — there's no objective metric. These are lived experiences that show up in your week.

**1. Team-reaches-out :**

> *"A teammate messages you with a question. You realize your AIOS would answer it better, faster, and with exact sources — even if you were awake and free. So you ask your AIOS too. That's the moment you stop being a bottleneck for your own knowledge."*

**2. Context-switching reduction :**

> *"You stop opening new tabs. You stop launching the desktop app. When something new lands, your first move is to ask the AIOS, not to open six things. The default surface for thought work shifts. Silent. Compounding."*

**3. Knowledge-leaves-your-head :**

> *"You stop trying to remember business facts. You don't rehearse what you decided last quarter or what your customer said in that meeting. You trust the retrieval. The AIOS holds the truth, you hold the questions."*

**Personal foundation → company AI-readiness.** Once these indicators show up for one person, the same data architecture powers everything else. Custom dashboards on the data you already collect. Automations on top of the connections you already wired. Team rollout where everyone has theirs. *A company where every operator runs a personal AIOS is a company that's actually AI-ready.*

The kit teaches personal AIOS first. Everything scales from there.

---

## Two frameworks

The kit teaches two complementary frameworks. **3M Operator Lens first, 4C AIOS Architecture second.** Without the brain rewire, the architecture is just a folder structure.

### The 3M Operator Lens — Mindset · Method · Machine (how you think)

| M | One-liner |
|---|---|
| **Mindset** | Default Shift, Function Breakdown, Curiosity Rule. *To what extent can AI be leveraged here ?* |
| **Method** | Find Constraint → EAD (Eliminate, Automate, Delegate) → Map Process → Pick Autonomy Level → Tie to KPI. |
| **Machine** | Lego Principle, Validation Chain, Bike Method, Intern Rule, Kill Switch. *Boring is beautiful. Workflows beat agents.* |

Full breakdown in `references/operator-lens.md`. The `/level-up` skill walks you through all three weekly.

### The 4C AIOS Architecture — Context · Connections · Capabilities · Cadence (what you build)

| # | Layer | One-liner | "This layer is in place" test |
|---|---|---|---|
| 1 | **Context** | Knows your business | Fresh Claude session answers "what does this business do and who works here ?" without browsing |
| 2 | **Connections** | Reaches your stuff | "What's on my calendar tomorrow and what tasks are due ?" → live data, no paste |
| 3 | **Capabilities** | Knows how to do the work | A short phrase triggers a multi-step workflow that produces an artifact |
| 4 | **Cadence** | Runs without being asked | Laptop closed. A brief lands in the inbox. A teammate messages it and gets a real answer |

**Brand line :** Context. Connections. Capabilities. Cadence.

Dependency graph : Context is non-skippable. Connections + Capabilities can build in parallel. Cadence is last — don't automate workflows that don't work manually.

---

## What ships — 8 skills

The kit is intentionally lean on infrastructure but rich on capabilities. Skills are ideation prompts, thinking tools, and orchestration commands — not heavy automations.

### Core skills (the AIOS rhythm)

| Skill | Type | When to run |
|---|---|---|
| `/onboard` | Setup wizard (one-time) | Day 1, immediately after clone. 7-question interview. Generates Day-1 file set, fills `CLAUDE.md`, maps your projects to Squads. |
| `/audit` | Recurring thinking skill | Day 7, then weekly. 4C gap report. Read-only. Watch the score climb. |
| `/level-up` | Recurring thinking skill | Day 14, then weekly. 3M Lens interview (Mindset → Method → Machine). One run = one shipped artifact. |

### Capability skills (activate agents on demand)

| Skill | What it does |
|---|---|
| `/squad <name>` | Activate one of the 8 Squads (5-15 agents bundled for a scope of work). |
| `/orchestrate <runbook>` | Run a multi-agent **Kopern Conductor** workflow (MVP, contenu, incident, feature, cinq-phases). |
| `/roster <besoin>` | Search the 224-agent catalog for a specific need and add an ad-hoc agent to the active scope. |

### Operator skills (cost and continuity)

| Skill | What it does |
|---|---|
| `/cost` | Track LLM consumption per project, squad, session. Helps decide when to switch to a cheaper model. |
| `/snapshot` | Save and restore session state (active squad, ad-hoc agents, recent decisions). Survives reboots, project switches, days off. |

`/audit` asks *"is the AIOS built right ?"* (form). `/level-up` asks *"what business leverage am I missing ?"* (function). They work in series — fix structure first, then capability planning becomes meaningful.

---

## The 224-agent catalog

The kit ships with a curated catalog of **224 specialized AI agents** across 14 divisions :

| Division | Agents | Examples |
|---|---|---|
| Engineering | 29 | Frontend, Backend, AI, DevOps, SRE, Security, Database, Code Reviewer… |
| Design | 8 | UI, UX, Brand Guardian, Visual Storyteller… |
| Marketing | 27 | Content, Growth Hacker, LinkedIn, YouTube, SEO, AI Citation, podcasts… |
| Sales | 9 | Outbound, Discovery, Deal Strategist, Sales Engineer, Proposal… |
| Paid Media | 7 | PPC, Search Query Analyst, Tracking, Creative Strategist… |
| Product | 5 | PM, Sprint Prioritizer, Trend Researcher, Feedback Synthesizer… |
| Project Mgmt | 6 | Studio Producer, Project Shepherd, Experiment Tracker… |
| Testing | 8 | Reality Checker, Evidence Collector, Performance, API, Accessibility… |
| Support | 6 | Analytics Reporter, Finance Tracker, Legal Compliance… |
| Spatial Computing | 6 | XR Architect, visionOS, WebXR, Metal, Cockpit… |
| Specialized | 40 | Orchestrator, Conductor Prime, MCP Builder, Compliance Auditor, Objective Decomposer… |
| Finance | 5 | Bookkeeper, Financial Analyst, FP&A, Tax Strategist, Investment Researcher |
| Game Dev | 16 | Game Designer, Level Designer, Unity, Unreal, Godot, Roblox, Blender |
| Academic | 5 | Anthropologist, Geographer, Historian, Narratologist, Psychologist |

Full index : `agents/README.md`. Browse by division or by Squad.

### The 8 Squads

| Squad | For what |
|---|---|
| **builder** | Code a product from zero to prod |
| **shipper** | GTM, acquisition, growth, metrics |
| **researcher** | Discovery, synthesis, user research |
| **operator** | Admin, finance, legal, ops |
| **creator** | Content : social, YouTube, articles, visual |
| **spatial** | XR, visionOS, Metal, immersive |
| **voice** | Audio pipelines, STT, transcription |
| **game** | Multi-engine game development |

Definitions in `squads/*.yml`. Activated with `/squad <name>`. One active at a time (symlinks into `.claude/agents/`).

### Kopern Conductor — multi-agent orchestration

The **Kopern Conductor** is the orchestration doctrine that turns the catalog into coordinated workflows. **5 ready-to-use runbooks** :

| Runbook | For what |
|---|---|
| `runbook-mvp` | Zero to prod product, 3-7 days |
| `runbook-feature` | Add feature to existing product, 1-3 days |
| `runbook-cinq-phases` | Rigorous module build (Spec → Pseudocode → Architecture → Affinage → Finition), 1-5 days |
| `runbook-contenu` | Editorial cycle (post, video, article, ebook), hours to weeks |
| `runbook-incident` | P0/P1 incident response with mandatory post-mortem |

Doctrine details : `agents/orchestration/conductor-doctrine.md`. Quickstart : `agents/orchestration/QUICKSTART.md`.

---

## Principles and good practices

Kopern-OS is opinionated. These are the principles that shape every default in the kit. Follow them or override them in `CLAUDE.md` — but know what you're trading away.

### 1. Lean structure, rich behavior

The kit ships with the minimum number of files needed for the AIOS to work. No empty folders, no organization theater. Folders grow as `EXPANSIONS.md` describes — when you need them.

### 2. Workflows beat agents

Default to deterministic skills with one or zero AI calls. Reach for multi-step agents only when the work genuinely needs reasoning + tool use. `/level-up` enforces this via the Boring-is-Beautiful default.

### 3. Bike Method (training wheels first)

Every artifact `/level-up` scaffolds ships with `bike-method-phase: 1` — meaning you run it manually first to validate before automating. You don't get to skip Phase 1.

### 4. No auto-commit, no auto-push, no auto-deploy

Default rule. Sub-orchestrators and agents propose commit messages and deploys, but **you** execute them. Configurable in `CLAUDE.md` per project, but the default is hard.

### 5. Minimal change

When building or fixing, change the smallest possible scope. No opportunistic refactoring. No abstraction for hypothetical futures. The `engineering-minimal-change-engineer` agent embodies this and `runbook-cinq-phases` enforces it in Phase 4.

### 6. Evidence-based quality gates

The `testing-reality-checker` agent defaults to **NEEDS-WORK**. PASS requires evidence. Retry max 3 per phase. After 3, escalate to the user.

### 7. Cost-aware model routing

Use the cheapest model that can do the job. Section "Routage modèles" in `CLAUDE.md` lays out the 3-tier doctrine (Opus / Sonnet / Haiku) by task type. `/cost` tells you where the bill actually goes.

### 8. Decisions logged, not memorized

Every meaningful decision goes into `decisions/log.md` with **why**. Append-only. Future-you reads it instead of re-deriving the reasoning.

### 9. Voice paste is mandatory

`/onboard` Q2 requires pasted writing samples, not typed-mid-chat prose. A sample shaped by a conversation is not your voice.

### 10. The Default Shift question

Before doing any task : **"to what extent can AI be leveraged here ?"** The Mindset framework lives in your head, not in a file. `/level-up` plants it; you grow it.

---

## Quick start

1. **Clone the repo** to a working folder on your machine.
2. **Open it in Claude Code** and run `/onboard`. Answer the 7 questions honestly. Voice samples must be pasted, not described. Takes ~15 minutes. Day-1 file set drops at the end. Squads get mapped to your projects.
3. **Use it for a week.** Bring real questions. Make real decisions. Append them to `decisions/log.md`.
4. **Day 3 :** activate your default Squad with `/squad <name>` and try `/orchestrate runbook-mvp` (or `runbook-contenu`, depending on your offer type).
5. **Day 7 :** run `/audit`. Read the 4C gap report. Pick one gap to close.
6. **Day 14 :** run `/level-up`. The 3M Lens interview surfaces one automation worth building. Build it.
7. **Week 3+ :** weekly `/level-up` ritual. One shipped artifact per week. Run `/cost` monthly to keep the spend honest.

---

## Repo layout

```
kopern-os/
├── README.md                       ← You are here
├── CLAUDE.md                       ← Your operating manual (filled by /onboard)
├── EXPANSIONS.md                   ← What to add as you grow
├── LICENSE
├── .gitignore
├── aios-intake.md                  ← Source-of-truth for /onboard. Edit + re-run any time.
├── connections.md                  ← Registry of every system your AIOS can reach
│
├── context/                        ← About you, your business (filled by /onboard)
├── references/
│   └── operator-lens.md            ← The 3M Operator Lens (Mindset · Method · Machine)
├── decisions/
│   └── log.md                      ← Append-only record of what was decided and why
├── archives/                       ← Old stuff. Don't delete. Move here.
│
├── agents/                         ← 224-agent catalog (14 divisions)
│   ├── README.md                   ← Full catalog index
│   └── orchestration/              ← Kopern Conductor doctrine + 5 runbooks + handoff templates
│
├── squads/                         ← 8 squad YAML definitions (filled with your projects by /onboard)
│
└── .claude/
    ├── agents/                     ← Active agents (managed by /squad, runtime symlinks)
    └── skills/
        ├── onboard/SKILL.md
        ├── audit/SKILL.md
        ├── level-up/SKILL.md
        ├── squad/SKILL.md
        ├── orchestrate/SKILL.md
        ├── roster/SKILL.md
        ├── cost/SKILL.md
        └── snapshot/SKILL.md
```

See `EXPANSIONS.md` for what to add as you grow (`projects/`, `templates/`, `scripts/`, sub-OS folders, etc.).

---

## About Kopern AI

**Kopern AI** builds operator-grade AI tooling — AI Operating Systems, agent builders, and automation frameworks for solo founders, small ops teams, and consultants who want AI to actually run in the background of their week.

**Kopern-OS** is the open-source piece of that stack : a free, MIT-licensed starter template that turns Claude Code into a personal AI Operating System.

- **Founder :** Thomas Berchet ([@berch-t](https://github.com/berch-t)) — AI Engineer, based in Grenoble (France).
- **Other products :** [Kopern](https://kopern.ai) (SaaS AI agent builder), and a growing suite of vertical AIOS templates.
- **Contact :** [berchet.thomas@gmail.com](mailto:berchet.thomas@gmail.com) · [LinkedIn](https://www.linkedin.com/in/thomas-berchet)

Pull requests, issues, and forks welcome. If Kopern-OS becomes the backbone of your week, drop a star and a note — that's how the roadmap stays grounded in real usage.

---

## License

MIT License — see `LICENSE`. Copyright (c) 2026 Thomas Berchet / Kopern AI.

The Kopern-OS naming, the "3M Operator Lens" and "4C AIOS Architecture" labels, the **Kopern Conductor** doctrine, the **Squads** pattern, and the Kopern AI brand are creations of Thomas Berchet / Kopern AI. Code is MIT — reuse freely. Please do not repackage the Kopern brand or labels as your own product.
