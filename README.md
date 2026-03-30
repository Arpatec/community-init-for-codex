# Skill Init for Codex

Un socle communautaire pour reproduire l'esprit de `/init` de Claude sur des LLM qui n'ont pas nativement cette fonction, avec en plus une memoire projet persistante.

Projet original cree par Arpatec / doc-rezo.fr.

Ce depot fournit un petit systeme de contexte pour Codex :

- initialiser rapidement la comprehension d'un projet
- garder une memoire exploitable entre les sessions
- resynchroniser cette memoire quand le repo evolue
- s'integrer sans ecraser les conventions deja en place

Pour la version courte, voir aussi [PLAYBOOK.md](PLAYBOOK.md).

## Pourquoi ce repo existe

Claude dispose deja d'une logique de type `/init` tres pratique pour repartir d'un projet avec du contexte. Ce repo a ete construit pour offrir un equivalent reutilisable aux autres LLM, avec une couche supplementaire : une memoire projet durable dans `.codex/project-memory/`.

L'idee n'est pas de remplacer les regles du projet.
L'idee est d'ajouter une couche de comprehension, de suivi et de synchronisation qui aide un agent a mieux reprendre le fil d'un repo au fil du temps.

## Ce que contient le systeme

- `AGENTS.md` : regles durables a injecter ou adapter dans le projet cible
- `.codex/skills/init-orchestrator/` : equivalent de `/init`
- `.codex/skills/project-scanner/` : scan structurel et comprehension du repo
- `.codex/skills/work-memory/` : suivi des taches longues, decisions et etat courant
- `.codex/skills/context-update/` : resynchronisation de la memoire
- `.codex/prompts/` : prompts reutilisables pour lancer l'initialisation ou la mise a jour
- `.codex/project-memory/` : base de memoire vivante a maintenir dans le projet

## Promesse

Une fois installe dans un repo, ce systeme aide un agent a :

- comprendre plus vite la structure du projet
- documenter les faits verifies et les hypotheses
- garder trace des taches, decisions et changements importants
- reprendre une session sans repartir de zero

## Cas d'usage

Ce repo est utile si vous voulez :

- donner a Codex ou a un autre LLM une logique d'initialisation de contexte
- conserver un historique de travail plus fiable entre plusieurs sessions
- reduire la perte de contexte sur des taches longues
- garder un `AGENTS.md` court tout en externalisant l'etat mouvant du projet

## Installation rapide dans un projet

### Cas 1. Le projet n'a pas encore de `AGENTS.md`

Copier :

- `AGENTS.md`
- `.codex/skills/`
- `.codex/prompts/`
- `.codex/project-memory/`

Puis lancer :

```text
Utilise init-orchestrator pour initialiser completement ce repository.
```

### Cas 2. Le projet a deja un `AGENTS.md`

Ne pas ecraser le fichier existant.

Faire une integration douce :

- conserver le `AGENTS.md` existant
- ajouter le bloc Memoire projet fourni plus bas
- copier `.codex/skills/`
- copier `.codex/prompts/`
- copier `.codex/project-memory/`

## Bloc Memoire projet a ajouter dans un `AGENTS.md` existant

```md
## Memoire projet

Avant toute tache non triviale, lire :
- `.codex/project-memory/CURRENT_STATE.md`
- `.codex/project-memory/TASKS.md`
- `.codex/project-memory/DECISIONS.md`

Si un journal source est precise dans la demande, le lire aussi.
Sinon, utiliser la source declaree dans `.codex/project-memory/CURRENT_STATE.md` si elle existe.

Apres toute tache non triviale, mettre a jour si necessaire :
- `.codex/project-memory/CURRENT_STATE.md`
- `.codex/project-memory/WORKLOG.md`
- `.codex/project-memory/TASKS.md`
- `.codex/project-memory/DECISIONS.md`
- le journal source du projet si le workflow le demande

Utiliser `init-orchestrator` pour initialiser le contexte.
Utiliser `context-update` pour le resynchroniser.
Utiliser `work-memory` pour les taches longues ou complexes.
```

## Quand utiliser quoi

### `init-orchestrator`

A utiliser quand le projet n'a pas encore de base de contexte exploitable.

Exemple :

```text
Utilise init-orchestrator pour initialiser completement ce repository.
```

Effet attendu :

- lecture du repo
- detection de la stack
- premiere base dans `.codex/project-memory/`

### `context-update`

A utiliser quand la memoire existe deja mais ne colle plus tout a fait au repo reel.

Exemple :

```text
Utilise context-update pour resynchroniser la memoire de ce repository.
```

Effet attendu :

- relecture de la memoire existante
- comparaison avec le repo reel
- mise a jour ciblee des fichiers de contexte

### `work-memory`

A utiliser pendant une tache longue, technique ou amene a etre reprise plus tard.

Exemple :

```text
Utilise work-memory pour suivre cette tache et maintenir la memoire du projet a jour.
```

Effet attendu :

- suivi de l'objectif
- mise a jour des taches en cours
- trace concise des decisions et suites utiles

### `project-scanner`

A utiliser quand le repo est peu connu, mal documente, ou quand on veut remettre a plat la vision technique et fonctionnelle.

Effet attendu :

- cartographie du projet
- vision plus claire de la stack et de l'architecture
- documentation projet plus fiable

## Journal source configurable

Le systeme peut lire un fichier d'historique ou de suivi sans supposer qu'il s'appelle `CHANGELOG.md`.

Vous pouvez :

- fournir le chemin dans le prompt
- ou memoriser la source dans `.codex/project-memory/CURRENT_STATE.md`

Exemple :

```text
Utilise context-update en prenant comme journal source : `notes/history.md`
```

Exemple de source memorisee :

```md
## Sources de synchronisation

- Journal principal : `notes/history.md`
- Autres sources utiles : `docs/decisions.md`
- Derniere synchronisation : 2026-03-29
```

## Philosophie

- `AGENTS.md` reste court et stable
- `.codex/project-memory/` contient l'etat mouvant
- les skills appliquent une methode specialisee
- les faits verifies sont distingues des hypotheses
- la memoire doit rester concise, utile et actionnable

## Limites actuelles

- le repo est pense pour des workflows bases sur `AGENTS.md` et des skills locaux
- la documentation est aujourd'hui en francais
- il ne remplace pas l'expertise humaine ni les conventions metier du projet

## Contribution

Les contributions utiles pour la communaute sont par exemple :

- ameliorer les prompts et instructions
- renforcer la clarte du workflow
- ajouter des exemples d'integration reellement testables
- proposer des variantes pour d'autres environnements LLM

Voir [CONTRIBUTING.md](CONTRIBUTING.md).

## Licence et attribution

Ce projet est distribue sous licence Apache-2.0.

Si vous le reutilisez, le modifiez ou le redistribuez, conservez la licence, les notices et le fichier `NOTICE` afin de preserver la trace du projet d'origine.

## Publication GitHub recommande

Pour publier proprement :

1. initialiser le depot Git local
2. choisir une licence explicite
3. pousser le repo sur GitHub avec ce README
4. ajouter quelques captures ou exemples reels d'utilisation plus tard si besoin

## En une phrase

Un kit simple pour donner a Codex et aux autres LLM une logique communautaire de type `/init`, renforcee par une memoire projet persistante.
