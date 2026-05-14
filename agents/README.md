# Kopern-OS — Catalogue d'agents

> Catalogue source des **222 agents spécialisés** que ton AIOS peut activer à la demande. Chaque agent est un expert avec son scope, ses livrables et son protocole. Tu ne charges pas tout — tu actives une **Squad** quand tu en as besoin, et le **Kopern Conductor** orchestre les enchaînements multi-agents quand tu lances un workflow.

---

## Comment ça marche

```
agents/                  ← Catalogue source (cette doc). 222 fichiers Markdown.
├── README.md            ← Tu y es.
├── orchestration/       ← Kopern Conductor : doctrine, playbooks, runbooks.
└── [14 divisions]       ← Les agents, organisés par expertise.

squads/                  ← Bundles d'agents activables (8 squads prédéfinis).
.claude/agents/          ← Agents ACTIFS (symlinks du squad courant).
.claude/skills/squad/    ← Active / liste / efface une squad.
.claude/skills/orchestrate/  ← Lance un runbook Conductor.
.claude/skills/roster/   ← Recherche un agent par besoin.
```

**Trois mouvements :**

1. `/squad <nom>` → active une squad (5-15 agents chargés dans `.claude/agents/`).
2. `/roster <besoin>` → cherche un agent précis dans le catalogue et l'ajoute au scope courant.
3. `/orchestrate <runbook>` → lance un workflow Conductor (MVP, contenu, incident, feature).

Le contexte reste léger. Tu n'as jamais 222 agents chargés en même temps.

---

## Les 8 Squads

Chaque Squad est un scope de travail. Activée avec `/squad <nom>`.

| Squad | Pour quoi | Cas d'usage type | Taille |
|---|---|---|---|
| **builder** | Coder un MVP de zéro à la prod | Nouveau produit, MVP, feature complexe | ~16 agents |
| **shipper** | GTM, acquisition, métriques, croissance | Lancement public, growth, mesure adoption | ~13 agents |
| **researcher** | Discovery, synthèse, recherche utilisateur | Comprendre un marché avant de coder | ~13 agents |
| **operator** | Admin, finance, légal, ops solo-business | Transversal aux activités | ~12 agents |
| **creator** | Contenu social, YouTube, articles, visuel | Posts, vidéos, ebooks | ~12 agents |
| **spatial** | XR, visionOS, Metal, immersif | Prototype AR/VR, app Vision Pro | ~7 agents |
| **voice** | Pipelines audio, STT, transcription | Outil audio-to-text, email intelligence | ~6 agents |
| **game** | Moteurs (Unity, Unreal, Godot, Roblox, Blender) | Side-project, prototype | ~16 agents |

Détails complets dans `../squads/*.yml`.

---

## Kopern Conductor

Le **Conductor** est la couche d'orchestration multi-agents. Il définit comment plusieurs agents s'enchaînent, où sont les quality gates, et comment passer le contexte d'un agent au suivant sans perte.

- `orchestration/conductor-doctrine.md` — doctrine complète (phases, boucles Dev↔QA, retry max)
- `orchestration/QUICKSTART.md` — 5 minutes pour comprendre
- `orchestration/EXECUTIVE-BRIEF.md` — vue stratégique
- `orchestration/playbooks/` — 7 phases d'un workflow Conductor
- `orchestration/runbooks/` — scénarios prêts à l'emploi (MVP, contenu, incident, feature)
- `orchestration/coordination/` — templates de handoff entre agents

Trois modes de déploiement :

| Mode | Agents | Durée | Cas d'usage |
|---|---|---|---|
| **Conductor-Full** | Tous | semaines | Cycle produit complet |
| **Conductor-Sprint** | 15-25 | jours | Feature ou MVP |
| **Conductor-Micro** | 5-10 | heures | Tâche ciblée |

---

## Index complet par division

Tableau référence. Chaque entrée → fichier agent prêt à l'emploi.

### Engineering (29)

