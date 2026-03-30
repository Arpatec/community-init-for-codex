# Update Project Context

Utilise `context-update` pour resynchroniser la memoire de ce repository avec son etat actuel.

Objectif :

- relire la memoire existante
- comparer avec le repo reel
- mettre a jour uniquement les fichiers necessaires dans `.codex/project-memory/`
- garder un contexte concis, fiable et actionnable

Journal source a lire en priorite :

- `<chemin-vers-le-fichier>` si fourni
- sinon utiliser la source declaree dans `.codex/project-memory/CURRENT_STATE.md` si elle existe

Actions attendues :

1. lire `AGENTS.md` et la memoire existante
2. lire le journal source si un chemin explicite est fourni ou deja memorise
3. comparer la documentation avec le code, la structure actuelle et le journal source si disponible
4. mettre a jour si necessaire :
   - `.codex/project-memory/PROJECT.md`
   - `.codex/project-memory/ARCHITECTURE.md`
   - `.codex/project-memory/CURRENT_STATE.md`
   - `.codex/project-memory/TASKS.md`
   - `.codex/project-memory/DECISIONS.md`
   - `.codex/project-memory/WORKLOG.md`
5. memoriser la source de synchronisation si elle doit etre reutilisee
6. distinguer clairement les faits verifies des hypotheses
7. terminer par un resume court avec les corrections apportees et la prochaine etape recommandee
