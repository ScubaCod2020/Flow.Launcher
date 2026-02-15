## docs/ROADMAP.md

### Purpose
Defines the **versioned capability roadmap** for the Brainstem layer.

### Scope rules
- **v0.1–v0.4 are canonical** and must be completed in order.
- Later versions (v1+) may be planned, but **cannot be implemented** until v0.4 is complete.
- Every capability must map to:
  - a command (input)
  - an action (typed output)
  - an executor (deterministic)
  - a log record (traceable)

### Definitions
- **Brain (AI Class):** planning/reasoning/intent.
- **Brainstem (Flow fork):** receives commands, renders results, executes safe OS actions, logs everything.
- **Action:** typed instruction emitted by Brain and executed by Brainstem.

### Roadmap

#### v0 — Brainstem Primitives (Windows-first)

##### v0.1 — Find / Launch / Open Fast
**Goal:** reliably open the right target with minimal friction.

**Capabilities**
- v0.1.1 Open **project target** (primary): open project root / jump locus
- v0.1.2 Open **app**
- v0.1.3 Open **file/folder**
- v0.1.4 Open **URL/search**
- v0.1.5 Quick targets (pinned projects + common loci)
- v0.1.6 Action logging (trace_id + outcome)

**Exit criteria**
- A user can invoke any of the above from Flow reliably.
- Every invocation produces a log entry.

##### v0.2 — Capture / Organize / Log
**Goal:** persist useful artifacts to the vault/project without friction.

**Capabilities**
- v0.2.1 Append to session log
- v0.2.2 Create/update markdown note
- v0.2.3 Clipboard read/write helpers
- v0.2.4 Minimal templating (note/task stub)

**Exit criteria**
- Capture actions always write to a deterministic path and log the artifact reference.

##### v0.3 — Repeatable Execution
**Goal:** run deterministic workflows with guardrails.

**Capabilities**
- v0.3.1 Whitelisted script runner
- v0.3.2 Project-scoped workflows (recipes)
- v0.3.3 Audit trail + rollback notes

**Exit criteria**
- Every workflow has an allowlist, a dry-run mode, and logs inputs/outputs.

##### v0.4 — Control Apps
**Goal:** start OS-level interaction safely.

**Capabilities**
- v0.4.1 Focus/foreground window
- v0.4.2 UI inspection (read-only) — later
- v0.4.3 Controlled interaction (invoke/set) — later

**Exit criteria**
- Focus window works reliably; UI automation work remains gated behind explicit safety policies.

#### v1+ — Expansion (Not Implemented Until v0.4 Done)
- v1 Projects-first enrichment (indexing, key files, defaults)
- v2 Project-centric capture improvements
- v3 Advanced workflow orchestration
- v4 Cross-platform cockpit strategy

### Next required action
Create `docs/BASELINE_CHECKLIST.md` and perform the baseline run on upstream Flow.
