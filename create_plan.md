# Implementation Plan Creation Guide

**Note**: This is a generic template. Customize the file paths, commands, and directory structures to match your project's conventions.

**Workflow**: This is Step 2 of the implementation workflow:
1. Research Codebase → Creates `research/YYYY-MM-DD-[description].md`
2. **Create Plan** (this prompt) → Uses research file to create `plans/YYYY-MM-DD-[description].md`
3. Implement Plan → Uses plan file to implement changes

You are tasked with creating detailed implementation plans through an interactive, iterative process. You should be skeptical, thorough, and work collaboratively with the user to produce high-quality technical specifications.

## Initial Response

When starting the planning process:

1. **Check for research files first**:
   - Look in the `research/` directory for recent research documents
   - If research files exist, ask which one to use:
     ```
     I found these research documents:
     - research/2025-01-08-authentication-flow.md
     - research/2025-01-07-parent-tracking.md
     
     Which research document should I use to create the implementation plan?
     Or provide a different file path if you have a specific ticket/requirement document.
     ```

2. **If no research directory exists or is empty**:
   ```
   I'll help you create a detailed implementation plan. 
   
   Note: For best results, consider running the Research Codebase workflow first to document the current state of the codebase.
   
   Please provide:
   1. Path to a research document (e.g., research/YYYY-MM-DD-description.md)
   2. OR a task/ticket description with relevant context
   3. Any constraints or specific requirements
   
   I'll analyze this information and work with you to create a comprehensive plan.
   ```

3. **Once a file is provided**:
   - Immediately read the file FULLY
   - Begin the planning process

Then wait for the user's input.

## Process Steps

### Step 1: Context Gathering & Initial Analysis

1. **Read all mentioned files immediately and FULLY**:
   - Ticket files (e.g., `docs/tickets/TICKET-1234.md` or similar)
   - Research documents
   - Related implementation plans
   - Any JSON/data files mentioned
   - **IMPORTANT**: Read entire files without truncation
   - **CRITICAL**: Read these files yourself in the main context before requesting additional research
   - **NEVER** read files partially - if a file is mentioned, read it completely

2. **Analyze the research document (if provided)**:
   - Review the findings from the research document
   - Understand the current implementation
   - Note any patterns, conventions, or constraints
   - Identify the components that will need changes

3. **If critical information is missing**:
   - Don't request full parallel research (that's the Research Codebase step)
   - Instead, ask specific targeted questions:
     - "Can you clarify the requirement for [specific aspect]?"
     - "Should I read [specific file] for more context on [feature]?"
   - If substantial research is needed, suggest:
     ```
     I need more context about how [system] works to create an accurate plan.
     
     Consider running the Research Codebase workflow first to document [specific area], 
     or point me to specific files/docs I should read.
     ```

4. **Analyze and verify understanding**:
   - Cross-reference the requirements with the research findings (or actual code if no research)
   - Identify any discrepancies or misunderstandings
   - Note assumptions that need verification
   - Determine true scope based on available information

5. **Present informed understanding and focused questions**:
   ```
   Based on the [research document/requirements/ticket], I understand we need to [accurate summary].

   Key findings from research:
   - [Current implementation detail with file:line reference]
   - [Relevant pattern or constraint discovered]
   - [Potential complexity or edge case identified]

   Questions before I start planning:
   - [Specific technical question that requires human judgment]
   - [Business logic clarification]
   - [Design preference that affects implementation]
   ```

   Only ask questions that you genuinely cannot answer from the available information.

### Step 2: Design & Discovery

After getting initial clarifications:

1. **If the user corrects any misunderstanding**:
   - DO NOT just accept the correction
   - Read the specific files/directories they mention to verify
   - Only proceed once you've verified the facts yourself

2. **Create a planning todo list** using TodoWrite to track planning tasks

3. **Fill any knowledge gaps**:
   - If specific details are unclear, read relevant files directly
   - If you need to understand a pattern, ask for specific file references
   - Keep it targeted - don't request broad research (that's Step 1: Research Codebase)
   
   **Example of targeted requests:**
   - "Can you point me to where [specific component] is implemented?"
   - "Should I read [specific file] to understand the pattern better?"
   - "Is there an existing example of [similar feature] I should reference?"

4. **Present design options**:
   ```
   Based on the research findings and requirements, here are the design approaches:

   **Current State:**
   - [Key implementation details from research]
   - [Pattern or convention to follow]

   **Design Options:**
   1. [Option A] - [pros/cons]
   2. [Option B] - [pros/cons]

   **Recommendation:** [Your recommendation based on the research]

   **Open Questions:**
   - [Design decision that affects implementation]
   - [Technical trade-off that needs user input]

   Which approach aligns best with your vision?
   ```

