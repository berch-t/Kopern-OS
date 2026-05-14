# Runbooks Kopern Conductor

Quatre runbooks adaptés solo-builder, en FR, calés sur les projets réels.

| Runbook | Pour quoi | Durée typique | Squad recommandée |
|---|---|---|---|
| [runbook-mvp](runbook-mvp.md) | Zéro à prod | 3-7 jours | `builder` |
| [runbook-contenu](runbook-contenu.md) | Cycle éditorial | 2h - 1 semaine | `creator` |
| [runbook-incident](runbook-incident.md) | P0/P1 production | heures | `builder` ou `operator` |
| [runbook-feature](runbook-feature.md) | Ajout feature | 1-3 jours | `builder` ou `shipper` |
| [runbook-cinq-phases](runbook-cinq-phases.md) | Build rigoureux d'un module (Spec → Pseudocode → Archi → Affinage → Finition) | 1-5 jours | `builder` |

Les anciens runbooks "scenario-*" (anglais, équipe humaine) sont conservés dans ce dossier pour référence, mais le défaut Kopern-OS est ces 4 runbooks FR ci-dessus.

## Lancer un runbook

```
/squad <nom>           # active la squad recommandée
/orchestrate <runbook> # lance le workflow
```

Exemple :
```
/squad builder
/orchestrate runbook-mvp
```
