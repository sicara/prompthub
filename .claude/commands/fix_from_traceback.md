# fix_from_traceback

## Description
Given a pasted **error message / traceback**, analyze the root cause, propose a detailed fix plan, **wait for user approval**, then implement the code and tests (pytest) to resolve the issue. Uses an iterative approach: reproduce → fix → validate.

## Arguments
- `$1` (required): The full error message / traceback (pasted text).

## Instructions
1. **Parse & understand the error**
   - Extract exception type, message, failing file/line, and call chain from `$1`.
   - Identify likely root-cause category (e.g., `ImportError`, `AttributeError`, `TypeError`, `ValueError`, `KeyError`, `IndexError`, `AssertionError`, `NoneType`, I/O, networking, env/config, version mismatch).
   - Locate implicated modules/functions using the file paths and symbols in the stack.
   - Skim surrounding code to understand intent (docstrings, comments, usage sites).

2. **Reproduce the failure**
   - Propose a **minimal reproducible test** using **pytest**:
     - File path and test name.
     - Input data and setup (fixtures/mocks).
     - Exact assertion that currently fails.
   - If runtime context is needed (env vars, config, dependency versions), list them explicitly.

3. **Plan the fix (await approval)**
   - Write a **clear fix plan** with:
     - **Root cause hypothesis** (what went wrong and why).
     - **Change list** (file-by-file; functions/classes to modify; signatures/logic to adjust).
     - **Validation plan** (tests to add/update; edge cases; negative tests).
     - **Non-code adjustments** if applicable (config/env/dependency pin).
   - Include **risk assessment** (API breakage, performance, backwards compatibility) and a **rollback idea**.
   - If plan touches **>2–3 substantial areas**, recommend splitting into multiple branches/PRs.
   - **Stop here and wait for explicit user approval** before coding.

4. **Implement the fix (after approval)**
   - Apply the minimal code changes required to satisfy the plan.
   - Add/adjust **pytest** tests:
     - Include edge cases and error paths.
     - Use fixtures/fakes/mocks for external effects (DB, API, FS).
   - Ensure style and typing are respected (type hints, clear names, small functions).

5. **Validate**
   - Run the test suite and confirm the original failure is resolved.
   - (If available) run `uv run coverage run -m pytest` and `uv run coverage report -m` to ensure coverage does not regress.
   - Provide a short summary of changes and remaining risks.
   - Do not run linting

## Output
Two phases:

1) **Before approval**  
- A Markdown report containing:
  - **Analysis** (exception breakdown, suspected root cause).
  - **Minimal reproducible pytest test** (specification; code stub if safe).
  - **Detailed fix plan** (file-by-file), **validation plan**, and **risks**.
  - A prompt asking the user to **approve** or request changes.

2) **After approval**  
- Applied code and test changes.
- A brief summary and (optionally) a diff of modified files.
- Test results confirmation (and coverage summary if run).

## Notes & constraints
- Prefer the **smallest viable fix**; avoid changing public APIs unless necessary.
- If a breaking change is unavoidable, **pause and re-confirm** with the user.
- Keep commits/PRs focused; if scope creeps, propose splitting the work.
