## docs/PROJECT_INDEX_SPEC.md

### Purpose
Defines the **Projects-first hierarchy**. Projects are the primary navigation primitive.

### Source-of-truth file
- `brainstem/projects.yaml` (recommended) OR a path configured in settings.
- v0 chooses **one** source and sticks to it.

### Minimum schema (v0.1)
Each project must define:
- `project_id` (unique, stable)
- `display_name`
- `root_path` (Windows path on Forge)
- `repo_url` (optional)
- `docs_path` (optional, defaults to `${root_path}\\docs`)
- `note_path` (optional, defaults to `${root_path}\\notes\\scratch.md`)
- `tags` (list)

### Example
```yaml
projects:
  - project_id: bishop-core
    display_name: Bishop Core
    root_path: C:\\Projects\\bishop\\bishop-core
    repo_url: https://github.com/<you>/bishop-core
    docs_path: C:\\Projects\\bishop\\bishop-core\\docs
    note_path: C:\\Projects\\bishop\\bishop-core\\notes\\scratch.md
    tags: [brain, kernel]
```

### Project targets
`open_project.target` must support:
- `root` → open `root_path`
- `docs` → open `docs_path`
- `repo` → open `repo_url`
- `note` → open `note_path`

### Selection behavior (Flow UI)
- Type-to-filter by `display_name`, `project_id`, and `tags`.
- Top result is the default action (open root).
- Secondary actions appear as sub-results (docs/repo/note).

### Next required action
Create `docs/BASELINE_CHECKLIST.md` and run the baseline on upstream Flow.
