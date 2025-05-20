Here are the implementation files to review:

<implementation_files>
- `server/resolvers/stack_mutations.go`
- `server/resolvers/stack_mutations_update.go`
- `server/resolvers/run_mutations.go`
</implementation_files>

You are an experienced software developer tasked with creating documentation about currently available actions used for authorization purposes. This documentation will be used by both end customers and frontend developers. Your goal is to create a clear, comprehensive table that maps backend implementation actions to their GraphQL counterparts and provides descriptions of each action.

Your task is to create a table with the following columns:
1. Action (implementation): The enum derived from the implementation in `database/rbac.go`
2. Action (GraphQL): The corresponding enum derived from the GraphQL schema in `server/resolvers/schema/schema.gohtml`
3. Description: A clear explanation of the action's purpose, based on the corresponding GraphQL mutation implementation

Instructions:
1. Analyze the implementation files to identify actions used in the mutation code. For example, if `database.ActionStackLock` is used in the `StackLock` method, it should be included in the table.
2. For each identified action:
   a. Determine the Action (implementation) name from `database/rbac.go`
   b. Find the corresponding Action (GraphQL) name in `server/resolvers/schema/schema.gohtml`
   c. Write a description based on the related GraphQL mutation implementation (e.g., in `server/resolvers/stack_mutations.go` for stack-related actions)
3. Compile the information into a table format as shown in the example below.

Before creating the final table, wrap your analysis process in <action_analysis> tags. In this section:
- List out all the actions found in the implementation files.
- For each action:
  a. Quote the relevant code snippet from the implementation files.
  b. Identify the corresponding GraphQL action.
  c. Summarize the purpose of the action based on the mutation implementation.
It's OK for this section to be quite long.

Example table format:

| Action (implementation) | Action (GraphQL) | Description |
|-------------------------|-------------------|-------------|
| `ActionExample`         | `EXAMPLE`         | Generic description of the action's purpose |

Please proceed with your analysis and documentation creation.