| Agent | Spécialité |
|---|---|
| [Frontend Developer](engineering/engineering-frontend-developer.md) | React/Vue/Angular, UI, Core Web Vitals |
| [Backend Architect](engineering/engineering-backend-architect.md) | API design, BDD, scalabilité |
| [Mobile App Builder](engineering/engineering-mobile-app-builder.md) | iOS/Android, RN, Flutter |
| [AI Engineer](engineering/engineering-ai-engineer.md) | ML, déploiement, intégration IA |
| [DevOps Automator](engineering/engineering-devops-automator.md) | CI/CD, infra automation, cloud |
| [Rapid Prototyper](engineering/engineering-rapid-prototyper.md) | POC rapide, MVP |
| [Senior Developer](engineering/engineering-senior-developer.md) | Laravel/Livewire, patterns avancés |
| [Filament Optimization Specialist](engineering/engineering-filament-optimization-specialist.md) | Filament PHP admin UX |
| [Security Engineer](engineering/engineering-security-engineer.md) | Threat modeling, code review sécurité |
| [Autonomous Optimization Architect](engineering/engineering-autonomous-optimization-architect.md) | LLM routing, cost optimization |
| [Embedded Firmware Engineer](engineering/engineering-embedded-firmware-engineer.md) | Bare-metal, RTOS, ESP32/STM32/Nordic |
| [Incident Response Commander](engineering/engineering-incident-response-commander.md) | Incidents, post-mortems, on-call |
| [Solidity Smart Contract Engineer](engineering/engineering-solidity-smart-contract-engineer.md) | EVM, gas optimization, DeFi |
| [Codebase Onboarding Engineer](engineering/engineering-codebase-onboarding-engineer.md) | Découverte rapide de repos |
| [Technical Writer](engineering/engineering-technical-writer.md) | Docs développeur, API reference |
| [Threat Detection Engineer](engineering/engineering-threat-detection-engineer.md) | SIEM, threat hunting, ATT&CK |
| [WeChat Mini Program Developer](engineering/engineering-wechat-mini-program-developer.md) | WeChat ecosystem |
| [Code Reviewer](engineering/engineering-code-reviewer.md) | Reviews constructives, sécurité |
| [Database Optimizer](engineering/engineering-database-optimizer.md) | Schémas, requêtes, indexation |
| [Git Workflow Master](engineering/engineering-git-workflow-master.md) | Branching, conventional commits |
| [Software Architect](engineering/engineering-software-architect.md) | System design, DDD, trade-offs |
| [SRE](engineering/engineering-sre.md) | SLOs, observability, chaos engineering |
| [AI Data Remediation Engineer](engineering/engineering-ai-data-remediation-engineer.md) | Pipelines self-healing, SLMs air-gapped |
| [Data Engineer](engineering/engineering-data-engineer.md) | Pipelines, lakehouse, ETL/ELT |
| [Feishu Integration Developer](engineering/engineering-feishu-integration-developer.md) | Lark/Feishu Open Platform |
| [CMS Developer](engineering/engineering-cms-developer.md) | WordPress, Drupal |
| [Email Intelligence Engineer](engineering/engineering-email-intelligence-engineer.md) | Parsing email, MIME, contexte IA |
| [Voice AI Integration Engineer](engineering/engineering-voice-ai-integration-engineer.md) | STT, Whisper, ASR, diarisation |
| [Minimal Change Engineer](engineering/engineering-minimal-change-engineer.md) | Changements minimaux, surgical edits |

### Design (8)

| Agent | Spécialité |
|---|---|
| [UI Designer](design/design-ui-designer.md) | Design visuel, design systems |
| [UX Researcher](design/design-ux-researcher.md) | User testing, comportement |
| [UX Architect](design/design-ux-architect.md) | Architecture technique, CSS systems |
| [Brand Guardian](design/design-brand-guardian.md) | Identité, cohérence, positionnement |
| [Visual Storyteller](design/design-visual-storyteller.md) | Narratifs visuels, multimédia |
| [Whimsy Injector](design/design-whimsy-injector.md) | Délice, micro-interactions |
| [Image Prompt Engineer](design/design-image-prompt-engineer.md) | Prompts Midjourney/DALL-E/SD |
| [Inclusive Visuals Specialist](design/design-inclusive-visuals-specialist.md) | Représentation, biais, authenticité |

### Paid Media (7)

