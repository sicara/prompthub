# implement_from_notion_ticket

## Description
Given a Notion ticket (pasted content), extract the **What**, **How**, and **Validation** sections, build an explicit and actionable **implementation plan for Python code**, and **wait for user approval** before writing any code.

## Arguments
- `$1` (required): The full Notion ticket content pasted as plain text.

## Instructions
1. **Parse the ticket content from `$1`:**
   - Detect and normalize sections (case-insensitive, tolerate formatting): **What**, **How**, **Validation**.
   - Extract: goals, non-goals, constraints, stakeholders, scope boundaries, timelines (if any).

2. **Understand the existing codebase (Python focus) before proposing changes:**
   - Identify the project type and frameworks (e.g., Django/FastAPI/Flask, CLI, library).
   - Inventory key modules and entry points:
     - Search for conventional files and patterns: `app.py`, `main.py`, `manage.py`, `asgi.py`, `wsgi.py`, `settings.py`, `urls.py`, `models.py`, `schemas.py`, `services/`, `routers/`, `views/`, `tasks/`, `commands/`, `__init__.py`, `pyproject.toml`, `requirements.txt`.
     - Detect domain keywords from the ticket and grep the codebase for them (class/function names, endpoints, models, events, feature flags).
   - Build a **light dependency/usage map**:
     - Parse AST of candidate modules to list public functions/classes, their signatures, and call sites.
     - Note side effects (I/O, DB, network), feature flags, environment variables, and config keys.
   - Locate **existing tests** that touch the target area to infer expected behaviors and fixtures.

3. **Derive a solution approach from the ticket’s What/How:**
   - Align the **What** with user-visible outcomes (acceptance criteria).
   - Align the **How** with a technical approach; highlight divergences or missing details.
   - State assumptions explicitly; list open questions.

4. **Produce a detailed, explicit change plan (no code yet):**
   - Present a **file-by-file plan** with concrete actions:
     - `CREATE/MODIFY/DELETE` file paths.
     - For each file: functions/classes to implement or update (names, signatures, responsibilities).
     - Data model changes (ORM models, Pydantic schemas), migrations (if applicable).
     - API/CLI changes (method, path/command, request/response schemas, error cases).
     - Cross-cutting concerns: validation, logging, metrics, idempotency, retries, timeouts.
   - Specify **integration points** (DB tables, queues, external services) and how to mock them for tests.
   - Include **risk areas** and mitigations (backward compatibility, migrations, performance).

5. **Map to Validation (acceptance criteria):**
   - Convert the ticket’s **Validation** into a checklist of verifiable behaviors.
   - Define **test plan**:
     - Unit tests to add/modify (module, test names, main cases & edge cases).
     - Integration tests (routes, DB, background jobs).
     - Manual validation steps (commands to run, curl/httpie, admin UI steps).

6. **Deliverables & rollout:**
   - If needed: feature flag name and default state.
   - Migration order and rollback strategy.
   - Documentation updates (README/ADR/CHANGELOG).
   - Observability hooks (logs/metrics/traces) to confirm behavior post-deploy.

7. **Stop and wait for user confirmation:**
   - Output the **plan** and the **open questions**.
   - **Do not write code** yet. Ask for explicit “Approved” before proceeding.
   - If the ticket implies **> 2–3 substantial changesets**, recommend splitting into multiple PRs.

## Output
Produce a Markdown document with the following structure (fill all applicable sections):

### 1) Ticket summary
- **What**: …
- **How**: …
- **Validation**: …

### 2) Understanding of the existing codebase
- **Project type/frameworks**: …
- **Relevant modules & entry points**: …
- **Dependency/usage map (high level)**: …
- **Existing tests impacting scope**: …

### 3) Assumptions & open questions
- Assumption 1: …
- Question 1: …

### 4) Detailed change plan (awaiting approval)
For each file:
- `PATH/TO/FILE.py` — **ACTION**: CREATE/MODIFY/DELETE  
  - **Functions/classes**: names, signatures, responsibilities  
  - **Models/schemas/migrations**: …  
  - **APIs/CLI**: method/path/command, request/response schema, errors  
  - **Side effects**: DB, I/O, external services  
  - **Notes**: validation, logging, perf concerns  

### 5) Test plan
- **Unit tests**: list test modules, cases, edge cases  
- **Integration tests**: endpoints/flows, fixtures  
- **Manual validation steps**: commands/curl steps mirroring the **Validation** section

### 6) Rollout & observability
- Feature flags / migration steps / rollback  
- Metrics, logs, traces to confirm success

### 7) Next step
- **Pending user approval.**  
- If approved, proceed to generate code diffs/patches and tests according to this plan.  
- If scope > 2–3 major items, propose **multiple branches/PRs**.
