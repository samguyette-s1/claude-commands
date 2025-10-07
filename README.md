# Cursor AI Workflow Prompts

A collection of structured prompts for using Cursor AI to research codebases, plan implementations, and execute development work systematically.

## Attribution

These prompts were adapted from the [HumanLayer project's Claude commands](https://github.com/humanlayer/humanlayer/blob/main/.claude/commands). The original approach used autonomous agents that could spawn sub-agents. This version has been modified to work with Cursor (or any AI coding assistant) by replacing agent spawning with user-driven parallel research in separate tabs.

**Key Changes:**
- Removed autonomous agent spawning
- Replaced with manual parallel Cursor tab workflow
- Generalized all file paths, commands, and directory structures
- Made suitable as templates for any project

## Overview

These prompts guide Cursor through a three-step workflow for tackling development tasks:

1. **Research Codebase** → Document and understand existing code
2. **Create Plan** → Design a detailed implementation strategy  
3. **Implement Plan** → Execute the plan with verification steps

## The Workflow

### Step 1: Research Codebase
**File**: `research_codebase.md`

Use this prompt to thoroughly document how existing code works before making changes.

**Creates**: `research/YYYY-MM-DD-description.md`

**Key Features**:
- Documents what exists (not what should be)
- Coordinates parallel research investigations
- Generates markdown documentation with code references
- No suggestions or critiques - pure documentation

### Step 2: Create Plan
**File**: `create_plan.md`

Use this prompt to create a detailed, phase-based implementation plan.

**Creates**: `plans/YYYY-MM-DD-description.md`

**Key Features**:
- Interactive, iterative planning process
- Phases with specific changes and success criteria
- Automated and manual verification steps
- Links back to research documentation

### Step 3: Implement Plan
**File**: `implement_plan.md`

Use this prompt to execute the implementation plan systematically.

**Uses**: `plans/YYYY-MM-DD-description.md`

**Key Features**:
- Phase-by-phase implementation
- Checkboxes for tracking progress
- Automated verification before manual testing
- Pauses for human verification between phases

## Getting Started

### 1. Set Up Directories

```bash
mkdir -p research-plans
```

### 2. Customize the Prompts

These are generic templates. Before using them:

- Update file paths to match your project structure
- Customize commands (e.g., `make test`, `npm test`, `pytest`)
- Adjust directory names if needed
- Modify the plan template structure for your needs

### 3. Use the Workflow

**Start a new task:**

```
1. Copy research_codebase.md content into Cursor
2. Provide your research question
3. Review generated research/YYYY-MM-DD-description.md

4. Copy create_plan.md content into Cursor  
5. Reference the research file
6. Iterate on the plan until satisfied
7. Review generated plans/YYYY-MM-DD-description.md

8. Copy implement_plan.md content into Cursor
9. Reference the plan file
10. Execute phase by phase with verification
```

## Directory Structure

After running the workflow, your project will have:

```
project/
├── research/
│   ├── 2025-01-08-authentication-flow.md
│   └── 2025-01-08-parent-tracking.md
├── plans/
│   ├── 2025-01-08-authentication-flow.md
│   └── 2025-01-08-parent-tracking.md
└── [your source code]
```

## Workflow Features

### Automatic File Discovery
Each prompt automatically checks for files from previous steps and lists them for selection.

### Consistent Naming
Files use `YYYY-MM-DD-description.md` format for easy matching across research and plans.

### Parallel Research
The workflow requests users to open multiple Cursor tabs for parallel investigations, maximizing efficiency while managing context.

### Progressive Enhancement
- Research step is optional but recommended
- Each step can work independently
- Alternative file paths can be provided

## Usage Example

### How to Use These Prompts

**Recommended approach:** Copy the entire prompt file content into Cursor, then add your specific request.

#### Example: Research Codebase

```
[Copy entire research_codebase.md content and paste into Cursor]

---

My research question: How does user authentication work in this application? 
I need to understand the login flow, session management, and token handling.
```

Cursor will then:
1. Ask you to open parallel research tabs with specific questions
2. Wait for you to paste back the findings
3. Synthesize everything into a research document
4. Save it to `research/2025-01-08-authentication-flow.md`

#### Example: Create Plan

```
[Copy entire create_plan.md content and paste into Cursor]

---

Please create an implementation plan based on research/2025-01-08-authentication-flow.md

I want to add OAuth2 support to the existing authentication system.
```

#### Example: Implement Plan

```
[Copy entire implement_plan.md content and paste into Cursor]

---

Please implement plans/2025-01-08-add-oauth2-support.md
```

### Good Research Questions

- "How does the payment processing system work?"
- "How are file uploads handled from upload to storage?"
- "What happens when a user creates a new order? Trace the complete data flow."
- "How does the application integrate with the external email service?"

