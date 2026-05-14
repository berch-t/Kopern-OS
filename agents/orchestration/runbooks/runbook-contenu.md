# Runbook — Contenu

> **Objectif** : produire un cycle éditorial cohérent (posts sociaux, YouTube, article, carrousel).
> **Squad** : `creator` (obligatoire). Bonus : `shipper` pour l'amplification.
> **Mode** : Conductor-Sprint ou Micro.
> **Durée** : 2h pour un post, 1 journée pour une série, 1 semaine pour un livre.

**Voix** : les règles d'écriture (langue, ton, accents, ponctuation, em dashes, emojis) viennent de `references/voice.md`. Si ce fichier est vide, lance `/onboard` pour le remplir. Le runbook respecte strictement la voix qui y est définie.

---

## Phases

### Phase 1 — Recherche (15-30 min pour un post, 2h pour une série)

**Agents** : `product-trend-researcher`, `marketing-seo-specialist`, `marketing-ai-citation-strategist`

- Sujet : qu'est-ce qui résonne en ce moment dans ta niche ?
- Angle : qu'est-ce que tu peux dire que personne d'autre ne dit ?
- Mot-clé / question cible

**Sortie** : un brief de 5 lignes.

### Phase 2 — Rédaction / création (30 min - 2h selon format)

| Format | Agent lead |
|---|---|
| Post réseau social | `marketing-linkedin-content-creator` (ou agent réseau spécifique) |
| Article long | `marketing-content-creator` |
| Script YouTube | `marketing-video-optimization-specialist` |
| Carrousel | `marketing-carousel-growth-engine` |
| Épisode podcast | `marketing-podcast-strategist` |
| Livre / ebook | `marketing-book-co-author` |

**Règle dure** : ne JAMAIS publier sous ton nom sans qu'un draft te soit montré d'abord (cf. `references/voice.md`).

### Phase 3 — Visuel (15-45 min)

**Agents** : `design-image-prompt-engineer`, `design-visual-storyteller`, `design-brand-guardian`

- Image principale / thumbnail
- Vérification cohérence brand
- (Optionnel) `design-whimsy-injector` pour une touche perso

### Phase 4 — Optimisation (15 min)

**Agents** : `marketing-seo-specialist`, `marketing-video-optimization-specialist` (YouTube), `marketing-ai-citation-strategist`

- Titre / hook
- Tags / mots-clés
- Citations IA (visibilité ChatGPT, Claude, Perplexity)

### Phase 5 — Mesure (J+7)

**Agents** : `support-analytics-reporter`, `product-feedback-synthesizer`

- Reach, engagement, conversion
- Qu'est-ce qui a marché / pas marché
- Note dans `decisions/log.md`

---

## Quand utiliser ce runbook

- Post réseau social hebdomadaire (Phase 1-4, Micro)
- Lancement d'une série éditoriale (Sprint, série de 5+ posts)
- Création d'un ebook ou cours (Full, semaines)

## Adaptations

- **Post unique** : Phase 1 (10 min) + Phase 2 (agent réseau) + Phase 3 (1 image) + Phase 4 (titre). Pas de Phase 5 systématique, mais reviewer une fois par mois.
- **Vidéo YouTube** : Phase 3 = thumbnail dédié, Phase 4 = chapitres + description SEO, Phase 5 obligatoire (retention dashboard).
- **Article long** : Phase 1 plus poussée (1-2h de recherche), Phase 2 avec book-co-author.
