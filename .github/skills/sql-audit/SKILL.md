---
name: sql-audit
description: Audits SQL files against project specifications and security rules.
---
# SQL Audit Workflow
When this skill is activated:
1. **Analyze**: Read `database_specs.md` to load current project standards.
2. **Review**: Scan the target SQL file for any violations of the Naming, Security, or Performance rules.
3. **Report**: Provide a bulleted list of violations found.
4. **Fix**: Propose a refactored version of the SQL that is 100% compliant.
