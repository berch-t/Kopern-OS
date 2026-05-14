# Runbook — MVP

> **Objectif** : passer d'une idée à un produit utilisable en prod en quelques jours.
> **Squad** : `builder` (obligatoire). Optionnel : `researcher` en pré-phase.
> **Mode** : Conductor-Sprint par défaut.
> **Durée** : 3-7 jours pour un MVP solo, selon scope.

---

## Phases (compressées solo-builder)

### Jour 0 — Discovery (2-4h)

**Agents** : `product-trend-researcher`, `product-feedback-synthesizer`, `specialized-workflow-architect`

- Cadrer le problème en une phrase
- Identifier le wedge le plus étroit (cf. office-hours)
- Mapper les workflows utilisateur cibles

**Sortie** : `decisions/log.md` — décision "scope MVP" avec ce qui est IN / OUT.

### Jour 1 — Architecture (3-5h)

**Agents** : `engineering-software-architect`, `engineering-backend-architect`

- Stack choisie (cf. `context/tech-stack.md` côté vault)
- Schéma de BDD initial
- Diagramme des modules principaux
- Décision sur l'auth, le déploiement, le CI

**Quality gate** : pas de coding avant que l'archi tienne en 1 page lisible.

### Jour 2-3 — Build (boucle Dev↔QA)

**Agents** : `engineering-frontend-developer`, `engineering-backend-architect`, `engineering-rapid-prototyper`, `engineering-ai-engineer` (si IA), `engineering-database-optimizer`

Boucle pour chaque feature critique :
1. `rapid-prototyper` ou `frontend/backend developer` code.
2. `testing-reality-checker` valide. Si NEEDS-WORK → retry max 3.
3. `engineering-code-reviewer` audite.

**Quality gate** : 100% des features critiques passent reality-checker avant Hardening.

### Jour 4 — Hardening (3-4h)

**Agents** : `engineering-security-engineer`, `engineering-sre`, `engineering-database-optimizer`

- Threat model rapide (OWASP top 10 ciblé)
- SLO de base (uptime, latence)
- Index BDD, requêtes lentes

### Jour 5 — Launch (2-3h)

**Agents** : `engineering-devops-automator`, `engineering-technical-writer`, `engineering-git-workflow-master`

- Deploy script reproductible
- README utilisateur minimal
- Tag v0.1.0 (commit manuel, jamais auto — règle Kopern-OS par défaut)

**Quality gate final** : `testing-reality-checker` → PASS / NEEDS-WORK avant annonce publique.

---

## Quand utiliser ce runbook

- Nouveau produit en V1
- Outil exploitable de zéro
- Side-project ou prototype rapide

## Quand NE PAS l'utiliser

- Feature dans un produit existant → `runbook-feature`
- Refonte d'archi → cycle Conductor-Full (semaines)
- Recherche pure sans livrable → `/squad researcher` sans runbook

## Adaptations courantes

- **MVP très court (< 2 jours)** : sauter Hardening, faire un mini-pass sécurité dans Build.
- **MVP IA-first** : ajouter `engineering-ai-engineer` en lead Phase 2-3, ajouter `specialized-model-qa` en Quality gate.
- **MVP voice** : switcher vers `/squad voice`, garder ce runbook.
