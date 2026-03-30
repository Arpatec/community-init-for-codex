# Playbook Express

Version courte du repo pour une prise en main rapide.

Ce systeme sert a donner a Codex ou a un autre LLM un equivalent communautaire de `/init`, avec une memoire projet persistante en plus.

## 1. Premiere installation sur un projet

```text
Utilise init-orchestrator pour initialiser completement ce repository.
```

## 2. Premiere installation sur un projet deja ancien

```text
Utilise init-orchestrator pour initialiser completement ce repository.
Prends comme journal source : `notes/history.md`
```

Remplacer `notes/history.md` par le vrai fichier du projet si besoin.

## 3. Mettre a jour une memoire deja en place

```text
Utilise context-update pour resynchroniser la memoire de ce repository.
```

## 4. Mettre a jour avec un journal source explicite

```text
Utilise context-update pour resynchroniser la memoire de ce repository.
Prends comme journal source : `notes/history.md`
```

## 5. Suivre une tache longue ou complexe

```text
Utilise work-memory pour suivre cette tache et maintenir la memoire du projet a jour.
```

## Regle simple

- pas encore de `.codex/project-memory/` utile -> `init-orchestrator`
- memoire deja en place -> `context-update`
- tache longue, debug, refactor, reprise plus tard -> `work-memory`

## Fichiers a lire vite

- `AGENTS.md`
- `.codex/project-memory/CURRENT_STATE.md`
- `.codex/project-memory/TASKS.md`
- `.codex/project-memory/DECISIONS.md`

## Si le projet a deja un `AGENTS.md`

- ne pas l'ecraser
- ajouter seulement le bloc Memoire projet du `README.md`
- garder les regles metier et marque existantes
