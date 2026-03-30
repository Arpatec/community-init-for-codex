---
name: context-update
description: Mettre a jour la memoire de projet existante apres des changements de code, d'architecture ou de priorites, sans refaire une initialisation complete. Use when Codex doit resynchroniser le contexte, corriger une documentation obsolete, ou rafraichir PROJECT, ARCHITECTURE, CURRENT_STATE, TASKS, DECISIONS et WORKLOG a partir de l'etat reel du repo, eventuellement en utilisant un journal source explicitement indique dans la demande.
---

# Context Update Skill

## Objective
Resynchroniser la memoire projet avec l'etat reel du repository sans relancer un scan initial complet.

## Workflow

### 1. Lire la memoire existante

Lire en priorite :

- `AGENTS.md`
- `.codex/project-memory/PROJECT.md`
- `.codex/project-memory/ARCHITECTURE.md`
- `.codex/project-memory/CURRENT_STATE.md`
- `.codex/project-memory/TASKS.md`
- `.codex/project-memory/DECISIONS.md`
- `.codex/project-memory/WORKLOG.md`

Si la demande fournit un chemin de journal source, le lire aussi.
Sinon, verifier dans `.codex/project-memory/CURRENT_STATE.md` si une source de synchronisation est deja declaree.

### 2. Comparer avec le repo actuel

- identifier ce qui a change
- distinguer les faits verifies des hypotheses
- reperer les sections devenues fausses, floues ou perimees
- recouper avec le journal source quand il existe

### 3. Mettre a jour uniquement ce qui est necessaire

Selon l'impact :

- `PROJECT.md` si le perimetre fonctionnel a bouge
- `ARCHITECTURE.md` si la structure technique a evolue
- `CURRENT_STATE.md` pour l'etat du moment
- `TASKS.md` pour les actions en cours, a faire ou terminees
- `DECISIONS.md` pour les arbitrages importants
- `WORKLOG.md` pour la trace des mises a jour

Si un journal source est utilise :

- n'en extraire que les informations encore utiles
- memoriser la source dans `CURRENT_STATE.md` si elle doit etre reutilisee
- indiquer la derniere synchronisation si l'information est disponible

### 4. Garder une memoire utile

- supprimer le bruit inutile
- ne pas dupliquer la meme information dans plusieurs fichiers
- preferer des notes courtes, exactes et actionnables

### 5. Terminer avec une synthese

- ce qui a ete confirme
- ce qui a ete corrige
- ce qui reste incertain
- prochaine etape recommandee

## Rules

- Ne pas reinitialiser tout le contexte si une mise a jour ciblee suffit
- Ne pas inventer d'informations
- Signaler clairement les zones d'incertitude
- Conserver l'historique utile dans `DECISIONS.md` et `WORKLOG.md`
- Garder `CURRENT_STATE.md` court et operationnel
- Ne pas supposer que le fichier s'appelle `CHANGELOG.md`

## Output

- memoire resynchronisee avec le repo
- documentation plus fiable
- priorites etat / prochaines actions clarifiees
