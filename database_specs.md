# Database Specifications v1.0

## SQL Standards

1. **Naming Convention**: All table names, CTE names, and aliases must use snake_case (e.g., `patient_data`, `refus_patient`). Exception: transit_zone tables and external source references may retain their original casing.

2. **Security & Explicit Selection**: Never use `SELECT *` in production models. All columns must be explicitly named to ensure data lineage clarity and prevent unintended data exposure.

3. **Join Clarity**: All `JOIN` operations must explicitly specify their type (`INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, `FULL OUTER JOIN`).

4. **Code Formatting**: SQL keywords (`SELECT`, `FROM`, `WHERE`, `JOIN`, `WITH`, `AS`, etc.) must be written in UPPERCASE for consistency and readability.

5. **Documentation**: All models must include a description in their corresponding `.yml` schema file.
