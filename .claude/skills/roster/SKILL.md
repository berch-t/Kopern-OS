---
name: roster
description: Cherche un agent dans le catalogue Kopern-OS par besoin, et l'ajoute au scope actif. Trigger : "j'ai besoin de quelqu'un pour X", "trouve-moi un agent pour Y", "/roster <besoin>". Le catalogue contient 222 agents dans 14 divisions. Ne change pas la squad courante — augmente juste.
---

## Ce que fait ce skill

Recherche dans `agents/**/*.md` un agent qui matche un besoin précis. Affiche les 3 meilleurs candidats. Propose d'ajouter le choisi au scope actif (symlink dans `.claude/agents/`) sans modifier la squad courante.

## Quand l'utiliser

- "J'ai besoin de quelqu'un pour <X>"
- "Y a-t-il un agent qui fait <Y>"
- "/roster <besoin>"
- Pendant un runbook quand un agent ad-hoc est requis

## Sous-commandes

### `/roster <besoin libre>`

1. Parse le besoin (mots-clés, intent).
2. `grep -ril` sur `agents/**/*.md` matchant les mots-clés dans la frontmatter `description:` et le corps.
3. Score : poids fort sur frontmatter, poids moyen sur les sections "Mission" et "Specialty", poids faible sur tout le corps.
4. Affiche les 3 meilleurs candidats :

   ```
   1. <Nom Agent>  [<division>/<fichier>.md]
      Description : <ligne frontmatter>
      Match : <mots-clés trouvés>
      Squads où il apparaît : <liste>

   2. ...
   ```

5. Demande : "Lequel ajouter au scope actif ? (1/2/3/aucun)"
6. Si choix : `ln -sf agents/<chemin> .claude/agents/roster-<basename>`. Préfixe `roster-` pour le distinguer des agents de la squad.
7. Logge dans `decisions/log.md` : `YYYY-MM-DD : Agent ajouté (roster) → <nom> pour besoin "<besoin>"`.

### `/roster remove <nom>`

Retire un agent ajouté ad-hoc (préfixe `roster-`). Ne touche pas aux agents du squad.

### `/roster show`

Liste les agents `roster-*` actuellement dans `.claude/agents/` (agents ad-hoc en surcharge du squad).

## Heuristiques de recherche

- Division par défaut suggérée selon le besoin :
  - "code", "API", "frontend", "backend", "deploy" → `engineering/`
  - "design", "UI", "UX" → `design/`
  - "post", "contenu", "LinkedIn" → `marketing/`
  - "ads", "PPC", "Google Ads" → `paid-media/`
  - "deal", "outbound", "discovery call" → `sales/`
  - "test", "QA", "audit" → `testing/`
  - "finance", "fisca", "comptable" → `finance/`
  - "incident", "outage", "post-mortem" → `engineering/` (incident-response-commander)
  - "audio", "STT", "transcription" → `voice` squad (et `engineering/`)
  - "XR", "VR", "Vision Pro" → `spatial-computing/`
  - "Unity", "Unreal", "Godot", "Roblox" → `game-development/`

## Notes d'implémentation

- Si le besoin est très vague ("aide", "support"), demande à l'user de préciser plutôt que retourner du bruit.
- Si aucun match > seuil, propose : "Aucun agent ne matche fortement. Veux-tu (a) reformuler, (b) lister tous les agents d'une division, (c) créer un nouvel agent ?"
- Si l'user enchaîne plusieurs `/roster`, suggère après 3 ajouts : "Tu as ajouté 3 agents hors squad. Veux-tu créer une **nouvelle squad** combinant ceux-ci ?"

## Lien avec les autres skills

- Complète `/squad` (qui charge un bundle prédéfini).
- Détecté par `/level-up` : si un agent ad-hoc est ajouté 3+ semaines de suite, propose de l'intégrer au squad correspondant.
