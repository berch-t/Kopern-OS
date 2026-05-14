# Examples — multi-agent workflows in action

This directory contains example outputs demonstrating how Kopern-OS Squads and Kopern Conductor runbooks coordinate multiple agents on a single mission.

## Why this exists

The Kopern-OS catalog defines 224 specialized agents across 14 divisions. Agent definitions alone don't show what happens when you **deploy a Squad on a real task** and let Kopern Conductor orchestrate the phases.

These examples answer the question : *"What does it actually look like when a full Squad runs through a Conductor runbook ?"*

## Contents

### [conductor-spatial-discovery.md](./conductor-spatial-discovery.md)

**What :** A complete product discovery exercise where 8 agents worked in parallel to evaluate a software opportunity and produce a unified plan.

**The scenario :** Web research identified an opportunity at the intersection of AI agent orchestration and spatial computing. A Squad combining Product, Engineering, Design, Marketing, and Spatial Computing was then deployed simultaneously to produce :

- Market validation and competitive analysis
- Technical architecture (8-service system design with full SQL schema)
- Brand strategy and visual identity
- Go-to-market and growth plan
- Customer support operations blueprint
- UX research plan with personas and journey maps
- 35-week project execution plan with 65 sprint tickets
- Spatial interface architecture specification

**Agents involved :**

| Agent | Role |
|---|---|
| Product Trend Researcher | Market validation, competitive landscape |
| Backend Architect | System architecture, data model, API design |
| Brand Guardian | Positioning, visual identity, naming |
| Growth Hacker | GTM strategy, pricing, launch plan |
| Support Responder | Support tiers, onboarding, community |
| UX Researcher | Personas, journey maps, design principles |
| Project Shepherd | Phase plan, sprints, risk register |
| XR Interface Architect | Spatial UI specification |

**Key takeaway :** All 8 agents ran in parallel and produced coherent, cross-referencing plans with handoff templates from the Conductor doctrine. The output demonstrates Kopern-OS's ability to go from "find an opportunity" to "here's the full blueprint" in a single session.

### Other workflow examples

- [workflow-startup-mvp.md](./workflow-startup-mvp.md) — End-to-end MVP workflow
- [workflow-landing-page.md](./workflow-landing-page.md) — Landing page production
- [workflow-book-chapter.md](./workflow-book-chapter.md) — Book chapter draft
- [workflow-with-memory.md](./workflow-with-memory.md) — Persistent context across sessions

## Adding new examples

If you run an interesting Squad or Conductor exercise, consider adding it here. Good examples show :

- A Squad activated for a specific scope
- Multiple agents collaborating with structured handoffs
- The breadth of Kopern-OS capabilities
- Real-world applicability beyond the obvious tutorial path

Format suggestion : title, scenario, Squad used, runbook (if any), output excerpts, key takeaway, time-to-result.

---

*Part of [Kopern-OS](../../README.md). MIT licensed.*
