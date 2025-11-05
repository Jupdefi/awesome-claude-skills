# My Claude Code MCP Setup

This document describes your **personal MCP server configuration** for Claude Code.

## ✅ Configuration Status

**Location:** `~/.claude.json`
**Project:** `/home/user/awesome-claude-skills`
**Total Servers:** 5

---

## 🚀 Your Active MCP Servers

### 1. GitHub Server 🐙
**Package:** `@modelcontextprotocol/server-github`
**Status:** ✅ Configured with auth token
**Capabilities:**
- Repository management
- Issue tracking
- Pull request operations
- Code search
- Gist management

**Configuration:**
```json
{
  "transport": "stdio",
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-github"],
  "env": {
    "GITHUB_TOKEN": "ghp_***"
  }
}
```

### 2. Brave Search Server 🔍
**Package:** `@modelcontextprotocol/server-brave-search`
**Status:** ✅ Configured with API key
**Capabilities:**
- Web search
- Current information lookup
- News and article search
- Real-time data access

**Configuration:**
```json
{
  "transport": "stdio",
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-brave-search"],
  "env": {
    "BRAVE_API_KEY": "BSA***"
  }
}
```

### 3. Filesystem Server 📁
**Package:** `@modelcontextprotocol/server-filesystem`
**Status:** ✅ Configured
**Access Scope:** `/home/user`
**Capabilities:**
- Read files and directories
- Write files
- Search filesystem
- File metadata access

**Configuration:**
```json
{
  "transport": "stdio",
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-filesystem", "/home/user"]
}
```

### 4. HuggingFace Server 🤗
**Package:** `@llmindest/mcp-hfspace`
**Status:** ✅ Configured with auth token
**Capabilities:**
- AI image generation (Stable Diffusion, DALL-E, etc.)
- Vision/image analysis models
- Text-to-speech
- Access to HuggingFace Spaces
- Private model access

**Configuration:**
```json
{
  "transport": "stdio",
  "command": "npx",
  "args": ["-y", "@llmindset/mcp-hfspace"],
  "env": {
    "HF_TOKEN": "hf_***"
  }
}
```

### 5. PostgreSQL Server 🐘
**Package:** `@modelcontextprotocol/server-postgres`
**Status:** ⚠️ Configured with placeholder credentials
**Capabilities:**
- Database queries
- Schema exploration
- Data analysis
- Table operations

**Configuration:**
```json
{
  "transport": "stdio",
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-postgres"],
  "env": {
    "DATABASE_URL": "postgresql://user:pass@host/db"
  }
}
```

**⚠️ Action Required:** Update `DATABASE_URL` with your actual PostgreSQL connection string.

---

## 🔄 How to Activate

Your MCP servers are configured in `~/.claude.json`. To activate them:

### Step 1: Restart Claude Code
```bash
exit
claude
```

### Step 2: Verify Servers Loaded
After Claude Code restarts, type:
```
/mcp
```

You should see:
- ✅ github
- ✅ brave-search
- ✅ filesystem
- ✅ huggingface
- ⚠️ postgres (may error if DATABASE_URL is invalid)

---

## 📚 Usage Examples

### GitHub Operations
```
"Show me my GitHub repositories"
"List open issues in Jupdefi/awesome-claude-skills"
"Create a new GitHub issue titled 'Update documentation'"
"@github search for MCP server examples"
"Show me recent commits in this repository"
```

### Web Search
```
"Search for the latest AI news"
"Find tutorials about Claude Code"
"@brave-search what are MCP servers"
"Search for Python best practices"
"Find recent articles about LLMs"
```

### Filesystem Operations
```
"List all files in /home/user/awesome-claude-skills"
"Show me the contents of AGENTS.md"
"@filesystem find all Python files in /home/user"
"Read the MCP-SETUP.md file"
"Create a new file at /home/user/notes.txt"
```

### HuggingFace AI
```
"Generate an image of a futuristic city"
"Create an image of a sunset using @huggingface"
"Use Stable Diffusion to generate a logo"
"Analyze this image using HuggingFace vision models"
"Convert this text to speech"
```

### PostgreSQL (After Configuration)
```
"Show me all tables in my database"
"Query the users table"
"@postgres what's the schema of the products table?"
"Count how many orders we have"
"Analyze sales data from last month"
```

---

## 🎯 Combined Workflows

### Research → Generate → Save → Track
```
"Search for 'AI art trends' using @brave-search,
generate an image based on the findings using @huggingface,
save the results to /home/user/ai-research.md using @filesystem,
and create a GitHub issue to track this research"
```

### Code Analysis → Database → Documentation
```
"Read my Python files from /home/user/projects,
query my database for usage statistics,
generate a report,
and commit it to GitHub"
```

### Data Pipeline
```
"Query PostgreSQL for user data,
analyze the patterns,
generate visualizations with HuggingFace,
save to filesystem,
create GitHub issue with findings"
```

