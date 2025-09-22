# write_mermaid_docs

## Description
Update the `README.md` in the given folder by analyzing the Python code, detecting **complex functions** and **main orchestrator functions** (those that coordinate many others), and representing their behavior with **Mermaid flowcharts**.  
Nodes must be explicit, showing the **business meaning / utility** of each step, not just raw function names (function names may appear in parentheses).  
Use colors and styles in Mermaid to make diagrams clearer and more readable.

## Arguments
- `$1` (required): Path to the folder containing the codebase.

## Instructions
1. **Parse the codebase in `$1`:**
   - Identify the most complex functions (based on length, branching, and nested calls).  
   - Identify orchestrator functions that coordinate multiple other functions or modules.

2. **Interpret function purpose:**
   - Derive the business meaning from function names, docstrings, and usage context.  
   - Express this meaning as explicit, user-oriented node labels.  
   - Optionally include the technical function name in parentheses.

3. **Generate Mermaid flowcharts:**
   - For each selected function, build a flowchart showing the main logical steps and calls.  
   - Use colors and styles (`style`, `fill`, `stroke`) to highlight:  
     - Entry/start nodes  
     - Decisions/branches  
     - External calls (DB, API, filesystem, services)  
     - Results/outputs  
   - Keep diagrams **simple and readable**: avoid trivial helper calls.

4. **Update `README.md`:**
   - Append a new section **“## Function Flowcharts”** (create if missing).  
   - Insert 2–3 Mermaid flowcharts (one per key function).  
   - Each diagram must be preceded by a short natural-language explanation.  

5. **Respect formatting:**
   - Use fenced code blocks with `mermaid`.  
   - Ensure diagrams render in GitHub/GitLab markdown preview.  
   - Only include the most meaningful functions (not every function).  

## Output
An updated `README.md` containing:
- A new **Function Flowcharts** section.  
- 2–3 clear and colorful Mermaid diagrams illustrating the main flows of the most important functions.  
- Explanatory text describing each diagram in plain language.
