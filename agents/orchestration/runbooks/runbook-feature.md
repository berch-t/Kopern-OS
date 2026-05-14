# Runbook — Feature

> **Objectif** : ajouter une feature à un produit existant, sans casser l'existant.
> **Squad** : `builder` ou `shipper` selon nature.
> **Mode** : Conductor-Sprint.
> **Durée** : 1-3 jours pour une feature solo-builder normale.

---

## Phases

### Phase 0 — Spec (30 min - 2h)

**Agents** : `product-manager`, `product-sprint-prioritizer`, `specialized-workflow-architect`

- Quel problème utilisateur résout cette feature ?
- Quel comportement attendu (acceptance criteria) ?
- Quel impact sur l'existant (compat ascendante, migration data) ?

**Sortie** : un mini-PRD en 1 page, archivé dans `projects/<projet>/roadmap.md` côté vault.

### Phase 1 — Design (1-3h, optionnel)

**Agents** : `design-ui-designer`, `design-ux-architect` (si UI complexe)

- Maquette ou wireframe
- Cohérence design system
- Edge cases UI

### Phase 2 — Architecture (30 min - 2h)

**Agents** : `engineering-software-architect`, `engineering-backend-architect`, `engineering-database-optimizer` (si schéma touché)

- Impact sur l'archi
- Migration data si besoin
- Plan de rollout (feature flag, canary)

### Phase 3 — Build (boucle Dev↔QA, 4h - 2j)

**Agents lead** : `engineering-minimal-change-engineer`, `engineering-frontend-developer`, `engineering-backend-architect`

Règle Kopern-OS : **changement minimal**. Pas de refacto opportuniste, pas d'abstraction prématurée, pas de fallback pour des cas qui n'arrivent pas.

Boucle :
1. Implémenter la feature ciblée
2. `testing-reality-checker` valide
3. `engineering-code-reviewer` audite
4. Si NEEDS-WORK → retry max 3

### Phase 4 — QA + Hardening (1-3h)

**Agents** : `testing-reality-checker`, `engineering-security-engineer` (si surface attaque change), `testing-accessibility-auditor` (si UI)

- Tests sur les golden path + edge cases
- Vérification que rien d'autre n'est cassé (regression check manuel ou auto)

### Phase 5 — Ship (1h)

**Agents** : `engineering-devops-automator`, `engineering-git-workflow-master`, `engineering-technical-writer`

- Commit propre (un commit = un changement logique)
- Mise à jour du changelog
- Doc utilisateur si user-facing
- Tag de version si applicable

**Règle Kopern-OS par défaut** : pas de commit/push auto. Je propose le message, tu commit.

### Phase 6 — Annonce (optionnel)

Bascule sur `/squad shipper` + `runbook-contenu` pour annoncer publiquement.

---

## Adaptations

- **Feature bug fix uniquement** : sauter Phase 0-1, démarrer Phase 2 rapide puis Build.
- **Feature avec migration data risquée** : ajouter une mini-Phase "Migration dry-run en staging" entre 3 et 4.
- **Feature touche prod existante critique** : `/squad operator` en parallèle pour double-check compliance (selon nature).
