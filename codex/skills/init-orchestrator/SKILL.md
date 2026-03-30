---
name: init-orchestrator
description: Orchestrer l'initialisation complete du contexte d'un repo en combinant scan structurel, creation de documentation et mise en place de la memoire de travail. Use when Codex doit reproduire un equivalent de /init, remettre a plat un projet, ou lancer un repo avec une base de contexte durable et exploitable.
---

# Init Orchestrator Skill

## Objective
Lancer une initialisation de contexte complete et coherente pour un repository.

## Workflow

### 1. Etablir le point de depart

- Lire `AGENTS.md` si present
- Examiner rapidement la structure du repo
- Identifier si `.codex/project-memory/` et les skills existent deja

### 2. Effectuer le scan structurel

Appliquer la logique du skill `project-scanner` pour :

- comprendre la stack
- identifier l'architecture
- relever les conventions du projet
- remplir ou corriger `.codex/project-memory/PROJECT.md`
- remplir ou corriger `.codex/project-memory/ARCHITECTURE.md`

### 3. Initialiser la memoire de travail

Appliquer la logique du skill `work-memory` pour :

- poser un `CURRENT_STATE.md` fidele a la situation actuelle
- initialiser ou ajuster `TASKS.md`
- consigner les arbitrages de depart dans `DECISIONS.md`
- enregistrer l'initialisation dans `WORKLOG.md`

### 4. Produire un resultat directement exploitable

Le resultat final doit laisser le repo avec :

- un cadre durable dans `AGENTS.md`
- une documentation de base dans `.codex/project-memory/`
- une prochaine etape claire

### 5. Signaler les limites

- distinguer les faits verifies des hypotheses
- signaler les zones floues
- proposer les suites logiques sans inventer

## Rules

- Ne pas modifier le code applicatif pendant l'initialisation sauf demande explicite
- Prioriser les fichiers de contexte plutot que des explications longues en reponse
- Garder `AGENTS.md` stable et concis
- Mettre l'etat mouvant dans `.codex/project-memory/`
- Utiliser une sortie structuree, concrete et actionnable

## Output

- contexte projet initialise ou remis a niveau
- memoire de travail prete pour les prochaines sessions
- resume clair de l'etat du repo et de la prochaine action recommande
