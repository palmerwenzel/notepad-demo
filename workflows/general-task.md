# Feature Implementation Workflow

## Phase 0: Initialize Workflow State
FIRST:
    IF workflow-state.md appears to be mid-task:
        IF current task came from user:
            UPDATE workflow-state.md:
                - Add user request as new component task after most recently-completed component task
                - Request user approval to continue with new component task
                - Continue with new component task per existing state in workflow-state.md
        ELSE:
            Notify user that workflow-state.md appears to be mid-task, request user approval to continue with UPDATE workflow-state.md
    UPDATE workflow-state.md:
        - Set Project Stage if needed
        - Set Primary Workflow to "@workflows/general-task.md"
        - Set Primary Workflow Step to "Phase 1: Understanding"
        - Initialize Task section:
            - Clear Task Name and Description
            - Clear previous Component Tasks
            - Clear Current Component Task
        - Request user approval to continue with Phase 1: Understanding

## Phase 1: Understanding
FIRST:
    Gather feature requirements
    Identify affected areas
    Check similar implementations
    UPDATE workflow-state.md:
        - Add relevant files to "Files Read" array

IF requirements vague or unclear:
    ASK: for info/clarification
    WAIT: for response

IF similar code found:
    SHOW: relevant examples
    SUGGEST: adaptation strategy

## Phase 2: Planning
THEN:
    List files to create/modify
    Identify dependencies
    Plan implementation steps
    UPDATE workflow-state.md:
        - Add target files to "Files to Modify" array
        - Set "Primary Task" Name and Description

IF complex feature:
    BREAK INTO: smaller tasks
    UPDATE workflow-state.md:
        - Add tasks to "Derived Component Tasks" list
        - Set first task in "Current Component Task":
            - Set Name and Description
            - Add implementation steps

## Phase 3: Implementation
FOR EACH component task:
    UPDATE workflow-state.md:
        - Update "Current Component Task":
            - Set Name and Description
            - List implementation steps
    
    FIRST: verify context
    THEN: implement changes
    LAST: verify changes
    
    UPDATE workflow-state.md:
        - Check completed task in "Derived Component Tasks"
        - Update "Files Read" and "Files to Modify" arrays

IF creating new file:
    ADD: types and documentation
    FOLLOW: codebase rules

IF modifying file:
    PRESERVE: existing patterns
    MAINTAIN: file structure

## Phase 4: Verification
BEFORE completing:
    CHECK: all requirements met
    VERIFY: code consistency
    CONFIRM: no regressions

IF issues found:
    EXPLAIN: problems
    SUGGEST: solutions
    UPDATE workflow-state.md:
        - Add new items to "Derived Component Tasks"

## Phase 5: Submission
BEFORE continuing:
    CHECK: all requirements met
    VERIFY: code consistency
    CONFIRM: no regressions

IF issues found:
    EXPLAIN: problems
    SUGGEST: solutions
    UPDATE workflow-state.md:
        - Add new items to "Derived Component Tasks"

ELSE:
    REQUEST: user approval to continue to github-workflow.md

## Phase 6: Cleanup
UPDATE workflow-state.md:
    - Clear Current Component Task
    - Set Primary Workflow to "None"
    - Set Primary Workflow Step to "None" 