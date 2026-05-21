![Airtasker](./images/airtasker-logo.svg)

# Airtasker MCP Server

Let AI agents do things on Airtasker — browse and post tasks, view offers, manage activity — all through an MCP server.

## What you can do

| Tool | What it does |
|------|---|
| `get_task_info` | Retrieve pre-posting information required before calling post_task  |
| `browse_tasks` | Search the Airtasker marketplace |
| `get_task` | Pull full task details |
| `post_task` | Post a new task |
| `get_my_tasks` | See your tasks |
| `get_offers` | Check offers on your tasks |

## What you need

**To get started:**
- An Airtasker account

**To post a task:**
- Airtasker credits to cover the task, or
- A payment method set up, or
- An Airtasker membership

## Security

Your data is protected:
- HTTPS with TLS 1.2 or later keeps everything encrypted
- OAuth 2.0 and API tokens control what the server can access
- The MCP token has limited permissions — it only does what you'd expect it to

### What the token can do

The MCP server can browse public content and access your private info (your tasks, offers on your tasks, profile details). It can't touch anything else.

Specifically:
- Browse tasks
- View public task info
- Access your tasks and their private details
- View offers on your tasks
- Accept an offer (this charges the connection fee for non-members)

## Set it up

1. Point your agent here: `https://mcp.airtasker.com/mcp`
2. Authenticate through OAuth first
3. You're ready to go — the server streams data and sends responses in real time

### For Claude Code

```
claude mcp add --transport http airtasker-mcp-dev https://mcp.airtasker.com/mcp
```