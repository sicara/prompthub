# generate_global_flow

## Description
Analyze the codebase to build a **global architecture flowchart** of the repository and save the diagram in a new `FLOW.md` file at the project root.

## Arguments
- `$1` (required): Path to the folder containing the repository.

## Instructions
1. **Scan the repository in `$1`:**
   - Detect main modules, packages, and services.
   - Identify entry points (`main.py`, `app.py`, CLI commands, server initializers).
   - Map dependencies and interactions between components.
   - Recognize external integrations (databases, APIs, message queues, file systems).

2. **Build a high-level architecture representation:**
   - Group code into **domains** (core, utils, API, models, services, etc.).
   - Highlight **data flows** (requests → processing → storage/output).
   - Distinguish internal vs. external components.
   - Abstract away low-level helpers; focus on key architecture.

3. **Generate a Mermaid diagram:**
   - Use `graph TD` or `graph LR` to represent flow clearly.
   - Nodes must have **explicit, business-oriented names** (optionally with module/class names in parentheses).
   - Use colors/shapes to distinguish:
     - APIs / entry points
     - Core services
     - Data models / storage
     - External integrations

4. **Write to `FLOW.md`:**
   - Create or overwrite a file named `FLOW.md` at the root of the project.
   - Include:
     - Title (`# Global Architecture Flow`)
     - Short description of the diagram
     - Mermaid diagram in a fenced code block
   - Ensure the file is standalone and can be previewed directly on GitHub/GitLab.

## Output
A new `FLOW.md` file at the repository root containing:
- A textual introduction.
- A **global Mermaid architecture diagram** that visualizes the structure and data flows of the repo.
