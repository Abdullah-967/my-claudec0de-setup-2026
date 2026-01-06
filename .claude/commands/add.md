# Create Custom Slash Command

You are a slash command generator expert. Your task is to create a new custom slash command based on the user's request.

## User Request
$ARGUMENTS

## Instructions

1. **Parse the request**: Extract the command name and description from the user's input. The format is typically `<command_name> <description>` (e.g., `greet A friendly greeting command`).

2. **Research best practices**: Search the web for best practices related to this specific type of command functionality. Look for:
   - Common patterns and conventions for similar commands
   - User experience best practices
   - Edge cases to handle
   - Security considerations if applicable

3. **Generate the command file**: Create a markdown file that follows Claude Code custom command best practices:

### Best Practices for Custom Commands

- **Clear purpose**: The command should do one thing well
- **Descriptive header**: Start with a clear `# Title` explaining the command
- **Context setting**: Provide Claude with the right context/role
- **Structured instructions**: Use numbered steps or clear sections
- **Input handling**: Use `$ARGUMENTS` to capture user input
- **Output format**: Specify the expected output format
- **Edge cases**: Handle missing arguments gracefully
- **Examples**: Include example usage in comments if helpful

### Command File Structure

```markdown
# Command Title

Brief description of what this command does.

## Context
Set the role/expertise Claude should assume.

## Input
$ARGUMENTS

## Instructions
1. Step one
2. Step two
3. etc.

## Output Format
Describe expected output format.

## Edge Cases
- Handle missing arguments
- Handle invalid input
```


4. **Save the file**:
   - Create the `.claude/commands/` directory in the current project if it doesn't exist
   - Write the generated command to the project's `.claude/commands/<command_name>.md` (relative to the current working directory)
   - Use the Write tool to save the file

## Output

After researching best practices, generate the complete command file and save it. Then provide:

1. A brief summary of the command you created
2. The best practices you incorporated
3. Example usage: `/command_name <example args>`

## Important Notes

- **Save location**: Always save commands to the project's `.claude/commands/` directory (not user-level)
- Command names should be lowercase, short (2-15 chars), and use hyphens for multi-word names
- Always include `$ARGUMENTS` placeholder for user input
- Keep the command focused - if it's complex, suggest breaking into multiple commands
- Consider what context/expertise Claude needs to execute the command well