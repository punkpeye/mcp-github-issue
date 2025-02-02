# MCP GitHub Issue Server

An MCP server that provides LLMs with the ability to use GitHub issues as the task to complete. This server allows LLMs to fetch GitHub issue details and use them as task descriptions.

## Installation

```bash
npx -y mcp-github-issue
```

## Usage

### As an MCP Server

Add to your MCP configuration:

```json
{
  "mcpServers": {
    "github-issue": {
      "command": "npx",
      "args": ["-y", "mcp-github-issue"]
    }
  }
}
```

### Available Tools

#### get_issue_task

Fetches GitHub issue details to use as a task.

**Input Schema:**
```json
{
  "type": "object",
  "properties": {
    "url": {
      "type": "string",
      "description": "GitHub issue URL (https://github.com/owner/repo/issues/number)"
    }
  },
  "required": ["url"]
}
```

**Example Usage:**
```typescript
<use_mcp_tool>
<server_name>github-issue</server_name>
<tool_name>get_issue_task</tool_name>
<arguments>
{
  "url": "https://github.com/owner/repo/issues/123"
}
</arguments>
</use_mcp_tool>
```

**Response Format:**
```json
{
  "task": {
    "title": "Issue Title",
    "description": "Issue Description/Body",
    "source": "https://github.com/owner/repo/issues/123"
  }
}
```

## Features

- Fetches GitHub issue details from public repositories
- No authentication required for public repositories
- Returns structured task data including title, description, and source URL
- Compatible with the Model Context Protocol (MCP)

## Development

```bash
# Install dependencies
npm install

# Build the project
npm run build

# Run the server locally
npm run serve

# Format code
npm run format

# Run MCP inspector
npm run inspector
```

## License

MIT

## Author

Sam McLeod (https://smcleod.net)
