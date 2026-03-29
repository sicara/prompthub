# classy_claude_commands
Here lays our best CCC (Classy Claude Commands)

## Function Flowcharts

This section illustrates the main workflows of our most complex Claude Code commands using Mermaid flowcharts.

### 1. Implement Notion Ticket Workflow

The `implement_notion_ticket` command orchestrates a comprehensive workflow for converting Notion tickets into detailed Python implementation plans. This process ensures thorough analysis before any code is written.

```mermaid
flowchart TD
    A[Parse Ticket Content<br/>extract What/How/Validation] --> B{Valid Ticket Format?}
    B -->|No| B1[Request Proper Format]
    B -->|Yes| C[Analyze Existing Codebase<br/>identify frameworks & patterns]
    C --> D[Build Dependency Map<br/>AST parsing & call sites]
    D --> E[Derive Solution Approach<br/>align What/How sections]
    E --> F[Generate Detailed Change Plan<br/>file-by-file actions]
    F --> G[Create Test Plan<br/>unit/integration tests]
    G --> H[Define Rollout Strategy<br/>migrations & observability]
    H --> I[Wait for User Approval<br/>explicit confirmation required]
    I -->|Approved| J[Proceed to Implementation]
    I -->|Too Complex| K[Recommend PR Split]

    style A fill:#e1f5fe,stroke:#01579b
    style I fill:#fff3e0,stroke:#e65100
    style J fill:#e8f5e8,stroke:#2e7d32
    style K fill:#fce4ec,stroke:#c2185b
```

### 2. Code Review Process Workflow

The `code_review` command implements a systematic code analysis process that prioritizes findings and maintains project documentation through TASK.md integration.

```mermaid
flowchart TD
    A[Scan Entire Codebase<br/>analyze structure & patterns] --> B[Identify Issues Across Categories<br/>security/performance/quality]
    B --> C[Categorize by Severity<br/>Critical/High/Medium/Low]
    C --> D[Read Existing TASK.md<br/>understand current priorities]
    D --> E{Duplicate Tasks Exist?}
    E -->|Yes| F[Update Existing Tasks<br/>mark completed items]
    E -->|No| G[Append New Tasks<br/>priority-based sections]
    F --> H[Generate Review Summary<br/>findings & recommendations]
    G --> H
    H --> I[Output Updated TASK.md<br/>actionable task format]

    style A fill:#e1f5fe,stroke:#01579b
    style C fill:#fff3e0,stroke:#e65100
    style D fill:#f3e5f5,stroke:#4a148c
    style I fill:#e8f5e8,stroke:#2e7d32
```

### 3. Project Understanding Workflow

The `prime` command provides a systematic approach to understanding any new codebase through structured analysis of documentation, structure, and dependencies.

```mermaid
flowchart TD
    A[Read Project README<br/>understand user perspective] --> B[Run git ls-files<br/>inventory project structure]
    B --> C[Examine Directory Architecture<br/>identify patterns & frameworks]
    C --> D[Read Core Documentation<br/>PLANNING.md & TASK.md]
    D --> E[Analyze Testing Strategy<br/>frameworks & coverage patterns]
    E --> F[Check Development Workflow<br/>CI/CD & quality tools]
    F --> G[Identify Data Models<br/>schemas & external integrations]
    G --> H[Validate Understanding<br/>answer key questions]
    H --> I{Understanding Complete?}
    I -->|No| J[Document Knowledge Gaps<br/>update documentation]
    I -->|Yes| K[Ready for Development Work]
    J --> L[Update TASK.md & PLANNING.md<br/>maintain project knowledge]

    style A fill:#e1f5fe,stroke:#01579b
    style D fill:#f3e5f5,stroke:#4a148c
    style H fill:#fff3e0,stroke:#e65100
    style K fill:#e8f5e8,stroke:#2e7d32
    style L fill:#fff9c4,stroke:#f57f17
```
