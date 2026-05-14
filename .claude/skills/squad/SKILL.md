---
name: squad
description: Active, liste, affiche ou efface une Squad du catalogue Kopern-OS. Trigger : "active la squad X", "switch to Y", "quelle squad est active", "/squad <nom>", "/squad list", "/squad current", "/squad clear". Une Squad est un bundle de 5-15 agents du catalogue `agents/` activé via symlinks dans `.claude/agents/`.
---

## Ce que fait ce skill

Gère le scope d'agents actifs. Un seul Squad actif à la fois. Les agents actifs sont des **symlinks** de `agents/<division>/<fichier>.md` vers `.claude/agents/<fichier>.md` (préfixés par le nom du squad pour identification).

## Quand l'utiliser

- L'user veut activer une squad : "active builder", "switch to voice", "/squad shipper"
- L'user demande quel scope est chargé : "quelle squad", "current"
- L'user veut libérer le scope : "/squad clear"
- L'user veut la liste : "/squad list"

## Sous-commandes

### `/squad list`

Lit `squads/*.yml`. Affiche un tableau :

| Squad | Pitch (1 ligne) | Projets | Nb agents |
|---|---|---|---|

### `/squad current`

Affiche les agents actuellement symlinkés dans `.claude/agents/`. Si vide, dis "Aucune squad active. `/squad list` pour voir les options."

```bash
ls .claude/agents/
```

### `/squad <nom>`

1. Vérifie que `squads/<nom>.yml` existe. Sinon : "Squad inconnue. /squad list pour voir les options."
2. Si une autre squad est active, demande confirmation : "Squad **<courant>** active. Switcher vers **<nom>** ?" (clear puis load).
3. Vide `.claude/agents/` (uniquement symlinks créés par ce skill — préserve d'éventuels agents manuels).
4. Parse le YAML, lit la liste `agents:`.
5. Pour chaque agent, crée un symlink :
   ```bash
   ln -sf "$KOPERN_OS_ROOT/agents/<chemin>" .claude/agents/<basename>
   # ou en relatif si tu utilises ln -srf et que tu es à la racine du projet :
   ln -srf agents/<chemin> .claude/agents/<basename>
   ```
6. Logge dans `decisions/log.md` : `YYYY-MM-DD : Squad activée → <nom> (N agents)`.
7. Affiche un récap :
   - Squad : **<nom>**
   - Pitch : <pitch>
   - Projets phares : <liste>
   - Agents chargés (N) : liste compacte
   - Runbooks compatibles : <liste>

### `/squad clear`

1. Supprime tous les symlinks dans `.claude/agents/` (mais pas les fichiers réels).
2. Logge dans `decisions/log.md` : `YYYY-MM-DD : Squad désactivée (était <nom>)`.
3. Affiche "Scope vidé. `/squad <nom>` pour activer une autre squad."

## Notes d'implémentation

- WSL2 : les symlinks Linux fonctionnent sans souci côté Claude Code. Ne pas tenter d'accéder à `.claude/agents/` depuis Cursor Windows.
- Si Claude Code refuse de suivre les symlinks, fallback : copier les fichiers (option `--copy` en sous-commande).
- Le YAML est lu en parsing simple (regex sur `^  - `). Pas besoin de dépendance YAML.
- Le squad **builder** est suggéré par défaut pour un nouveau projet code, **researcher** pour un nouveau projet recherche/exploration.

## Lien avec les autres skills

- Après `/squad <nom>`, suggère `/orchestrate <runbook>` si un runbook est compatible.
- Si l'user décrit un besoin qui ne matche pas la squad active, suggère `/roster <besoin>` pour piocher un agent ad-hoc.
- `/audit` (4C) lit `.claude/agents/` pour mesurer la dimension Capabilities.
