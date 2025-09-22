# write_docstrings

## Description
Generate or improve NumPy-style docstrings for functions in a Python file.

## Arguments
- `$1` (required): Path to the `.py` file to analyze.

## Instructions
1. Parse `$1` and list all functions and methods.
2. Detect functions with missing or incomplete docstrings.
3. For each function marked as `missing` or `improve`:
   - Propose a complete NumPy-style docstring outline:
     - One-line summary
     - Parameters (with types and optional flags)
     - Returns or Yields
     - Raises
     - Notes / See Also (if relevant)
     - Examples (include only if complexity justifies it)
4. Mark functions as `ok` if their docstrings are already compliant.
5. Justify the decision for including or skipping `Examples`.

## Hints
- For examples, read the tests files in src/tests to get hints.

