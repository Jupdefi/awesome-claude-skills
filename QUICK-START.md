# Quick Start Guide

## 🚀 Your Development Environment is Ready!

You have **24 Claude Skills** and **5 MCP Servers** configured for Claude Code.

---

## ⚡ Activate Everything

### Step 1: Restart Claude Code
```bash
exit
claude
```

### Step 2: Verify Skills Loaded
All 24 skills in `~/.config/claude-code/skills/` load automatically.

### Step 3: Check MCP Servers
```
/mcp
```

You should see:
- ✅ github
- ✅ brave-search
- ✅ filesystem
- ✅ huggingface
- ⚠️ postgres (needs database URL)

---

## 📚 What You Have

### Skills (24 Total)
**Location:** `~/.config/claude-code/skills/`

**Categories:**
- Business & Marketing (5 skills)
- Communication & Writing (2 skills)
- Creative & Media (5 skills)
- Development & Code Tools (5 skills)
- Document Processing (4 skills)
- Productivity & Organization (3 skills)

**Full List:** See [AGENTS.md](./AGENTS.md)

### MCP Servers (5 Total)
**Location:** `~/.claude.json`

1. **GitHub** - Code management
2. **Brave Search** - Web search
3. **Filesystem** - File operations
4. **HuggingFace** - AI image generation
5. **PostgreSQL** - Database queries

**Full Setup:** See [MY-MCP-SETUP.md](./MY-MCP-SETUP.md)

---

## 🎯 Quick Examples

### Using Skills
Skills activate automatically based on your request:

```
"Generate a changelog from my git commits"
→ Uses changelog-generator skill

"Create a PowerPoint presentation"
→ Uses document-skills-pptx skill

"Organize my invoice files"
→ Uses invoice-organizer skill
```

### Using MCP Servers
Use @ mentions or natural language:

```
"@github show my repositories"
"@brave-search find AI tutorials"
"@filesystem list files in /home/user"
"@huggingface generate an image of a cat"
```

### Combined Power
```
"Search for 'AI art styles' on the web,
generate an AI image based on the results,
save it to my filesystem,
and create a GitHub issue to showcase it"

→ Uses: brave-search + huggingface + filesystem + github
```

---

## 📖 Documentation Guide

| Document | Purpose |
|----------|---------|
| [AGENTS.md](./AGENTS.md) | Complete skills list & MCP overview |
| [MY-MCP-SETUP.md](./MY-MCP-SETUP.md) | Your personal MCP configuration |
| [MCP-SETUP.md](./MCP-SETUP.md) | Complete MCP setup guide |
| [README.md](./README.md) | Repository overview |
| **QUICK-START.md** (this file) | Fast reference |

---

## ⚠️ Important: Update PostgreSQL

Your PostgreSQL MCP server needs a real database connection:

**Edit:** `~/.claude.json`

**Replace:**
```json
"DATABASE_URL": "postgresql://user:pass@host/db"
```

**With your actual database URL:**
```json
"DATABASE_URL": "postgresql://username:password@hostname:5432/database"
```

**Then restart Claude Code.**

---

## 🔐 Security Reminder

You've configured these credentials:
- GitHub Token
- Brave API Key
- HuggingFace Token

**⚠️ These were shared in the conversation and should be rotated!**

See [MY-MCP-SETUP.md](./MY-MCP-SETUP.md#security-notes) for rotation instructions.

---

## 🎮 Test Everything

After restarting Claude Code, try these:

### Test Skills
```
"Help me create a skill for managing Docker containers"
→ Uses skill-creator

"Generate a changelog from my last 10 commits"
→ Uses changelog-generator
```

### Test MCP Servers
```
"List my GitHub repositories"
→ Tests github server

"Search for Claude Code tutorials"
→ Tests brave-search server

"List files in /home/user/awesome-claude-skills"
→ Tests filesystem server

"Generate an image of a futuristic robot"
→ Tests huggingface server
```

### Test Combined
```
"Search for trending open source projects,
find their GitHub repos,
save a summary to /home/user/projects.md,
and generate an image to represent each project"
```

---

## 💡 Pro Tips

### @ Mentions
Use @ to explicitly call MCP servers:
- `@github` - GitHub operations
- `@brave-search` - Web searches
- `@filesystem` - File operations
- `@huggingface` - AI operations
- `@postgres` - Database queries

### Slash Commands
- `/mcp` - View loaded MCP servers
- `/help` - Claude Code help

### Natural Language
You don't always need @mentions:
- "Search GitHub for..." → auto-uses github
- "Generate an image..." → auto-uses huggingface
- "Find files in..." → auto-uses filesystem

---

## 🚀 You're Ready!

**Step 1:** Restart Claude Code
```bash
exit
claude
```

**Step 2:** Try an example
```
"Generate an image of a mountain landscape using AI"
```

**Step 3:** Build amazing things! 🎉

---

## 🆘 Need Help?

- **Skills not working?** Check `~/.config/claude-code/skills/`
- **MCP servers not loading?** Check `~/.claude.json` and run `/mcp`
- **Authentication errors?** Verify tokens in config file
- **Full troubleshooting:** See [MY-MCP-SETUP.md](./MY-MCP-SETUP.md#troubleshooting)

Happy coding! 🚀