---

## 🔧 Configuration File Location

Your MCP servers are configured in:
```
~/.claude.json
```

To view your configuration:
```bash
cat ~/.claude.json | grep -A 50 "mcpServers"
```

To edit manually:
```bash
nano ~/.claude.json
```

---

## 📊 Server Capabilities Matrix

| Server | Auth | Read | Write | Search | AI | Database |
|--------|------|------|-------|--------|----|----|
| **github** | ✅ Token | ✅ | ✅ | ✅ | ❌ | ❌ |
| **brave-search** | ✅ API Key | ✅ | ❌ | ✅ | ❌ | ❌ |
| **filesystem** | 🔓 None | ✅ | ✅ | ✅ | ❌ | ❌ |
| **huggingface** | ✅ Token | ✅ | ✅ | ❌ | ✅ | ❌ |
| **postgres** | ⚠️ DB URL | ✅ | ✅ | ✅ | ❌ | ✅ |

---

## ⚠️ Security Notes

### API Credentials in Use
1. **GitHub Token** - Provides access to your GitHub account
2. **Brave API Key** - Web search quota
3. **HuggingFace Token** - Access to AI models and private spaces
4. **PostgreSQL URL** - Direct database access

### Security Best Practices
- ✅ Never commit `~/.claude.json` to version control
- ✅ Rotate credentials regularly
- ✅ Use read-only database credentials when possible
- ✅ Limit filesystem access to necessary directories
- ⚠️ The credentials shown in conversation history should be rotated immediately

### How to Rotate Credentials

**GitHub Token:**
1. Go to: https://github.com/settings/tokens
2. Delete old token
3. Create new token with same permissions
4. Update in `~/.claude.json`

**Brave API Key:**
1. Go to: https://brave.com/search/api/
2. Revoke old key
3. Generate new key
4. Update in `~/.claude.json`

**HuggingFace Token:**
1. Go to: https://huggingface.co/settings/tokens
2. Revoke old token
3. Create new token
4. Update in `~/.claude.json`

---

## 🛠️ Troubleshooting

### Server Not Loading

**Check configuration:**
```bash
cat ~/.claude.json | grep -A 5 "server-name"
```

**Verify Node.js packages:**
```bash
npx -y @modelcontextprotocol/server-github --version
```

**Restart Claude Code:**
```bash
exit
claude
```

### Authentication Errors

**GitHub:**
- Verify token has correct permissions: `repo`, `read:org`, `gist`
- Check token hasn't expired

**Brave Search:**
- Verify API key is valid
- Check usage quota

**HuggingFace:**
- Verify token has read access
- Check if accessing private models requires additional permissions

**PostgreSQL:**
- Test connection string separately
- Verify database is accessible
- Check firewall rules

### Server Timeout

**For stdio transport:**
- Ensure Node.js is installed: `node --version`
- Check package exists: `npm search @modelcontextprotocol/server-github`

**For database:**
- Test connection: `psql "postgresql://user:pass@host/db"`
- Check network connectivity
- Verify database is running

---

## 📖 Quick Reference Commands

### View MCP Servers
```bash
/mcp
```

### List Configuration
```bash
cat ~/.claude.json | grep -A 50 mcpServers
```

### Edit Configuration
```bash
nano ~/.claude.json
```

### Restart Claude Code
```bash
exit
claude
```

### Test Each Server
```
"@github list my repos"
"@brave-search find AI news"
"@filesystem list files in /home/user"
"@huggingface generate an image"
"@postgres show tables"
```

---

## 🚀 Next Steps

### 1. Update PostgreSQL Credentials
Edit `~/.claude.json` and replace:
```json
"DATABASE_URL": "postgresql://user:pass@host/db"
```

With your actual database connection string.

### 2. Restart Claude Code
```bash
exit
claude
```

### 3. Test All Servers
Use the examples above to test each server.

### 4. Build Complex Workflows
Combine multiple servers for powerful AI-assisted development.

---

## 📚 Additional Documentation

- [MCP-SETUP.md](./MCP-SETUP.md) - Complete MCP server setup guide
- [AGENTS.md](./AGENTS.md) - Skills and MCP servers overview
- [MCP Protocol Docs](https://modelcontextprotocol.io/)
- [Claude Code Docs](https://docs.claude.com/en/docs/claude-code/mcp)

---

## 🎉 Summary

You have **5 powerful MCP servers** configured:

1. **GitHub** - Code and project management
2. **Brave Search** - Web search and research
3. **Filesystem** - Local file operations
4. **HuggingFace** - AI image generation and models
5. **PostgreSQL** - Database queries and analysis

**Status:** ✅ Ready to use (after restart and PostgreSQL config update)

**Next:** Restart Claude Code with `exit` then `claude`

Happy building! 🚀