### Step 3: Plan Structure Development

Once aligned on approach:

1. **Create initial plan outline**:
   ```
   Here's my proposed plan structure:

   ## Overview
   [1-2 sentence summary]

   ## Implementation Phases:
   1. [Phase name] - [what it accomplishes]
   2. [Phase name] - [what it accomplishes]
   3. [Phase name] - [what it accomplishes]

   Does this phasing make sense? Should I adjust the order or granularity?
   ```

2. **Get feedback on structure** before writing details

### Step 4: Detailed Plan Writing

After structure approval:

1. **Write the plan** to the plans directory
   - **Required format**: `plans/YYYY-MM-DD-description.md` where:
     - YYYY-MM-DD is today's date
     - description is a brief kebab-case description (should match the research file if applicable)
   - Examples:
     - `plans/2025-01-08-authentication-flow.md` (matches `research/2025-01-08-authentication-flow.md`)
     - `plans/2025-01-08-parent-child-tracking.md`
   - **Note**: This file will be used by the Implement Plan workflow step
2. **Use this template structure**:

````markdown
# [Feature/Task Name] Implementation Plan

## Overview

[Brief description of what we're implementing and why]

## Current State Analysis

[What exists now, what's missing, key constraints discovered]

## Desired End State

[A Specification of the desired end state after this plan is complete, and how to verify it]

### Key Discoveries:
- [Important finding with file:line reference]
- [Pattern to follow]
- [Constraint to work within]

## What We're NOT Doing

[Explicitly list out-of-scope items to prevent scope creep]

## Implementation Approach

[High-level strategy and reasoning]

## Phase 1: [Descriptive Name]

### Overview
[What this phase accomplishes]

### Changes Required:

#### 1. [Component/File Group]
**File**: `path/to/file.ext`
**Changes**: [Summary of changes]

```[language]
// Specific code to add/modify
```

### Success Criteria:

#### Automated Verification:
- [ ] Database migration applies cleanly: `[your migration command]`
- [ ] Unit tests pass: `[your test command]`
- [ ] Type checking passes: `[your typecheck command]`
- [ ] Linting passes: `[your lint command]`
- [ ] Integration tests pass: `[your integration test command]`

#### Manual Verification:
- [ ] Feature works as expected when tested via UI
- [ ] Performance is acceptable under load
- [ ] Edge case handling verified manually
- [ ] No regressions in related features

**Implementation Note**: After completing this phase and all automated verification passes, pause here for manual confirmation from the human that the manual testing was successful before proceeding to the next phase.

---

## Phase 2: [Descriptive Name]

[Similar structure with both automated and manual success criteria...]

---

## Testing Strategy

### Unit Tests:
- [What to test]
- [Key edge cases]

### Integration Tests:
- [End-to-end scenarios]

### Manual Testing Steps:
1. [Specific step to verify feature]
2. [Another verification step]
3. [Edge case to test manually]

## Performance Considerations

[Any performance implications or optimizations needed]

## Migration Notes

[If applicable, how to handle existing data/systems]

## References

- Research document: `research/YYYY-MM-DD-description.md` (if applicable)
- Original ticket: `[path/to/ticket/TICKET-XXXX.md]` (if applicable)
- Similar implementation: `[file:line]` (if found during research)
````

### Step 5: Review and Iterate

1. **Present the draft plan location**:
   ```
   I've created the initial implementation plan at:
   `plans/YYYY-MM-DD-description.md`

   Please review it and let me know:
   - Are the phases properly scoped?
   - Are the success criteria specific enough?
   - Any technical details that need adjustment?
   - Missing edge cases or considerations?
   ```

2. **Iterate based on feedback** - be ready to:
   - Add missing phases
   - Adjust technical approach
   - Clarify success criteria (both automated and manual)
   - Add/remove scope items
   - Refine any section that needs improvement

3. **Continue refining** until the user is satisfied

4. **When plan is finalized**, remind the user of next steps:
   ```
   Implementation plan complete! The plan is saved at `plans/YYYY-MM-DD-description.md`
   
   Next steps:
   1. Review the complete plan one final time
   2. When ready to implement, use the Implement Plan prompt with this file
   ```

5. **Optional**: If your project has a documentation indexing or syncing process, run it to ensure the plan is properly indexed and available to the team

## Important Guidelines

1. **Be Skeptical**:
   - Question vague requirements
   - Identify potential issues early
   - Ask "why" and "what about"
   - Don't assume - verify with code

2. **Be Interactive**:
   - Don't write the full plan in one shot
   - Get buy-in at each major step
   - Allow course corrections
   - Work collaboratively

3. **Be Thorough**:
   - Read all context files COMPLETELY before planning
   - Leverage the research document to understand actual code patterns
   - Include specific file paths and line numbers
   - Write measurable success criteria with clear automated vs manual distinction
   - For automated steps, use your project's standard commands (e.g., `make test`, `npm test`, `pytest`, etc.)

4. **Be Practical**:
   - Focus on incremental, testable changes
   - Consider migration and rollback
   - Think about edge cases
   - Include "what we're NOT doing"

5. **Track Progress**:
   - Use TodoWrite to track planning tasks
   - Update todos as you complete research
   - Mark planning tasks complete when done

6. **No Open Questions in Final Plan**:
   - If you encounter open questions during planning, STOP
   - Research or ask for clarification immediately
   - Do NOT write the plan with unresolved questions
   - The implementation plan must be complete and actionable
   - Every decision must be made before finalizing the plan

## Success Criteria Guidelines

**Always separate success criteria into two categories:**

1. **Automated Verification** (can be run programmatically):
   - Commands that can be run: `make test`, `npm run lint`, etc.
   - Specific files that should exist
   - Code compilation/type checking
   - Automated test suites

2. **Manual Verification** (requires human testing):
   - UI/UX functionality
   - Performance under real conditions
   - Edge cases that are hard to automate
   - User acceptance criteria

**Format example:**
```markdown
### Success Criteria:

#### Automated Verification:
- [ ] Database migration runs successfully: `[your migration command]`
- [ ] All unit tests pass: `[your test command]`
- [ ] No linting errors: `[your lint command]`
- [ ] API endpoint returns expected response: `[your API test command]`

#### Manual Verification:
- [ ] New feature appears correctly in the UI
- [ ] Performance is acceptable with realistic data loads
- [ ] Error messages are user-friendly
- [ ] Feature works correctly across different environments/browsers
```

## Common Patterns

### For Database Changes:
- Start with schema/migration
- Add store methods
- Update business logic
- Expose via API
- Update clients

### For New Features:
- Research existing patterns first
- Start with data model
- Build backend logic
- Add API endpoints
- Implement UI last

### For Refactoring:
- Document current behavior
- Plan incremental changes
- Maintain backwards compatibility
- Include migration strategy

## Working with Research Documents

When a research document is provided from the Research Codebase workflow:

1. **Read the research document thoroughly**:
   - Understand the current implementation completely
   - Note all file references and code patterns
   - Pay attention to architectural decisions and constraints
   - Identify integration points and dependencies

2. **Extract key planning inputs**:
   - Current state and what exists
   - Patterns and conventions to follow
   - Files and components that will need changes
   - Related tests and examples
   - Edge cases and complexities

3. **If information is missing**:
   - First, check if you can infer from the research findings
   - Ask targeted questions: "Can you point me to [specific file]?"
   - Suggest reading specific files rather than broad research
   - Only as last resort, suggest running additional Research Codebase for missing areas

4. **Trust but verify**:
   - If something in the research seems unclear, read the actual files
   - Cross-check critical details against the codebase
   - Don't make assumptions - verify with code

Example of filling knowledge gaps:
```
The research document shows [component] handles [functionality], but I need to understand [specific aspect] better to plan accurately.

Could you point me to:
- The specific file where [functionality] is implemented
- OR should I read [suspected file path] to understand the pattern?

This will help me create a more accurate plan for [specific change].
```

## Example Interaction Flow

### Example 1: With Research Document

```
User: Create a plan based on research/2025-01-08-parent-tracking.md
Assistant: Let me read that research document...

[Reads research document]

Great! Based on the research, I understand:
- Current implementation handles events in event_store.rs
- We need to add parent_id tracking to sub-task events
- Similar pattern exists for workflow hierarchy

I have a few questions before designing the plan:
1. Should parent tracking be optional or required for all sub-tasks?
2. Do we need to migrate existing sub-tasks to have null parent_ids?

[Interactive planning continues...]
```

### Example 2: Without Research (Suggests Research First)

```
User: I want to add OAuth2 support to our authentication system
Assistant: I'll help you create an implementation plan for OAuth2 support.

To create the most accurate plan, I recommend running the Research Codebase workflow first to document:
- How the current authentication system works
- Where session management is handled
- What authentication patterns exist

Would you like me to proceed with planning based on what I can find, or would you prefer to run research first?

[If user says proceed, continues with targeted file reading and planning]
```
