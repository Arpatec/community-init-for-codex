# ARCHITECTURE

## Vue d'ensemble

Le repo est un petit depot de configuration documentaire sans code applicatif.

Il s'articule autour de quatre briques :

- `AGENTS.md` : cadre de comportement a injecter ou adapter dans un projet
- `.codex/skills/` : logique specialisee de scan, init, synchronisation et memoire
- `.codex/prompts/` : points d'entree textuels pour lancer les workflows
- `.codex/project-memory/` : structure de memoire persistante a maintenir dans le projet cible

## Structure technique

- racine : documentation de publication et regles globales
- `.codex/skills/init-orchestrator/` : orchestration du scan initial puis de la memoire
- `.codex/skills/project-scanner/` : comprehension structurelle du repo
- `.codex/skills/work-memory/` : suivi des taches longues et de l'etat courant
- `.codex/skills/context-update/` : resynchronisation de la memoire
- `.codex/prompts/` : prompts prets a copier dans une session
- `.codex/project-memory/` : templates de contexte persistants

## Statut de confiance

- Source principale : scan du repo au 2026-03-30
- Derniere verification : 2026-03-30
- Niveau de confiance : eleve

## Stack

- Backend : aucun
- Frontend : aucun
- Base de donnees : aucune
- Infra / deploy : non applicable
- Outils / integrations : Markdown, structure `.codex`, skills et prompts

## Organisation du code

- depot centré sur la documentation et les instructions agentiques
- pas de code applicatif, pas de build, pas de runtime applicatif

## Modules ou domaines

- initialisation du contexte
- scan du projet
- memoire de travail
- resynchronisation du contexte

## Flux principaux

1. installer les fichiers dans un repo cible
2. lancer `init-orchestrator`
3. remplir la base `.codex/project-memory/` a partir du scan reel
4. utiliser `work-memory` pendant les taches longues
5. utiliser `context-update` quand la memoire n'est plus alignee avec le repo

## Points d'entree

- `AGENTS.md`
- `.codex/prompts/init-project-context.md`
- `.codex/prompts/update-project-context.md`
- skills dans `.codex/skills/`

## Dependances externes

- aucune dependance logicielle detectee

## Zones sensibles

- clarte des instructions
- coherence entre skills, prompts et memoire
- compatibilite avec des `AGENTS.md` deja presents

## Dette technique ou zones floues

- licence open source non choisie
- absence actuelle de repo Git initialise
- documentation publique encore uniquement en francais
