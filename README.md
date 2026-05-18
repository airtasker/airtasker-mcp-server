![Airtasker](./images/airtasker-logo.svg)

# Airtasker MCP Server

The Airtasker MCP server exposes Airtasker actions as structured tools for AI agents. It allows AI agents to interact with Airtasker on behalf of users — browsing and posting tasks, viewing offers, and managing task activity.

## Available tools

| Tool | Description |
|------|-------------|
| `get_task_info` | Retrieve public information about a task |
| `browse_tasks` | Search and browse available tasks |
| `get_task` | Fetch full task details |
| `post_task` | Create a new task |
| `get_my_tasks` | List tasks posted by the authenticated user |
| `get_offers` | View offers on a task |

Authentication uses Auth0 OAuth 2.0 Device Flow.

## Before you start
Ensure you meet the necessary requirements to successfuly connec to the Airtasker MCP Server.

### Prerequisites 
* Airtasker login 

### Prerequisites for Posting Tasks
* Either:
  * Airtasker credits that cover the full value of the task
  * Payment method configured

## Data and security
Security is a core focus of the Airtasker MCP Server:

* All traffic is encrypted via HTTPS using TLS 1.2 or later.
* OAuth 2.1 and API token authentication provide secure access control.
* The token accquired via the mcp server has limitations in which actions can be performed at Airtasker 

### Functions allowed with the Airtasker MCP token
A lot of the content at Airtasker is public. However, some bits of information are private to the user, for example specific details on their profiles, or price of offers made on their tasks. The list below will use the terminology **private** to indicate the pieces of information that are usually not displayed unless it pertains to the current logged in user.

* Browse Tasks
* Get public task information
* Get current user tasks
* Get private details on current user tasks
* View offers on users's tasks with private details
* Accept an offer (this will charge the connection fee for users without the Airtasker membership)

## How to configure

1. An AI agent will use the endpoint to connect:

```
https://mcp.airtasker.com/mcp
```

2. You will need to authenticate with the OAuth flow before you are able to use the server
3. Once authorized, the client streams contextual data and receives real-time responses from the Airtasker services.

### Claude Code
To add the MCP server to Claude Code use the following:

```
claude mcp add --transport http airtasker-mcp-dev https://mcp.airtasker.com/mcp
```