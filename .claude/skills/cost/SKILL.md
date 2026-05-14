---
name: cost
description: Suivi de la consommation LLM (Anthropic, OpenAI) par projet, par squad, par session. Trigger : "combien j'ai dépensé", "coût de cette session", "/cost", "/cost month", "/cost project <nom>". Lit les logs disponibles, calcule, propose un tableau. Aide à décider quand passer en modèle moins cher.
---

## Ce que fait ce skill

Track la facture LLM en cours pour éviter les mauvaises surprises mensuelles. Lit les données de coût disponibles (logs Claude Code, exports Anthropic console, état session courant) et propose un récap actionnable.

**Pas une comptabilité comptable.** C'est un outil de décision : suis-je en train de cramer mon budget IA sur un projet qui ne rapporte pas ?

## Quand l'utiliser

- "Combien j'ai dépensé aujourd'hui / cette semaine / ce mois"
- "Quel projet me coûte le plus"
- "Cette session a coûté quoi"
- Avant de lancer un runbook long ("est-ce que je peux me permettre")
- En fin de mois pour rationaliser

## Sous-commandes

### `/cost` (sans argument)

Récap session courante :
- Tokens input / output estimés
- Modèle utilisé (Opus 4.7 → cher, Sonnet 4.6 → moyen, Haiku 4.5 → cheap)
- Coût approx en USD
- Projection si tu continues 1h / 4h / journée

### `/cost month`

Récap du mois en cours :
- Total approximatif (lu depuis console Anthropic si export dispo dans `references/anthropic-export.csv`)
- Par projet (basé sur `decisions/log.md` et activations de squad logguées)
- Par squad (corrélation projets ↔ squads)
- Comparaison vs mois précédent si historique présent

### `/cost project <nom>`

Récap par projet (les projets que tu as déclarés via `/onboard` ou que tu nommes dans `decisions/log.md`) :
- Tokens consommés ce mois
- Sessions actives
- Coût moyen par session
- Runbooks lancés ce mois sur ce projet

### `/cost squad <nom>`

Récap par squad :
- Combien de sessions ce mois ont utilisé cette squad
- Agents les plus invoqués
- Estimation coût total

## Comment estimer en l'absence d'export Anthropic

Si pas d'export Anthropic dispo :
1. Lire `decisions/log.md` pour le nombre de sessions / activations.
2. Estimer 50k tokens input + 5k tokens output par session de travail moyen avec Opus 4.7.
3. Calcul : Opus 4.7 ≈ $15/M input + $75/M output. Sonnet 4.6 ≈ $3/M + $15/M. Haiku 4.5 ≈ $0.80/M + $4/M.
4. Présenter comme **estimation grossière**, pas comptabilité.

Suggérer à l'user : "Pour des chiffres réels, exporte ta conso depuis console.anthropic.com et place-la dans `references/anthropic-export.csv`."

## Lien avec routage modèles

Si `/cost month` indique > 80% du budget consommé sur Opus 4.7 pour des tâches simples :
- Suggérer la section **Routage modèles** du `CLAUDE.md` racine
- Proposer de basculer les tâches répétitives vers Haiku 4.5
- Lister les 3 tâches récurrentes les plus coûteuses

## Sortie type

```
Coût session (estimation grossière)
───────────────────────────────────
Modèle : Opus 4.7 (1M context)
Input  ~ 45k tokens   →  $0.68
Output ~ 4k tokens    →  $0.30
─────────────────
Total session       ~  $0.98

Projection 4h continue : ~$4
Projection journée 8h  : ~$8
```

```
Coût mois en cours (au 14)
──────────────────────────
Total estimé : ~$95
  Projet A      : ~$42 (12 sessions)
  Projet B      : ~$28 (8 sessions)
  Contenu / éditorial : ~$15 (5 sessions creator)
  Autres        : ~$10
Vs mois -1 : +18%
Recommandation : 3 tâches récurrentes pourraient basculer en Haiku → économie ~$8/mois
```

## Notes

- Le skill ne **stocke pas** de données financières sensibles. Tout est calculé à la volée.
- Aucune connexion automatique à Anthropic Console (privacy). L'user exporte manuellement.
- Logger les recommandations significatives dans `decisions/log.md`.

## Lien avec autres skills

- `/audit` — la dimension Cadence peut tenir compte de la fraîcheur du suivi coût.
- `/level-up` — si une corvée hebdo coûte cher, c'est un candidat à automatiser sur modèle moins cher.
- Section "Routage modèles" du `CLAUDE.md` racine — règles de fallback.
