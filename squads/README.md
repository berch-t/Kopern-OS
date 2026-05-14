# Squads — bundles d'agents activables

Chaque fichier `.yml` définit un **Squad** : un scope de travail composé de 5-15 agents du catalogue `../agents/`. Un seul Squad est actif à la fois (symlinks dans `../.claude/agents/`).

## Squads disponibles

| Fichier | Squad | Pour quoi | Cas d'usage type |
|---|---|---|---|
| `builder.yml` | **builder** | Coder de zéro à la prod | MVP, feature complexe, hardening |
| `shipper.yml` | **shipper** | GTM, acquisition, métriques | Lancement public, growth, mesure |
| `researcher.yml` | **researcher** | Discovery, synthèse | Comprendre avant de coder |
| `operator.yml` | **operator** | Admin/finance/légal solo | Ops transversales |
| `creator.yml` | **creator** | Contenu social / YouTube / article | Posts, vidéos, ebooks |
| `spatial.yml` | **spatial** | XR, visionOS, Metal | Expérience immersive, AR/VR |
| `voice.yml` | **voice** | Pipelines audio, STT | Transcription, email intel |
| `game.yml` | **game** | Moteurs (Unity, Unreal, Godot…) | Side-project ou prototype |

## Utilisation

```
/squad list                  # liste les squads
/squad <nom>                 # active un squad
/squad current               # affiche le squad actif
/squad clear                 # désactive (vide .claude/agents/)
/roster <besoin>             # cherche un agent dans le catalogue et l'ajoute au scope
/orchestrate <runbook>       # lance un workflow Conductor avec le squad courant
```

## Personnalisation

Les `projets_phares:` de chaque YAML contiennent des placeholders `{{...}}`. Édite-les pour matcher tes propres projets. `/onboard` peut le faire pour toi en lisant `aios-intake.md`.

## Format d'un squad

```yaml
name: <slug>
pitch: |
  Description courte du scope.

projets_phares:
  - "{{Nom de ton projet}}"

agents:
  - division/nom-fichier.md     # chemin relatif depuis agents/

runbooks_compatibles:
  - runbook-xxx

exemples_usage:
  - "Phrase d'exemple"
```

## Ajouter un squad

1. Crée `mon-squad.yml` ici, structure ci-dessus.
2. Mets à jour ce README (tableau).
3. Update `agents/README.md` (section "Les 8 Squads" → "Les N Squads").
4. Si nouveau runbook requis, ajoute-le dans `../agents/orchestration/runbooks/`.
