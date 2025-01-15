# GitHub Workflow
All context needed for this workflow is in workflow-state.md

FIRST:
    CHECK: current branch
    ```bash
    git status
    ```

    IF current branch is not 'main':
        ASK: user permission to continue
        WAIT: for user confirmation

    DETERMINE: branch name from Primary Task in workflow-state.md:
        IF bug fix:
            USE: fix/task-name
        IF new feature:
            USE: feat/task-name
        IF documentation:
            USE: docs/task-name
        IF refactor:
            USE: refactor/task-name
        IF performance:
            USE: perf/task-name
        
        THEN:
            CONVERT: spaces to dashes
            ENSURE: lowercase only
            REMOVE: special characters

    CREATE: new branch from main
    ```bash
    git checkout -b <branch-type>/<task-name>
    ```

THEN:
    CREATE: temporary commit message file:
    ```bash
    touch commit-message.md
    ```
    
    EDIT commit-message.md:
        - Add task description
        - List changes made
        - Follow commit message conventions
    
    EXECUTE: commit with message file
    ```bash
    git commit -F commit-message.md
    ```

    CLEANUP: temporary commit file
    ```bash
    rm commit-message.md
    ```

    PUSH: branch to remote
    ```bash
    git push -u origin <branch-name>
    ```

IF push fails:
    ASK: user to check remote configuration
    WAIT: for user to confirm

THEN:
    CREATE: PR description file
    ```bash
    touch pr-description.md
    ```

    EDIT pr-description.md:
        - List completed component tasks
        - Detail changes made
        - Include impact statement

    CREATE: PR using description
    ```bash
    gh pr create --title "feat: [task-name]" --body-file pr-description.md --base main
    ```

    CLEANUP: temporary PR file
    ```bash
    rm pr-description.md
    ```

IF PR creation fails:
    ASK: user to check GitHub CLI authentication
    ASK: user to check repository permissions
