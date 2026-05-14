---
name: snapshot
description: Sauvegarde un état session Kopern-OS (squad active, agents roster ad-hoc, contexte décisions récentes, mémoire courante) pour reprise ultérieure. Trigger : "/snapshot", "/snapshot save", "/snapshot list", "/snapshot restore <id>", "sauvegarde l'état". Complémentaire de /context-save gstack — focalisé Kopern-OS (squads + runbooks).
---

## Ce que fait ce skill

Capture l'état complet de ta session Kopern-OS dans un fichier daté pour pouvoir reprendre exactement où tu en étais — même après plusieurs jours, même sur une autre machine WSL2, même après un reboot Windows forcé par un conflit Docker.

**Différence avec `/context-save` (gstack)** : `/context-save` capture l'état git et décisions de la conversation courante. `/snapshot` capture l'état **Kopern-OS spécifique** : quelle squad, quels agents roster ad-hoc, quel runbook en cours, quelles décisions logguées récentes.

## Sous-commandes

### `/snapshot` ou `/snapshot save`

Crée un nouveau snapshot dans `archives/snapshots/YYYY-MM-DD-HHMM.md` avec :

- Date/heure
- Squad active (lu depuis `.claude/agents/` symlinks)
- Agents roster ad-hoc (les `roster-*`)
- Dernières 10 entrées de `decisions/log.md`
- Liste des 5 mémoires projet les plus récentes (`/home/tonton/.claude/projects/.../memory/`)
- Runbook en cours si détecté (parsing recent decisions)
- Branch git courante + 5 derniers commits
- État du squad selon `squads/<active>.yml`

Format markdown lisible à la main.

### `/snapshot list`

Liste les snapshots existants dans `archives/snapshots/`. Affiche :
- Date
- Squad active à ce moment
- Runbook en cours
- Note libre (si l'user en a ajouté une via `/snapshot save "note"`)

### `/snapshot save "<note>"`

Idem `/snapshot save` mais ajoute une note libre en haut du fichier.

### `/snapshot restore <id-ou-date>`

Reprend l'état d'un snapshot :
1. Active la squad qui était active (équivalent `/squad <nom>`)
2. Ré-ajoute les agents roster ad-hoc qui étaient présents
3. Lit les décisions du snapshot et affiche un récap
4. NE TOUCHE PAS au git (pas de checkout automatique — règle Kopern-OS par défaut)
5. Suggère le runbook en cours si applicable

### `/snapshot diff <id>`

Compare l'état actuel au snapshot. Affiche ce qui a changé : squad, agents ad-hoc, décisions ajoutées, mémoires nouvelles.

## Cas d'usage

- **Avant un reboot ou un risque environnement** : `/snapshot save "avant reboot"`.
- **Fin de journée** : `/snapshot save "EOD"` puis demain `/snapshot restore` pour reprendre direct.
- **Changement de projet** : `/snapshot save "fin sprint projet A"` puis `/squad <autre>` pour projet B.
- **Suite à un incident** : `/snapshot save "avant post-mortem"`.

## Notes

- Les snapshots sont **plain markdown**. Lisibles, commit-ables, archivables.
- Pas de compression, pas de format binaire. Anti-pattern "boîte noire".
- `archives/snapshots/` est créé à la première utilisation. Cleanup manuel quand le dossier dépasse 50 entrées (cf. EXPANSIONS.md cadence archives).

## Lien avec autres skills

- `/context-save` (gstack) — complémentaire, focalisé git+conversation. Lance les deux si tu veux une sauvegarde maximale.
- `/squad current` — l'état que `/snapshot save` capture en partie.
- `/audit` — un repo avec snapshots récents marque des points en dimension Cadence.
