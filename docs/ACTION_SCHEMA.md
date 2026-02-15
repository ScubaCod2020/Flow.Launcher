## docs/ACTION_SCHEMA.md

### Purpose
Defines the **typed action contract** the Brainstem can execute.

### Design rules
- Actions are **deterministic**. The Brain may *propose* actions; the Brainstem **executes**.
- Actions must include a **trace_id**.
- Actions must be **idempotent** when feasible.
- Actions must declare required **confirmation** level.

### Common fields
All actions share:
- `trace_id` (string)
- `action_type` (string)
- `title` (string, user-facing)
- `requires_confirmation` (boolean)
- `risk_level` (`low` | `medium` | `high`)
- `payload` (object)

### v0.1 action types

#### 1) open_project
Opens a project locus.

Payload:
- `project_id`
- `target` (`root` | `docs` | `repo` | `note`)

#### 2) open_app
Launches an application.

Payload:
- `app_id` (friendly id)
- `command` (full path or registered command)
- `args` (array of strings)

#### 3) open_path
Opens a file/folder in the default handler.

Payload:
- `path`

#### 4) open_url
Opens a URL.

Payload:
- `url`

#### 5) search_web
Opens a search using a named template.

Payload:
- `engine` (e.g., `google`, `bing`, `duckduckgo`, `github`, `docs`)
- `query`

### v0.2 action types (planned)
- `append_log`
- `write_note`
- `clipboard_write`
- `clipboard_read`

### v0.3 action types (planned)
- `run_script`
- `run_workflow`

### v0.4 action types (planned)
- `focus_window`
- `uia_inspect_active_window`

### Logging contract (minimum)
Every executed action writes a log line:
- timestamp
- trace_id
- action_type
- decision (executed / rejected / failed)
- outcome summary
- artifact refs (if any)

### Next required action
Create `docs/PROJECT_INDEX_SPEC.md` (source of truth for `open_project`).
