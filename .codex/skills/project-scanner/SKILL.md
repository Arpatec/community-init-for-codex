---
name: project-scanner
description: Analyser un projet pour comprendre sa structure, sa stack et son architecture, puis creer ou mettre a jour une base documentaire de contexte. Use when Codex initialise un repo, reprend un projet existant, manque de contexte, ou doit remettre a plat la documentation technique et fonctionnelle.
---

# Project Scanner Skill

## Objective
Analyser un projet et generer une comprehension claire de sa structure, de sa stack et de son architecture.

## Workflow

### 1. Scanner la structure

- Lister les dossiers principaux
- Identifier les fichiers cles : `config`, `routes`, `controllers`, `services`, infra, workflows, scripts, docs
- Reperer les points d'entree de l'application

### 2. Detecter la stack

Identifier les technologies visibles :

- Laravel / PHP
- Node / JavaScript / TypeScript
- Docker
- n8n
- Supabase ou autre base de donnees
- outils de build, tests, lint, CI

### 3. Analyser l'architecture

Determiner :

- le type de projet (SaaS, API, monolithe, microservices, site marketing, back-office)
- l'organisation des couches
- la logique metier principale
- les flux importants et integrations

### 4. Identifier les conventions

Reperer :

- conventions de nommage
- organisation des fichiers
- patterns visibles
- conventions de routes, vues et composants
- pratiques SEO si le projet a un front

### 5. Generer ou mettre a jour la documentation

Mettre a jour selon les informations verifiables :

- `.codex/project-memory/PROJECT.md`
- `.codex/project-memory/ARCHITECTURE.md`
- `.codex/project-memory/CURRENT_STATE.md`
- `.codex/project-memory/TASKS.md`

### 6. Formuler des suggestions

Proposer si pertinent :

- ameliorations structurelles
- simplifications
- optimisations de lisibilite
- points de vigilance

## Rules

- Ne pas modifier le code applicatif dans un scan de contexte sauf demande explicite
- Ne pas inventer d'informations
- Se baser uniquement sur ce qui est present dans le repo
- Signaler clairement les zones floues ou hypotheses
- Produire des fichiers markdown concrets et faciles a maintenir

## Output

- documentation `.codex/project-memory/` exploitable
- resume clair de la comprehension du projet
