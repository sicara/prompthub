# update_changelog

## Description
Read the changelog and the changes in the current branch, understand the main improvements, and update `$1` (`changelog.md`) with only the key changes. Minor adjustments should not be included.

## Arguments
- `$1` (required): Path to the `changelog.md` file.

## Instructions
1. Read the existing changelog from `$1`.
2. Read the changes of the current branch (diff compared to main).
3. Identify **main changes and improvements** only:
   - New features
   - Significant bug fixes
   - Major refactors or performance improvements
4. Ignore small adjustments (formatting, comments, minor refactors).
5. Write **only 2 or 3 concise changelog entries**:
   - Each entry should be short, clear, and user-facing.
   - Use bullet points.
6. If more than 3 main changes are detected:
   - Stop writing.
   - Output a message to the user suggesting to split the work into multiple branches or PRs.

## Output
An updated `changelog.md` file with:
- Only the most important 2–3 changes listed under the current version.
- A warning message if too many changes are detected.
