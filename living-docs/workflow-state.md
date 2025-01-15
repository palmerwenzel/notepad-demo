# Workflow State

Project Stage: planning | initialization | implementation | completion # Current stage of entire project
Primary Workflow: <filepath> # File reference, "None" if no workflow is active
Primary Workflow Step: None # Current step in primary workflow
Secondary Workflow: <filepath> # File reference, "None" if no workflow is active
Secondary Workflow Step: None # Current step in secondary workflow

# Current Task (if active workflow is a task)

## Primary Task
Name: Task Name
Description: Task Description

## Derived Component Tasks
- [ ] Component Task 1
- [ ] Component Task 2
- [ ] Component Task 3

## Current Component Task
Name: Component Task 1
Description: Detailed description of current component task

### Steps
- [ ] Step 1
- [ ] Step 2
- [ ] Step 3

### Context
Files Read: [
    "path/to/file.ts:1-50"
]

Files to Modify: [
    "path/to/file.ts"
]