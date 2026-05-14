---
name: orchestrate
description: Lance un workflow Kopern Conductor (runbook multi-agents) avec la squad courante. Trigger : "lance le runbook X", "orchestre un MVP", "/orchestrate <runbook>". Les runbooks vivent dans `agents/orchestration/runbooks/`. Sans argument, liste les runbooks disponibles.
---

## Ce que fait ce skill

Active un workflow multi-agents pré-câblé du **Kopern Conductor**. Chaque runbook enchaîne plusieurs agents selon les 7 phases de la doctrine (Discovery → Strategy → Foundation → Build → Hardening → Launch → Operate), avec handoffs structurés et quality gates.

## Quand l'utiliser

- L'user lance un MVP : "/orchestrate runbook-mvp"
- L'user veut un cycle de contenu : "/orchestrate runbook-contenu"
- L'user gère un incident : "/orchestrate runbook-incident"
- L'user ajoute une feature : "/orchestrate runbook-feature"
- L'user demande "quels runbooks ?" → liste.

## Préalable

Une **squad doit être active** (`/squad <nom>` avant). Si `.claude/agents/` est vide :

> "Aucune squad active. Active d'abord : `/squad builder` (pour mvp/feature/incident) ou `/squad creator` (pour contenu). Puis relance `/orchestrate`."

## Sous-commandes

### `/orchestrate` (sans argument) ou `/orchestrate list`

Lit `agents/orchestration/runbooks/`. Affiche :

| Runbook | Pour quoi | Squads compatibles | Phases impliquées |
|---|---|---|---|
| runbook-mvp | MVP de zéro à launch | builder | 0→5 |
| runbook-contenu | Cycle éditorial | creator, shipper | 1, 3, 5 |
| runbook-incident | P0/P1 incident | builder, operator | 6 (operate) |
| runbook-feature | Ajout feature à un produit existant | builder, shipper | 2→4 |

### `/orchestrate <runbook>`

1. Vérifie `agents/orchestration/runbooks/<runbook>.md` existe.
2. Vérifie squad active. Si incompatible avec le runbook, alerte (laisse l'user décider).
3. Lit le runbook. Affiche :
   - Nom du runbook
   - Objectif
   - Phases et agents impliqués (séquence)
   - Quality gates
   - Durée estimée (heures/jours pas semaines — solo builder)
4. Demande : "Go ? (oui/personnaliser/annuler)"
5. Si oui : démarre l'exécution séquentielle, appelle les agents un par un, applique handoff templates (`agents/orchestration/coordination/handoff-templates.md`).
6. Logge chaque transition dans `decisions/log.md`.
7. À la fin : récap, sortie finale, statut quality gates.

## Modes Conductor

- **Conductor-Full** — toutes les phases (cycle produit complet, semaines)
- **Conductor-Sprint** — phases ciblées (feature/MVP, jours)
- **Conductor-Micro** — tâche unique (heures)

Par défaut, Conductor-Sprint. L'user peut demander : "`/orchestrate runbook-mvp --mode full`".

## Notes d'implémentation

- Si la doctrine `agents/orchestration/conductor-doctrine.md` parle d'équipes humaines, l'adapter mentalement : Kopern-OS est solo-builder, donc "Engineering Lead" = toi en mode software-architect.
- Les boucles Dev↔QA avec retry max 3 sont préservées : si l'agent reality-checker dit NEEDS-WORK trois fois, escalade à l'user.
- Les runbooks sont **adaptables** : l'user peut sauter une phase ou en ajouter une via `/orchestrate <runbook> --skip phase-1`.

## Lien avec les autres skills

- Pré-requis : `/squad <nom>`
- `/roster` peut être appelé pendant un runbook si un agent ad-hoc est requis.
- À la fin du runbook, suggère `/level-up` pour capturer les corvées identifiées.