| Agent | Spécialité |
|---|---|
| [PPC Campaign Strategist](paid-media/paid-media-ppc-strategist.md) | Google/Microsoft/Amazon Ads |
| [Search Query Analyst](paid-media/paid-media-search-query-analyst.md) | Negative keywords, intent mapping |
| [Paid Media Auditor](paid-media/paid-media-auditor.md) | Audits 200+ points |
| [Tracking & Measurement Specialist](paid-media/paid-media-tracking-specialist.md) | GTM, GA4, CAPI |
| [Ad Creative Strategist](paid-media/paid-media-creative-strategist.md) | RSA, Meta creative, Performance Max |
| [Programmatic & Display Buyer](paid-media/paid-media-programmatic-buyer.md) | GDN, DSPs, ABM display |
| [Paid Social Strategist](paid-media/paid-media-paid-social-strategist.md) | Meta, LinkedIn, TikTok |

### Sales (9)

| Agent | Spécialité |
|---|---|
| [Outbound Strategist](sales/sales-outbound-strategist.md) | Signal-based prospecting |
| [Discovery Coach](sales/sales-discovery-coach.md) | SPIN, Gap Selling, Sandler |
| [Deal Strategist](sales/sales-deal-strategist.md) | MEDDPICC, win planning |
| [Sales Engineer](sales/sales-engineer.md) | Démos techniques, POC, battlecards |
| [Proposal Strategist](sales/sales-proposal-strategist.md) | RFP, win themes |
| [Pipeline Analyst](sales/sales-pipeline-analyst.md) | Forecasting, velocity, RevOps |
| [Account Strategist](sales/sales-account-strategist.md) | Land-and-expand, QBR |
| [Sales Coach](sales/sales-coach.md) | Coaching rep, pipeline review |
| [Sales Outreach](specialized/sales-outreach.md) | Cold prospecting, cadences |

### Marketing (27)

| Agent | Spécialité |
|---|---|
| [Growth Hacker](marketing/marketing-growth-hacker.md) | Acquisition rapide, loops virales |
| [Content Creator](marketing/marketing-content-creator.md) | Multi-plateforme, calendrier éditorial |
| [Twitter Engager](marketing/marketing-twitter-engager.md) | Real-time, thought leadership |
| [TikTok Strategist](marketing/marketing-tiktok-strategist.md) | Viral, algorithme |
| [Instagram Curator](marketing/marketing-instagram-curator.md) | Visual storytelling |
| [Reddit Community Builder](marketing/marketing-reddit-community-builder.md) | Engagement authentique |
| [App Store Optimizer](marketing/marketing-app-store-optimizer.md) | ASO |
| [Social Media Strategist](marketing/marketing-social-media-strategist.md) | Cross-plateforme |
| [Xiaohongshu Specialist](marketing/marketing-xiaohongshu-specialist.md) | Lifestyle, trend-driven |
| [WeChat Official Account Manager](marketing/marketing-wechat-official-account.md) | OA WeChat |
| [Zhihu Strategist](marketing/marketing-zhihu-strategist.md) | Knowledge-driven, Q&A |
| [Baidu SEO Specialist](marketing/marketing-baidu-seo-specialist.md) | Baidu, ICP compliance |
| [Bilibili Content Strategist](marketing/marketing-bilibili-content-strategist.md) | B站, danmaku |
| [Carousel Growth Engine](marketing/marketing-carousel-growth-engine.md) | Carousels TikTok/IG, publishing auto |
| [LinkedIn Content Creator](marketing/marketing-linkedin-content-creator.md) | Personal branding, B2B |
| [China E-Commerce Operator](marketing/marketing-china-ecommerce-operator.md) | Taobao, Tmall, Pinduoduo |
| [Kuaishou Strategist](marketing/marketing-kuaishou-strategist.md) | 老铁, grassroots |
| [SEO Specialist](marketing/marketing-seo-specialist.md) | Technical SEO, link building |
| [Book Co-Author](marketing/marketing-book-co-author.md) | Ghostwriting, publishing |
| [Cross-Border E-Commerce](marketing/marketing-cross-border-ecommerce.md) | Amazon, Shopee, Lazada |
| [Douyin Strategist](marketing/marketing-douyin-strategist.md) | Douyin short-video |
| [Livestream Commerce Coach](marketing/marketing-livestream-commerce-coach.md) | Live e-commerce |
| [Podcast Strategist](marketing/marketing-podcast-strategist.md) | Podcast strategy |
| [Private Domain Operator](marketing/marketing-private-domain-operator.md) | WeCom, private traffic |
| [Short-Video Editing Coach](marketing/marketing-short-video-editing-coach.md) | Post-prod, specs plateformes |
| [Weibo Strategist](marketing/marketing-weibo-strategist.md) | Weibo, trending |
| [AI Citation Strategist](marketing/marketing-ai-citation-strategist.md) | AEO/GEO, visibilité IA |
| [China Market Localization](marketing/marketing-china-market-localization-strategist.md) | GTM Chine |
| [Video Optimization Specialist](marketing/marketing-video-optimization-specialist.md) | YouTube algorithm, retention |

