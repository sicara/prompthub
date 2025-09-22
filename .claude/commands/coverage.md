# coverage

## Description
Analyze the test suite, run coverage python library (with uv), and guide improvements until the folder reaches **100% test coverage**.  
Focus on adding **pytest tests** for edge cases, error handling, and untested branches.

## Arguments
- `$1` (required): Path to the folder containing the repository.

## Instructions
1. **Run coverage analysis**:
   - Execute: `uv run coverage run -m pytest` inside `$1`.
   - Generate a coverage report with: `uv run coverage report -m`.
   - Identify files, functions, and lines not covered.

2. **Read the test files**:
   - Detect existing pytest test modules and functions.
   - Understand the current test structure (fixtures, mocks, parametrization).

3. **Design missing tests**:
   - For each uncovered function/line:
     - Add new pytest tests targeting **edge cases**.
     - Cover both normal flow and error conditions.
   - Ensure exceptions, boundary inputs, and unusual scenarios are tested.

4. **Iterate**:
   - Rerun coverage until all functions/branches are tested.
   - If 100% coverage cannot be achieved (e.g., dead code, defensive guards), explain why.

5. **Best practices**:
   - Use **pytest fixtures** for reusable setup.
   - Use `pytest.mark.parametrize` to test multiple inputs.
   - Mock external dependencies (DB, APIs, filesystem) when required.
   - Keep tests isolated and deterministic.

## Output
- An updated test suite with additional pytest test files/functions.  
- `coverage report -m` showing **100% coverage** (or explanation for untestable code).  
- A summary of new tests added, especially edge cases.
