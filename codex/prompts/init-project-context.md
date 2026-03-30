# Init Project Context

Utilise `init-orchestrator` pour initialiser completement ce repository.

Objectif :

- scanner la structure du projet
- identifier la stack et l'architecture
- creer ou mettre a jour la base documentaire dans `.codex/project-memory/`
- initialiser la memoire de travail pour les prochaines sessions

Actions attendues :

1. appliquer la logique de `project-scanner`
2. appliquer ensuite la logique de `work-memory`
3. mettre a jour au minimum :
   - `.codex/project-memory/PROJECT.md`
   - `.codex/project-memory/ARCHITECTURE.md`
   - `.codex/project-memory/CURRENT_STATE.md`
   - `.codex/project-memory/TASKS.md`
   - `.codex/project-memory/DECISIONS.md`
   - `.codex/project-memory/WORKLOG.md`
4. distinguer clairement les faits verifies des hypotheses
5. terminer par un resume court avec la prochaine etape recommandee