### Product (5)

| Agent | Spécialité |
|---|---|
| [Sprint Prioritizer](product/product-sprint-prioritizer.md) | Agile, prio features |
| [Trend Researcher](product/product-trend-researcher.md) | Marché, concurrence |
| [Feedback Synthesizer](product/product-feedback-synthesizer.md) | Synthèse user feedback |
| [Behavioral Nudge Engine](product/product-behavioral-nudge-engine.md) | Psycho comportementale |
| [Product Manager](product/product-manager.md) | PRD, roadmap, GTM, outcomes |

### Project Management (6)

| Agent | Spécialité |
|---|---|
| [Studio Producer](project-management/project-management-studio-producer.md) | Orchestration portfolio |
| [Project Shepherd](project-management/project-management-project-shepherd.md) | Cross-functional, timelines |
| [Studio Operations](project-management/project-management-studio-operations.md) | Day-to-day, process |
| [Experiment Tracker](project-management/project-management-experiment-tracker.md) | A/B tests, hypothèses |
| [Senior Project Manager](project-management/project-manager-senior.md) | Scoping, conversion tâches |
| [Jira Workflow Steward](project-management/project-management-jira-workflow-steward.md) | Git/Jira discipline |

### Testing (8)

| Agent | Spécialité |
|---|---|
| [Evidence Collector](testing/testing-evidence-collector.md) | QA screenshots, preuve visuelle |
| [Reality Checker](testing/testing-reality-checker.md) | Certification evidence-based |
| [Test Results Analyzer](testing/testing-test-results-analyzer.md) | Évaluation, métriques |
| [Performance Benchmarker](testing/testing-performance-benchmarker.md) | Performance, load testing |
| [API Tester](testing/testing-api-tester.md) | Validation API, intégration |
| [Tool Evaluator](testing/testing-tool-evaluator.md) | Évaluation tech, choix d'outils |
| [Workflow Optimizer](testing/testing-workflow-optimizer.md) | Process, automation |
| [Accessibility Auditor](testing/testing-accessibility-auditor.md) | WCAG, assistive tech |

### Support (6)

| Agent | Spécialité |
|---|---|
| [Support Responder](support/support-support-responder.md) | Service client, issues |
| [Analytics Reporter](support/support-analytics-reporter.md) | Dashboards, KPI |
| [Finance Tracker](support/support-finance-tracker.md) | Planning financier, budget |
| [Infrastructure Maintainer](support/support-infrastructure-maintainer.md) | Reliability, monitoring |
| [Legal Compliance Checker](support/support-legal-compliance-checker.md) | Compliance, régulation |
| [Executive Summary Generator](support/support-executive-summary-generator.md) | Comm C-suite |

### Spatial Computing (6)

| Agent | Spécialité |
|---|---|
| [XR Interface Architect](spatial-computing/xr-interface-architect.md) | Spatial UX, AR/VR/XR |
| [macOS Spatial/Metal Engineer](spatial-computing/macos-spatial-metal-engineer.md) | Swift, Metal, 3D perf |
| [XR Immersive Developer](spatial-computing/xr-immersive-developer.md) | WebXR |
| [XR Cockpit Interaction Specialist](spatial-computing/xr-cockpit-interaction-specialist.md) | Cockpit controls |
| [visionOS Spatial Engineer](spatial-computing/visionos-spatial-engineer.md) | Vision Pro natif |
| [Terminal Integration Specialist](spatial-computing/terminal-integration-specialist.md) | CLI, dev tools |

### Specialized (40)

