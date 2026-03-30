# PROJECT

## Vision

Ce repository fournit un kit de contexte pour Codex compose de skills, prompts et fichiers de memoire projet.

Le but est de permettre a un agent de :

- initialiser rapidement la comprehension d'un repo
- garder une memoire exploitable entre plusieurs sessions
- remettre a jour cette memoire quand le projet evolue

## Probleme adresse

Le projet vise les environnements LLM qui ne disposent pas nativement d'une commande de type `/init` accompagnee d'une memoire projet persistante.

## Livrables principaux

- un `AGENTS.md` orientant le comportement global
- quatre skills coeur : `init-orchestrator`, `project-scanner`, `work-memory`, `context-update`
- deux prompts de lancement
- une base `.codex/project-memory/` a embarquer dans un projet cible

## Utilisateur cible

- personnes qui travaillent avec Codex ou un autre agent base sur `AGENTS.md`
- maintainers voulant reduire la perte de contexte entre sessions
- equipes souhaitant ajouter une couche de memoire sans ecraser les conventions d'un repo existant

## Statut de confiance

- Source principale : scan du repo au 2026-03-30
- Derniere verification : 2026-03-30
- Niveau de confiance : eleve sur la structure, moyen sur l'intention communautaire a long terme
