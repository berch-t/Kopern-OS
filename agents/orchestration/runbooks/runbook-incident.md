# Runbook — Incident

> **Objectif** : restaurer le service le plus vite possible, comprendre la cause, écrire un post-mortem.
> **Squad** : `builder` (ou `operator` si incident admin/finance/légal).
> **Mode** : Conductor-Micro (heures).
> **Durée cible** : MTTR < 1h pour P1, < 4h pour P0 si non-critique.

---

## Phases

### Phase 0 — Triage (5-15 min)

**Agent lead** : `engineering-incident-response-commander`

- Sévérité : P0 (prod down), P1 (dégradation), P2 (bug visible non bloquant), P3 (cosmétique)
- Périmètre : qui est affecté, quoi est cassé
- Décision : escalade ou pas, communication ou pas

**Quality gate** : si P0/P1, freeze tout autre travail. Si P2/P3, planifier.

### Phase 1 — Investigation (15-60 min)

**Agents** : `engineering-incident-response-commander`, `engineering-sre`, `engineering-codebase-onboarding-engineer` (si zone du code inconnue)

- Hypothèse principale
- Logs, métriques, état système
- Reproduction si possible

**Iron Law** : pas de fix sans cause racine. Aucun "ça marche encore une fois, je sais pas pourquoi".

### Phase 2 — Mitigation (15-30 min)

**Agents** : `engineering-incident-response-commander`, `engineering-sre`, agent spécialisé selon zone

- Rollback ou patch
- Vérifier que le service répond
- Ne PAS toucher git config / push --force / no-verify sauf urgence absolue

### Phase 3 — Récupération (30 min - 2h)

**Agents** : `engineering-sre`, `support-infrastructure-maintainer`

- Restauration complète
- Monitoring rétabli
- Backups vérifiés

### Phase 4 — Post-mortem (1-2h, dans les 48h)

**Agents** : `engineering-incident-response-commander`, `engineering-technical-writer`

- Timeline factuelle
- Cause racine (5 whys)
- Ce qui a marché / pas marché
- Actions correctives avec owner + date
- Sauvegarde dans `decisions/log.md` (ou équivalent projet) avec lien vers `references/incidents/<incident-slug>.md` si tu veux archiver les détails

---

## Adaptations

- **Incident purement infra (pas code)** : `/squad operator` + ce runbook, lead `support-infrastructure-maintainer`.
- **Incident sécurité (data breach, secret leak)** : ajouter `engineering-security-engineer` + `engineering-threat-detection-engineer` en Phase 1, alerter compliance-auditor.
- **Incident IA (modèle hallucine, dérive)** : `specialized-model-qa` en lead Phase 1.
- **Incident infrastructure locale (Docker, WSL2, dev env)** : si un pattern récurrent émerge, archive le détail technique dans `references/incidents/<slug>.md` et référence-le ici pour la prochaine fois.

## Garder une mémoire d'incidents

`references/incidents/` est l'endroit où archiver les playbooks d'incidents spécifiques (config locale, conflits réseau, dette infra). Pas livré dans le kit — à créer au besoin.