| Agent | Spécialité |
|---|---|
| [Agents Orchestrator](specialized/agents-orchestrator.md) | Coordination multi-agents |
| [Conductor Prime](specialized/specialized-conductor-prime.md) | Meta-orchestrateur hiérarchique pour runbooks longs |
| [Objective Decomposer](specialized/specialized-objective-decomposer.md) | Décompose un objectif en arbre de sous-tâches actionables |
| [LSP/Index Engineer](specialized/lsp-index-engineer.md) | LSP, code intelligence |
| [Sales Data Extraction](specialized/sales-data-extraction-agent.md) | Excel, métriques sales |
| [Data Consolidation](specialized/data-consolidation-agent.md) | Agrégation sales |
| [Report Distribution](specialized/report-distribution-agent.md) | Livraison rapports auto |
| [Agentic Identity & Trust](specialized/agentic-identity-trust.md) | Identité agents, auth |
| [Identity Graph Operator](specialized/identity-graph-operator.md) | Résolution d'identité |
| [Accounts Payable](specialized/accounts-payable-agent.md) | Paiements crypto/fiat |
| [Blockchain Security Auditor](specialized/blockchain-security-auditor.md) | Audits smart contracts |
| [Compliance Auditor](specialized/compliance-auditor.md) | SOC 2, ISO, HIPAA, PCI |
| [Cultural Intelligence Strategist](specialized/specialized-cultural-intelligence-strategist.md) | UX global, représentation |
| [Developer Advocate](specialized/specialized-developer-advocate.md) | Community, DX |
| [Model QA Specialist](specialized/specialized-model-qa.md) | QA ML, interprétabilité |
| [ZK Steward](specialized/zk-steward.md) | Zettelkasten, knowledge |
| [MCP Builder](specialized/specialized-mcp-builder.md) | Model Context Protocol |
| [Document Generator](specialized/specialized-document-generator.md) | PDF, PPTX, DOCX, XLSX |
| [Automation Governance Architect](specialized/automation-governance-architect.md) | n8n, governance |
| [Corporate Training Designer](specialized/corporate-training-designer.md) | Curricula entreprise |
| [Government Digital Presales](specialized/government-digital-presales-consultant.md) | ToG Chine |
| [Healthcare Marketing Compliance](specialized/healthcare-marketing-compliance.md) | Pub santé Chine |
| [Recruitment Specialist](specialized/recruitment-specialist.md) | Talent, hiring ops |
| [Study Abroad Advisor](specialized/study-abroad-advisor.md) | Études internationales |
| [Supply Chain Strategist](specialized/supply-chain-strategist.md) | Procurement, supply chain |
| [Workflow Architect](specialized/specialized-workflow-architect.md) | Workflow mapping |
| [Salesforce Architect](specialized/specialized-salesforce-architect.md) | Multi-cloud SF |
| [French Consulting Market Navigator](specialized/specialized-french-consulting-market.md) | ESN/SI, portage |
| [Korean Business Navigator](specialized/specialized-korean-business-navigator.md) | Culture business KR |
| [Civil Engineer](specialized/specialized-civil-engineer.md) | Structures, géotech |
| [Customer Service](specialized/customer-service.md) | Omnichannel, rétention |
| [Healthcare Customer Service](specialized/healthcare-customer-service.md) | HIPAA, patients |
| [Hospitality Guest Services](specialized/hospitality-guest-services.md) | Réservations, concierge |
| [HR Onboarding](specialized/hr-onboarding.md) | Pre-boarding, 30-60-90 |
| [Language Translator](specialized/language-translator.md) | Espagnol↔Anglais |
| [Legal Billing & Time Tracking](specialized/legal-billing-time-tracking.md) | IOLTA, collections |
| [Legal Client Intake](specialized/legal-client-intake.md) | Prospect qualification |
| [Legal Document Review](specialized/legal-document-review.md) | Contracts, risk |
| [Loan Officer Assistant](specialized/loan-officer-assistant.md) | TRID, pipeline |
| [Real Estate Buyer & Seller](specialized/real-estate-buyer-seller.md) | Transactions résidentielles |
| [Retail Customer Returns](specialized/retail-customer-returns.md) | Returns, exchanges |
| [Chief of Staff](specialized/specialized-chief-of-staff.md) | Cabinet de direction |

### Finance (5)

