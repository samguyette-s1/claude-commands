# Implementation Plan Execution Guide

**Note**: This is a generic template. Customize the file paths, commands, and verification steps to match your project's conventions.

**Workflow**: This is Step 3 of the implementation workflow:
1. Research Codebase → Creates `research-plans/research-YYYY-MM-DD-[description].md`
2. Create Plan → Creates `research-plans/plan-YYYY-MM-DD-[description].md`
3. **Implement Plan** (this prompt) → Uses plan file to implement changes

You are tasked with implementing an approved technical plan. These plans contain phases with specific changes and success criteria.

## Getting Started

**First, check for plan files:**

1. **If no plan path provided**:
   - Check if a `research-plans/` directory exists and look for files starting with `plan-`
   - If plans exist, list them:
     ```
     I found these implementation plans:
     - research-plans/plan-2025-01-08-authentication-flow.md
     - research-plans/plan-2025-01-07-parent-tracking.md
     
     Which plan should I implement?
     ```
   - If no research-plans directory or no plan files:
     ```
     No implementation plans found in the `research-plans/` directory.
     
     Please either:
     1. Provide the path to an existing implementation plan
     2. Run the Create Plan workflow first to generate a plan
     
     The typical workflow is:
     1. Research Codebase (optional but recommended)
     2. Create Plan (required)
     3. Implement Plan (this step)
     ```

2. **When given a plan path**:
   - Read the plan completely and check for any existing checkmarks (- [x])
   - Read the original ticket and all files mentioned in the plan
   - **Read files fully** - always read complete files for full context
   - Think deeply about how the pieces fit together
   - Create a todo list to track your progress
   - Start implementing if you understand what needs to be done

## Implementation Philosophy

Plans are carefully designed, but reality can be messy. Your job is to:
- Follow the plan's intent while adapting to what you find
- Implement each phase fully before moving to the next
- Verify your work makes sense in the broader codebase context
- Update checkboxes in the plan as you complete sections

When things don't match the plan exactly, think about why and communicate clearly. The plan is your guide, but your judgment matters too.

If you encounter a mismatch:
- STOP and think deeply about why the plan can't be followed
- Present the issue clearly:
  ```
  Issue in Phase [N]:
  Expected: [what the plan says]
  Found: [actual situation]
  Why this matters: [explanation]

  How should I proceed?
  ```

## Verification Approach

After implementing a phase:
- Run the success criteria checks specified in the plan (e.g., test commands, lint checks, etc.)
- Fix any issues before proceeding
- Update your progress in both the plan and your todos
- Check off completed items in the plan file itself
- **Pause for human verification**: After completing all automated verification for a phase, pause and inform the user that the phase is ready for manual testing. Use this format:
  ```
  Phase [N] Complete - Ready for Manual Verification

  Automated verification passed:
  - [List automated checks that passed]

  Please perform the manual verification steps listed in the plan:
  - [List manual verification items from the plan]

  Let me know when manual testing is complete so I can proceed to Phase [N+1].
  ```

If instructed to execute multiple phases consecutively, skip the pause until the last phase. Otherwise, assume you are just doing one phase.

Do not check off items in the manual testing steps until confirmed by the user.


## If You Get Stuck

When something isn't working as expected:
- First, make sure you've read and understood all the relevant code
- Consider if the codebase has evolved since the plan was written
- Present the mismatch clearly and ask for guidance
- If you need additional research, ask the user to open a separate Cursor tab to investigate specific aspects

## Resuming Work

If the plan has existing checkmarks:
- Trust that completed work is done
- Pick up from the first unchecked item
- Verify previous work only if something seems off

Remember: You're implementing a solution, not just checking boxes. Keep the end goal in mind and maintain forward momentum.
