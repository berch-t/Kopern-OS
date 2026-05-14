# Runbook — Cinq Phases (méthode rigoureuse de dev)

> **Objectif** : développer une feature ou un module en évitant les bugs structurels via une décomposition systématique : **Spécification → Pseudocode → Architecture → Affinage → Finition**.
> **Squad** : `builder` (obligatoire).
> **Mode** : Conductor-Sprint.
> **Durée** : 1 jour pour un module, 3-5 jours pour une feature complexe.

Différence avec `runbook-mvp` : ce runbook s'utilise pour la partie **build d'une seule chose** (une feature, un module critique, un endpoint complexe). `runbook-mvp` est le cycle global produit. Tu peux invoquer ce runbook **à l'intérieur** de la phase Build de runbook-mvp pour les modules sensibles.

---

## Phase 1 — Spécification (30 min - 2h)

**Agents lead** : `product-manager`, `specialized-workflow-architect`

**Output attendu** : 1 page max
- Quel problème exact on résout (en 1 phrase utilisateur)
- Inputs / outputs explicites
- Critères d'acceptance vérifiables (testables)
- Edge cases listés (au moins 5)
- Hors-scope explicite (ce qu'on ne fait PAS)

**Quality gate** : si tu ne peux pas écrire un test qui passerait avec cette spec, la spec n'est pas finie.

---

## Phase 2 — Pseudocode (15-45 min)

**Agents lead** : `engineering-software-architect`, ou `engineering-ai-engineer` si logique IA

**Output attendu** : algo en français/pseudo-code, **avant tout vrai code**
- Fonctions principales avec signatures
- Data flow étape par étape
- Branchements / boucles / récursions
- Gestion erreurs et états dégradés

**Why** : 80% des bugs structurels viennent d'algo flou. Mettre le pseudocode sur papier avant le code force la clarté.

**Quality gate** : un autre dev (ou agent `engineering-code-reviewer`) doit pouvoir relire le pseudocode et **prédire le comportement** sans ambiguïté.

---

## Phase 3 — Architecture (30 min - 2h)

**Agents lead** : `engineering-software-architect`, `engineering-backend-architect`, `engineering-database-optimizer` (si data touchée)

**Output attendu** :
- Schéma des modules / classes / fonctions impliqués
- Dépendances internes et externes
- Stockage (BDD, cache, fichiers) avec schéma
- Points d'extension prévus / volontairement absents
- Décisions clés loggées dans `decisions/log.md`

**Quality gate** : tient en 1 page lisible. Si tu as besoin d'une page A3 ou d'un diagramme à 50 nœuds, le scope est trop large.

---

## Phase 4 — Affinage (boucle Dev↔QA, durée variable)

**Agents lead** : `engineering-frontend-developer` / `engineering-backend-architect`, `engineering-minimal-change-engineer`

Boucle pour chaque sous-bloc :
1. Implémenter selon Phase 2 + 3
2. `testing-reality-checker` valide contre Phase 1 (acceptance + edge cases)
3. `engineering-code-reviewer` audite
4. Si NEEDS-WORK → retry max 3

**Règle Kopern-OS** : changement minimal. Pas de refacto opportuniste, pas d'abstraction prématurée pour un futur hypothétique.

**Quality gate** : 100% des critères d'acceptance et edge cases Phase 1 passent.

---

## Phase 5 — Finition (30 min - 2h)

**Agents lead** : `engineering-code-reviewer`, `engineering-technical-writer`, `engineering-git-workflow-master`

**Output** :
- Doc utilisateur courte (README ou commentaire si interne)
- Tests automatisés couvrant golden path + edge cases majeurs
- Commit propre, message clair (proposé par l'agent, validé par toi)
- Update changelog si livré

**Règle Kopern-OS par défaut** : aucun commit/push automatique. L'agent propose le message, tu commit toi-même.

---

## Quand utiliser

- Feature critique d'un produit existant (auth, paiement, pipeline data, API publique)
- Module IA / agent dont le comportement doit être prévisible
- Refonte d'un composant qui fuit
- Sous-bloc d'un MVP qui mérite plus de rigueur que le reste

## Quand NE PAS utiliser

- POC jetable → `runbook-mvp` mode rapide
- Bug fix one-liner → fix direct
- Tâche purement répétitive → automatiser

## Adaptations

- **Module 100% IA / non-déterministe** : ajouter Phase 4 bis = "Eval suite" avec `specialized-model-qa`.
- **Module critique sécu** : insérer `engineering-security-engineer` review entre Phase 3 et Phase 4.
- **Module data lourde** : insérer Phase 2 bis = "Migration plan" avec `engineering-database-optimizer`.