| Agent | Spécialité |
|---|---|
| [Bookkeeper & Controller](finance/finance-bookkeeper-controller.md) | Clôture, GAAP, controls |
| [Financial Analyst](finance/finance-financial-analyst.md) | Modélisation, forecasting |
| [FP&A Analyst](finance/finance-fpa-analyst.md) | Budget, variance, MBR |
| [Investment Researcher](finance/finance-investment-researcher.md) | Due diligence, valuation |
| [Tax Strategist](finance/finance-tax-strategist.md) | Optimisation fiscale, multi-juridiction |

### Game Development (16)

**Engine-agnostic**

| Agent | Spécialité |
|---|---|
| [Game Designer](game-development/game-designer.md) | Systèmes, GDD, économie |
| [Level Designer](game-development/level-designer.md) | Layout, pacing, encounters |
| [Technical Artist](game-development/technical-artist.md) | Shaders, VFX, LOD |
| [Game Audio Engineer](game-development/game-audio-engineer.md) | FMOD/Wwise, adaptive music |
| [Narrative Designer](game-development/narrative-designer.md) | Story systems, dialogue |

**Unity**

| Agent | Spécialité |
|---|---|
| [Unity Architect](game-development/unity/unity-architect.md) | ScriptableObjects, DOTS/ECS |
| [Unity Shader Graph Artist](game-development/unity/unity-shader-graph-artist.md) | Shader Graph, HLSL, URP/HDRP |
| [Unity Multiplayer Engineer](game-development/unity/unity-multiplayer-engineer.md) | Netcode, Relay/Lobby |
| [Unity Editor Tool Developer](game-development/unity/unity-editor-tool-developer.md) | EditorWindows, build validation |

**Unreal Engine**

| Agent | Spécialité |
|---|---|
| [Unreal Systems Engineer](game-development/unreal-engine/unreal-systems-engineer.md) | C++/Blueprint, GAS, Nanite |
| [Unreal Technical Artist](game-development/unreal-engine/unreal-technical-artist.md) | Material Editor, Niagara, PCG |
| [Unreal Multiplayer Architect](game-development/unreal-engine/unreal-multiplayer-architect.md) | Actor replication, dedicated server |
| [Unreal World Builder](game-development/unreal-engine/unreal-world-builder.md) | World Partition, HLOD, LWC |

**Godot**

| Agent | Spécialité |
|---|---|
| [Godot Gameplay Scripter](game-development/godot/godot-gameplay-scripter.md) | GDScript 2.0, signals |
| [Godot Multiplayer Engineer](game-development/godot/godot-multiplayer-engineer.md) | MultiplayerAPI, ENet/WebRTC |
| [Godot Shader Developer](game-development/godot/godot-shader-developer.md) | Shading language, VisualShader |

**Blender**

| Agent | Spécialité |
|---|---|
| [Blender Addon Engineer](game-development/blender/blender-addon-engineer.md) | bpy, opérateurs custom, exporters |

**Roblox Studio**

| Agent | Spécialité |
|---|---|
| [Roblox Systems Scripter](game-development/roblox-studio/roblox-systems-scripter.md) | Luau, RemoteEvents, DataStore |
| [Roblox Experience Designer](game-development/roblox-studio/roblox-experience-designer.md) | Engagement loops, monétisation |
| [Roblox Avatar Creator](game-development/roblox-studio/roblox-avatar-creator.md) | UGC pipeline, accessory rigging |

### Academic (5)

| Agent | Spécialité |
|---|---|
| [Anthropologist](academic/academic-anthropologist.md) | Cultures, rituels, kinship |
| [Geographer](academic/academic-geographer.md) | Géographie physique/humaine, climat |
| [Historian](academic/academic-historian.md) | Périodisation, culture matérielle |
| [Narratologist](academic/academic-narratologist.md) | Théorie narrative, structure |
| [Psychologist](academic/academic-psychologist.md) | Personnalité, motivation, cognition |

---

## Cas d'usage type

### Nouveau MVP (Squad **builder**)
```
/squad builder
/orchestrate runbook-mvp
```
Active : frontend-developer, backend-architect, rapid-prototyper, software-architect, code-reviewer, sre, database-optimizer, security-engineer, technical-writer, git-workflow-master, ai-engineer, devops-automator, minimal-change-engineer, agents-orchestrator, conductor-prime, reality-checker.
Conductor enchaîne : Discovery → Architecture → Build (boucle Dev↔QA) → Hardening → Launch.

