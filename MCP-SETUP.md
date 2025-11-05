# MCP Server Setup Guide

This guide explains how to attach and configure MCP (Model Context Protocol) servers to extend Claude's capabilities with external tools, APIs, and services.

## What are MCP Servers?

MCP servers are different from skills:
- **Skills** are markdown files that teach Claude how to perform tasks
- **MCP Servers** are running processes that connect Claude to external APIs, databases, and services

MCP servers expose **tools** (functions Claude can call) and **resources** (data Claude can access with @ mentions).

---

## Table of Contents

1. [Quick Start](#quick-start)
2. [Configuration Methods](#configuration-methods)
3. [Claude Code Setup](#claude-code-setup)
4. [Claude Desktop App Setup](#claude-desktop-app-setup)
5. [Popular MCP Servers](#popular-mcp-servers)
6. [Transport Types](#transport-types)
7. [Managing MCP Servers](#managing-mcp-servers)
8. [Troubleshooting](#troubleshooting)

---

## Quick Start

### Using Claude Code CLI (Recommended)

The easiest way to add MCP servers to Claude Code:

```bash
# Add an MCP server (interactive wizard)
claude mcp add server-name --scope user

# List all configured servers
claude mcp list

# Remove a server
claude mcp remove server-name

# View MCP servers in a running session
/mcp
```

### Example: Adding GitHub MCP Server

```bash
# Add GitHub MCP server with HTTP transport
claude mcp add github --scope user
```

---

## Configuration Methods

### Method 1: CLI Wizard (Easiest)

Use the interactive CLI to configure servers:

```bash
claude mcp add [server-name] --scope user
```

The wizard will prompt you for:
- Transport type (http, stdio)
- Server URL or command
- Environment variables (API keys, tokens)

### Method 2: Direct File Edit (Advanced)

For complex configurations, edit the config file directly.

**Config file location:**
```
~/.claude.json
```

---

## Claude Code Setup

### Configuration File Structure

Claude Code stores MCP server configuration in `~/.claude.json` under the `mcpServers` field:

```json
{
  "projects": {
    "/path/to/project": {
      "mcpServers": {
        "server-name": {
          "transport": "http",
          "url": "https://api.example.com/mcp"
        }
      }
    }
  }
}
```

### HTTP Transport (Recommended for Remote Services)

Best for connecting to remote MCP servers:

```bash
# Add HTTP MCP server
claude mcp add notion --transport http https://mcp.notion.com/mcp
```

**Manual configuration:**
```json
{
  "projects": {
    "/home/user/awesome-claude-skills": {
      "mcpServers": {
        "notion": {
          "transport": "http",
          "url": "https://mcp.notion.com/mcp",
          "headers": {
            "Authorization": "Bearer YOUR_API_TOKEN"
          }
        }
      }
    }
  }
}
```

### Stdio Transport (For Local Processes)

Best for running local MCP servers:

```bash
# Add stdio MCP server with environment variables
claude mcp add github-local \
  -e GITHUB_TOKEN=your_github_token \
  -- npx -y @modelcontextprotocol/server-github
```

**Manual configuration:**
```json
{
  "projects": {
    "/home/user/awesome-claude-skills": {
      "mcpServers": {
        "github-local": {
          "transport": "stdio",
          "command": "npx",
          "args": ["-y", "@modelcontextprotocol/server-github"],
          "env": {
            "GITHUB_TOKEN": "your_github_token"
          }
        }
      }
    }
  }
}
```

### Scope Levels

MCP servers can be configured at three scope levels:

1. **User scope** (`--scope user`)
   - Available across all projects for the user
   - Best for personal tooling you'll reuse
   - Location: Global user config

2. **Project scope** (default)
   - Only available in the current project
   - Best for project-specific integrations
   - Location: Project-specific config

3. **System scope** (`--scope system`)
   - Available system-wide for all users
   - Best for organization-wide tools
   - Requires admin privileges

**Recommended:** Use `--scope user` for most personal MCP servers.

---

## Claude Desktop App Setup

For Claude Desktop (macOS/Windows):

### Configuration File Locations

**macOS:**
```
~/Library/Application Support/Claude/claude_desktop_config.json
```

**Windows:**
```
%APPDATA%\Claude\claude_desktop_config.json
```

### Example Configuration

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "your_github_token"
      }
    },
    "notion": {
      "command": "npx",
      "args": ["-y", "@notionhq/mcp-server"],
      "env": {
        "NOTION_API_KEY": "your_notion_key"
      }
    }
  }
}
```

After editing, restart Claude Desktop.

---

## Popular MCP Servers

### 1. GitHub MCP Server
Connect to GitHub repositories, issues, and PRs.

```bash
claude mcp add github -e GITHUB_TOKEN=your_token -- npx -y @modelcontextprotocol/server-github
```

### 2. Filesystem MCP Server
Access local files and directories.

```bash
claude mcp add filesystem -- npx -y @modelcontextprotocol/server-filesystem /path/to/directory
```

### 3. Brave Search MCP Server
Web search capabilities.

```bash
claude mcp add brave-search -e BRAVE_API_KEY=your_key -- npx -y @modelcontextprotocol/server-brave-search
```

### 4. PostgreSQL MCP Server
Database access and queries.

```bash
claude mcp add postgres -e DATABASE_URL=postgresql://... -- npx -y @modelcontextprotocol/server-postgres
```

### 5. Puppeteer MCP Server
Browser automation.

```bash
claude mcp add puppeteer -- npx -y @modelcontextprotocol/server-puppeteer
```

### 6. Slack MCP Server
Slack integration.

```bash
claude mcp add slack -e SLACK_BOT_TOKEN=your_token -e SLACK_TEAM_ID=your_team -- npx -y @modelcontextprotocol/server-slack
```

### 7. Google Drive MCP Server
Google Drive access.

```bash
claude mcp add google-drive -- npx -y @modelcontextprotocol/server-gdrive
```

---

## Transport Types

### HTTP Transport
- **Best for:** Remote MCP servers, cloud services
- **Pros:** Simple, secure (HTTPS), no local processes
- **Cons:** Requires server to be running remotely

```json
{
  "transport": "http",
  "url": "https://api.example.com/mcp",
  "headers": {
    "Authorization": "Bearer TOKEN"
  }
}
```

### Stdio Transport
- **Best for:** Local MCP servers, command-line tools
- **Pros:** Fast, no network overhead, runs locally
- **Cons:** Requires Node.js/Python installed

```json
{
  "transport": "stdio",
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-github"],
  "env": {
    "API_KEY": "your_key"
  }
}
```

### SSE Transport (Deprecated)
- Server-Sent Events transport
- **Not recommended:** Being phased out in favor of HTTP

---

## Managing MCP Servers

### List All Servers

```bash
# CLI command
claude mcp list

# Or in a Claude Code session
/mcp
```

### Remove a Server

```bash
claude mcp remove server-name
```

### Update Server Configuration

Edit the config file directly or remove and re-add:

```bash
claude mcp remove github
claude mcp add github -e GITHUB_TOKEN=new_token -- npx -y @modelcontextprotocol/server-github
```

### Verify Server is Working

After adding a server:
1. Restart Claude Code: `exit` then `claude`
2. Check server list: `claude mcp list`
3. Try using server tools in a chat
4. Use @ mentions to access server resources

---

## Troubleshooting

### Server Not Appearing

**Check configuration:**
```bash
claude mcp list
cat ~/.claude.json | grep -A 10 mcpServers
```

**Restart Claude Code:**
```bash
exit
claude
```

### Authentication Errors

**Verify environment variables:**
```bash
# Check if API key is set correctly in config
cat ~/.claude.json | grep -A 5 "server-name"
```

**Update API keys:**
```bash
# Remove and re-add with correct credentials
claude mcp remove server-name
claude mcp add server-name -e API_KEY=correct_key -- command
```

### Server Timeout

**For stdio transport:**
- Ensure Node.js/Python is installed
- Check server package is available: `npx -y @modelcontextprotocol/server-github --version`

**For HTTP transport:**
- Verify server URL is accessible: `curl https://api.example.com/mcp`
- Check network connectivity

### Permission Denied

**For system scope:**
```bash
# Use sudo for system-wide installation
sudo claude mcp add server-name --scope system
```

**For user/project scope:**
```bash
# Check file permissions
ls -la ~/.claude.json
chmod 600 ~/.claude.json
```

---

## Docker MCP Toolkit

For 200+ pre-built MCP servers with one-click deployment:

**Install Docker Desktop MCP Toolkit:**
1. Install Docker Desktop
2. Enable MCP integration in Docker settings
3. Browse available MCP servers
4. One-click deploy and configure

**Benefits:**
- 200+ containerized MCP servers
- Automatic credential handling
- Easy updates and management
- No local dependencies required

---

## Advanced: Creating Custom MCP Servers

To create your own MCP server, use the `mcp-builder` skill in this repository:

```bash
# In Claude Code, the mcp-builder skill guides you through:
# 1. Researching the API you want to integrate
# 2. Implementing MCP server in Python or TypeScript
# 3. Testing and evaluating your server
# 4. Deploying to HTTP or running locally
```

See the [mcp-builder skill](./mcp-builder/SKILL.md) for complete guidance.

---

## Example: Complete Setup Workflow

Here's a complete example of setting up multiple MCP servers:

```bash
# 1. Add GitHub integration
claude mcp add github \
  -e GITHUB_TOKEN=ghp_your_token_here \
  -- npx -y @modelcontextprotocol/server-github

# 2. Add filesystem access
claude mcp add filesystem \
  -- npx -y @modelcontextprotocol/server-filesystem /home/user/projects

# 3. Add web search
claude mcp add brave-search \
  -e BRAVE_API_KEY=your_brave_key \
  -- npx -y @modelcontextprotocol/server-brave-search

# 4. Verify all servers
claude mcp list

# 5. Restart Claude Code
exit
claude

# 6. Test in chat
"@github Show me open issues in my repository"
"@filesystem List files in the projects directory"
"Search for Claude MCP documentation using @brave-search"
```

---

## Additional Resources

- [MCP Official Documentation](https://modelcontextprotocol.io/)
- [MCP Python SDK](https://github.com/modelcontextprotocol/python-sdk)
- [MCP TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk)
- [Claude Code MCP Docs](https://docs.claude.com/en/docs/claude-code/mcp)
- [MCP Server Registry](https://github.com/modelcontextprotocol/servers)
- [MCP Builder Skill](./mcp-builder/SKILL.md) - Create custom MCP servers

---

## Summary

**Skills vs MCP Servers:**
- **Skills** = Instructions for Claude (markdown files)
- **MCP Servers** = External tools and data sources (running processes)

**Quick Commands:**
```bash
claude mcp add [name]     # Add MCP server
claude mcp list           # List servers
claude mcp remove [name]  # Remove server
/mcp                      # View servers in chat
```

**Recommended Setup:**
1. Start with pre-built MCP servers (GitHub, filesystem, etc.)
2. Use `--scope user` for personal tools
3. Test with HTTP transport for remote services
4. Use stdio transport for local tools
5. Create custom servers with mcp-builder skill when needed

Happy building! 🚀
