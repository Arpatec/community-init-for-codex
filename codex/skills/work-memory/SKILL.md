---
name: work-memory
description: Maintenir une memoire de travail claire, structuree et persistante pour les taches complexes. Use when Codex travaille sur une tache multi-etapes, du debug, un refactor, une evolution fonctionnelle, une decision technique, ou un travail qui devra etre repris plus tard.
---

# Work Memory Skill

## Objective
Maintenir une memoire de travail claire, structuree et persistante du projet.

## Workflow

### 1. Lire le contexte

Lire en priorite :

- `.codex/project-memory/CURRENT_STATE.md`
- `.codex/project-memory/TASKS.md`
- `.codex/project-memory/DECISIONS.md`

Si la demande fournit un journal source explicite, le lire aussi.
Sinon, verifier dans `.codex/project-memory/CURRENT_STATE.md` s'il existe une section `Sources de synchronisation` avec un journal principal.

Comprendre :

- ou en est le projet
- ce qui est en cours
- les contraintes et risques connus
- les changements recents consignes dans le journal source s'il existe

### 2. Clarifier la tache

Definir :

- l'objectif
- les etapes
- les risques ou dependances

### 3. Suivre pendant l'execution

Noter les elements utiles a memoriser :

- changements importants
- erreurs rencontrees
- choix techniques
- pistes de suivi

### 4. Mettre a jour la memoire

Mettre a jour selon le niveau d'impact :

- `.codex/project-memory/CURRENT_STATE.md`
- `.codex/project-memory/WORKLOG.md`
- `.codex/project-memory/TASKS.md`
- `.codex/project-memory/DECISIONS.md`

Si un journal source est present :

- en extraire uniquement les informations utiles et encore actives
- ne pas recopier integralement son contenu dans la memoire
- noter dans `CURRENT_STATE.md` la source utilisee et, si utile, la derniere synchronisation
- mettre a jour le journal source seulement si la demande ou le workflow du projet le prevoit

### 5. Rester pratique

- etre concis
- etre clair
- eviter le bruit inutile
- privilegier l'actionnable
- ne documenter que ce qui aidera vraiment une prochaine session

## Rules

- Ne pas sur-documenter
- Ne pas repeter inutilement
- Toujours garder une vision operationnelle
- Mettre a jour uniquement ce qui est pertinent
- Faire apparaitre clairement les prochaines actions quand elles existent
- Considerer le journal source comme une entree de synchronisation, pas comme un substitut a toute la memoire projet

## Output

- memoire propre et a jour
- continuite entre les sessions
- comprehension immediate de l'etat du projet
