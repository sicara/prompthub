# load_context

## Description
Read all `.md` files in the given folder to build a **global context** of the repository, including business logic, architecture, code conventions, and domain knowledge.  
⚠️ This command does **not output anything**. The extracted context is kept internally in Claude's working memory for later commands.

## Arguments
- `$1` (required): Path to the folder containing the repository.

## Instructions
1. **Scan `$1` recursively**:
   - Find all `.md` files (README, CONTRIBUTING, ADRs, specs, FLOW, docs).
   - Ignore files without meaningful context (LICENSE, CHANGELOG, etc.).

2. **Parse and understand content**:
   - Extract project description, business/domain terminology, architecture hints.
   - Identify modules, responsibilities, design decisions, and constraints.
   - Note coding practices, testing strategy, deployment details.

3. **Keep the context**:
   - Store the synthesized knowledge internally (business + technical context).
   - Do not display or write any file.
   - Make this context available for follow-up commands (`write_docstrings`, `generate_global_flow`, etc.).

## Output
Nothing.  
All information is stored in Claude’s context for future use.
