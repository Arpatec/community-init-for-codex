# AGENTS.md

## Objective
Fournir un cadre clair pour travailler efficacement sur ce projet avec Codex, en garantissant coherence, lisibilite et continuite.

---

## General principles

- Toujours comprendre avant de modifier
- Ne jamais casser un comportement existant sans raison
- Privilegier des solutions simples, lisibles et maintenables
- Adapter les propositions a la stack reelle du projet
- Ne pas sur-architecturer

---

## Project awareness

Avant toute tache non triviale, analyser :

- la structure du projet
- les fichiers existants lies a la tache
- les conventions deja en place

Si le contexte est insuffisant :
utiliser le skill `project-scanner`

Si le contexte existe deja mais semble obsolete ou incomplet :
utiliser le skill `context-update`

---

## Working memory (CRITICAL)

Ce projet utilise une memoire de travail persistante.

### Files to read before working

- `.codex/project-memory/CURRENT_STATE.md`
- `.codex/project-memory/TASKS.md`
- `.codex/project-memory/DECISIONS.md`

Si un journal source est indique dans la demande ou dans `.codex/project-memory/CURRENT_STATE.md`, le lire aussi avant de travailler.

### Files to update after working

- `.codex/project-memory/CURRENT_STATE.md`
- `.codex/project-memory/WORKLOG.md`
- `.codex/project-memory/TASKS.md`
- `.codex/project-memory/DECISIONS.md` (si decision importante)

Si un journal source officiel est utilise par le projet, proposer ou effectuer sa mise a jour selon la demande.

### When to use work-memory skill

Utiliser le skill `work-memory` si :

- la tache comporte plusieurs etapes
- il y a du debug
- il y a des choix techniques
- il y a un impact sur l'architecture
- la tache devra etre reprise plus tard

---

## Project documentation

Les fichiers suivants doivent rester coherents :

- `.codex/project-memory/PROJECT.md` -> vision fonctionnelle
- `.codex/project-memory/ARCHITECTURE.md` -> structure technique

Si un changement impacte ces elements :
proposer une mise a jour

---

## Code conventions

- Respecter l'organisation existante
- Ne pas deplacer des fichiers sans raison
- Nommer clairement variables, fonctions, classes
- Factoriser si necessaire, mais sans exces
- Eviter la logique complexe dans les vues

---

## Laravel specific rules (if applicable)

- Controleurs fins
- Logique metier dans des services si necessaire
- Routes nommees
- Blade propre et lisible
- SEO pris en compte (title, meta, OG si front)

---

## Safety rules

- Ne pas supprimer du code sans validation implicite
- Ne pas modifier des fichiers critiques sans expliquer
- Toujours expliquer les changements importants

---

## Skills usage

### init-orchestrator

A utiliser pour :

- lancer une initialisation complete du contexte projet
- enchainer scan structurel et mise en place de la memoire
- remettre en route un repo avec une base documentaire incomplete

### project-scanner

A utiliser pour :

- initialiser le projet
- comprendre une base inconnue
- remettre a plat la documentation

### work-memory

A utiliser pour :

- suivre les taches complexes
- maintenir l'etat du projet
- eviter la perte de contexte

### context-update

A utiliser pour :

- resynchroniser la memoire projet apres des changements
- mettre a jour la documentation sans refaire une initialisation complete
- corriger un contexte devenu obsolete

---

## Expected behavior

- Etre clair, structure, utile
- Donner des reponses actionnables
- Anticiper les impacts
- Proposer des ameliorations pertinentes (sans deriver)
- Garder `.codex/project-memory/` court, fiable et a jour
