# Instruction

You are an experienced DevOps engineer tasked with creating a bash script that
automates a complex development workflow. The script will create multiple tmux
sessions, each dedicated to a specific item from a list, and perform a series
of git operations and code modifications.


## List of <item>:
- StackReslug
- StackManagedStateImport
- StackManagedStateRollback
- StackConfigAdd

## Steps
Your task is to create a bash script named 'fan-out.sh' that implements the
following workflow for each <item> in the list above:

1. In tmux session, Go to `$HOME/repos/spacelift-io/backend` 
2. In tmux session, Create branch `feat-action-based-authz-<item>` based on `main` using `git branch`
  - just create, don't checkout
3. In tmux session, Create new git worktree based on the branch in `%HOME/repos/spacelift-io/backend/.worktrees/<branch>`
4. In tmux session, Go to the worktree
5. Outside tmux, wait 5 seconds 
6. In tmux session, Execute 
<bash_script>
allowedTools="Bash(git checkout:*),Bash(git fetch:*),"
allowedTools="${allowedTools}Bash(go test:*),Bash(golangci-lint run:*)"
allowedTools="${allowedTools}Bash(grep:*),Bash(cat:*)"
claude "
You are a skilled software developer tasked with making changes to a codebase
and creating a pull request. Your task involves analyzing a specific commit,
applying changes, adding tests, ensuring code quality, and creating a pull
request. Please follow these instructions carefully:
## Steps
1. Analyze a commit fd26b9b56aa231467aefb9c52217443ca9f43d8c. 
2. Based on that apply the same changes for <item> mutation in server/resolvers/stack_mutations.go. 
3. Add a test with a suffix _ff_on()
4. Make sure tests and linting are working.
5. Ensure that all tests pass and that the code adheres to linting standards.
6. Create two separate commits:
   a. First commit: All changes except tests
   b. Second commit: Only the test changes
7. Create a new Pull Request based on the template found in .github/pull_request_template.md.
## Work organization
  - Create TODO list and keep it up to date
" --allowedTools "$allowedTools"
</bash_script>

## Bash best practises
Before writing the script, please think through the implementation details, potential issues, and error handling strategies. 

In your script, make sure to include:

1. A function that creates a tmux session (if it doesn't exist) and runs the required commands within it
2. A loop that iterates over the items list and calls the above function for each item
3. Error handling for each major operation (e.g., git commands, tmux session creation)
  - don't use exit/return so I can see the actual errors
4. The 'claude' command execution with the specified instructions
5. Any necessary cleanup operations
6. Use `EOF` syntax to handle multiline commands in bash
7. Wait 1s between eash `tmux send-key`

## Work organization
- Create TODO list and keep it up to date
