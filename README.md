# IDE Workflow Prompts

Structured prompts for systematic code research, planning, and implementation in an AI enabled IDE.

Adapted from [HumanLayer's Claude commands](https://github.com/humanlayer/humanlayer/blob/main/.claude/commands), modified to use manual parallel research tabs instead of autonomous agents.

## Three-Step Workflow

1. **Research Codebase** → Document existing code
2. **Create Plan** → Design implementation strategy  
3. **Implement Plan** → Execute with verification

## Workflow Steps

| Step | Prompt File | Output | Purpose |
|------|------------|--------|---------|
| 1 | `research_codebase.md` | `research-plans/research-*.md` | Document existing code (no suggestions, pure documentation) |
| 2 | `create_plan.md` | `research-plans/plan-*.md` | Create phased implementation plan with success criteria |
| 3 | `implement_plan.md` | - | Execute plan phase-by-phase with verification |

## Quick Start

1. **Setup**: Create directory and customize prompts for your project
   ```bash
   mkdir -p research-plans
   ```

2. **Customize**: Update file paths, test commands, and directory names in the prompt files

3. **Use**: Copy entire prompt file into Cursor, add your request, and follow the interactive workflow

## Usage Examples

**Step 1 - Research:**
```
[Paste research_codebase.md content]
---
How does user authentication work? I need to understand login flow, session management, and tokens.
```

**Step 2 - Plan:**
```
[Paste create_plan.md content]
---
Create plan from research-plans/research-2025-01-08-authentication-flow.md to add OAuth2 support.
```

**Step 3 - Implement:**
```
[Paste implement_plan.md content]
---
Implement research-plans/plan-2025-01-08-add-oauth2-support.md
```