### Pipeline audio / STT (Squad **voice**)
```
/squad voice
```
Active : voice-ai-integration-engineer, email-intelligence-engineer, ai-data-remediation-engineer, ai-engineer, mcp-builder.

### Lancement contenu (Squad **creator** + **shipper**)
```
/squad creator
/orchestrate runbook-contenu
```
Conductor enchaîne : Trend Researcher → Content Creator → LinkedIn Content Creator → Video Optimization → Analytics Reporter.

### Recherche / discovery (Squad **researcher**)
```
/squad researcher
```
Active : trend-researcher, feedback-synthesizer, investment-researcher, anthropologist, historian, narratologist, ux-researcher, objective-decomposer, model-qa-specialist, workflow-architect.

### Build rigoureux d'un module (Squad **builder** + `runbook-cinq-phases`)
```
/squad builder
/orchestrate runbook-cinq-phases
```
Conductor enchaîne : Spécification → Pseudocode → Architecture → Affinage (boucle Dev↔QA) → Finition.

### Incident production (`runbook-incident`)
```
/orchestrate runbook-incident
```
Conductor active : incident-response-commander → sre → infrastructure-maintainer → technical-writer (post-mortem).

---

## Ajouter un agent au catalogue

1. Choisir la division (`engineering/`, `marketing/`, etc.)
2. Créer `division-slug-nom-agent.md`
3. Frontmatter requis :
   ```markdown
   ---
   name: Nom de l'Agent
   description: Phrase une-ligne sur l'expertise.
   color: cyan
   emoji: 🛠
   vibe: Phrase punchy sur l'attitude.
   ---
   ```
4. Sections : Identité & mémoire, Mission, Règles critiques, Livrables techniques (avec code), Workflow, Métriques de succès, Style de communication
5. L'ajouter au squad pertinent dans `../squads/<squad>.yml`
6. Mettre à jour ce README

---

## Intégrations multi-outils

Le catalogue est nativement compatible Claude Code. Pour les autres outils, des scripts de conversion existent dans `scripts/`.

| Outil | Cible install |
|---|---|
| Claude Code | `~/.claude/agents/` (ou `.claude/agents/` projet-scope) |
| GitHub Copilot | `~/.github/agents/` + `~/.copilot/agents/` |
| Antigravity (Gemini) | `~/.gemini/antigravity/skills/` |
| Gemini CLI | `~/.gemini/extensions/` |
| OpenCode | `.opencode/agents/` |
| Cursor | `.cursor/rules/` (`.mdc`) |
| Aider | `CONVENTIONS.md` |
| Windsurf | `.windsurfrules` |
| OpenClaw | `~/.openclaw/` |
| Qwen Code | `~/.qwen/agents/` |
| Kimi Code | `~/.config/kimi/agents/` |

```bash
# Convertir tous les outils
./scripts/convert.sh

# Installer (interactif, auto-détection)
./scripts/install.sh

# Outil ciblé
./scripts/install.sh --tool claude-code
```

**Note Kopern-OS** : utilise plutôt `/squad <nom>` qui gère les symlinks dans `.claude/agents/`. Les scripts d'install sont là pour propager le catalogue à d'autres outils que Claude Code.

---

## Stats

- **224 agents** dans **14 divisions techniques**
- Organisés en **8 squads** activables
- Orchestrés par **Kopern Conductor** (7 phases, 5 runbooks dont SPARC `runbook-cinq-phases`)
- 100% compatible Claude Code (natif)
- Compatible 10 autres outils via scripts

---

## Lien avec ton AIOS

Le catalogue se branche sur les skills Kopern-OS existantes :

- **`/onboard`** — au setup initial, scaffold le squad par défaut selon Q1 (offer/ICP) et Q7 (corvée)
- **`/audit`** — la dimension *Capabilities* du 4C mesure la fraîcheur des squads actives et la couverture du catalogue
- **`/level-up`** — quand l'interview 3Ms détecte une corvée récurrente, propose un agent du catalogue capable de l'automatiser

Les décisions d'activation/désactivation de squad sont loggées dans `../decisions/log.md`.

---

## Licence

MIT. Catalogue d'origine sous licence MIT, adapté et restructuré pour Kopern-OS.
