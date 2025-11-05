# Claude Skills - Agent Documentation

This document provides a comprehensive list of all Claude Skills available in this repository that can be used with Claude Code, Claude.ai, and the Claude API.

## Installation

Skills from this repository can be used across all Claude platforms. Follow the instructions below for your platform:

### Installing Skills in Claude Code

All skills have been installed to `~/.config/claude-code/skills/` for use with Claude Code.

To manually install or update skills:

```bash
# Install a specific skill
cp -r /home/user/awesome-claude-skills/skill-name ~/.config/claude-code/skills/

# Verify installation
ls -1 ~/.config/claude-code/skills/
```

### Installing Skills in Claude.ai

To use these skills in Claude.ai (web interface):

1. **Open Claude.ai** and navigate to https://claude.ai
2. **Click the skill icon (🧩)** in your chat interface
3. **Click "Upload custom skill"**
4. **Select the SKILL.md file** from any skill folder in this repository
   - Example: `/home/user/awesome-claude-skills/brand-guidelines/SKILL.md`
5. **The skill is now available** and will activate automatically when relevant

**Note:** Each skill must be uploaded individually. Once uploaded, the skill is saved to your Claude.ai account and available across all conversations.

### Using Skills via API

Use the Claude Skills API to programmatically load and manage skills:

```python
import anthropic

client = anthropic.Anthropic(api_key="your-api-key")

# Load a skill by uploading the SKILL.md content
with open("path/to/skill/SKILL.md", "r") as f:
    skill_content = f.read()

response = client.messages.create(
    model="claude-3-5-sonnet-20241022",
    skills=[{"type": "custom", "content": skill_content}],
    messages=[{"role": "user", "content": "Your prompt"}]
)
```

See the [Skills API documentation](https://docs.claude.com/en/api/skills-guide) for details.

---

## MCP Servers: Extending Claude with External Tools

In addition to **Skills** (which teach Claude how to perform tasks), you can attach **MCP Servers** to connect Claude to external APIs, databases, and services.

### Skills vs MCP Servers

- **Skills** = Instructions for Claude (markdown files with workflows and knowledge)
- **MCP Servers** = External tools and data sources (running processes that expose APIs)

### Quick MCP Setup

Add MCP servers using the Claude Code CLI:

```bash
# Add an MCP server
claude mcp add github -e GITHUB_TOKEN=your_token -- npx -y @modelcontextprotocol/server-github

# List all configured servers
claude mcp list

# View servers in chat
/mcp
```

### Popular MCP Servers

- **GitHub** - Repository, issues, and PR management
- **Filesystem** - Local file and directory access
- **Brave Search** - Web search capabilities
- **PostgreSQL** - Database queries
- **Puppeteer** - Browser automation
- **Slack** - Slack integration
- **Google Drive** - Drive file access

### Complete MCP Setup Guide

For comprehensive instructions on configuring MCP servers, see:
- **[MCP Setup Guide](./MCP-SETUP.md)** - Complete configuration and usage guide
- **[mcp-builder Skill](./mcp-builder/SKILL.md)** - Create custom MCP servers

**Key topics covered:**
- Configuration methods (CLI wizard vs manual config)
- Transport types (HTTP vs Stdio)
- Scope levels (user, project, system)
- Troubleshooting common issues
- Creating custom MCP servers

---

## Available Skills

### Business & Marketing

#### brand-guidelines
Applies Anthropic's official brand colors and typography to artifacts for consistent visual identity and professional design standards.

**Location:** `~/.config/claude-code/skills/brand-guidelines`

#### competitive-ads-extractor
Extracts and analyzes competitors' ads from ad libraries to understand messaging and creative approaches that resonate.

**Location:** `~/.config/claude-code/skills/competitive-ads-extractor`

#### domain-name-brainstormer
Generates creative domain name ideas and checks availability across multiple TLDs including .com, .io, .dev, and .ai extensions.

**Location:** `~/.config/claude-code/skills/domain-name-brainstormer`

#### internal-comms
Helps write internal communications including 3P updates, company newsletters, FAQs, status reports, and project updates using company-specific formats.

**Location:** `~/.config/claude-code/skills/internal-comms`

#### lead-research-assistant
Identifies and qualifies high-quality leads by analyzing your product, searching for target companies, and providing actionable outreach strategies.

**Location:** `~/.config/claude-code/skills/lead-research-assistant`

---

### Communication & Writing

#### content-research-writer
Assists in writing high-quality content by conducting research, adding citations, improving hooks, and providing section-by-section feedback.

**Location:** `~/.config/claude-code/skills/content-research-writer`

#### meeting-insights-analyzer
Analyzes meeting transcripts to uncover behavioral patterns including conflict avoidance, speaking ratios, filler words, and leadership style.

**Location:** `~/.config/claude-code/skills/meeting-insights-analyzer`

---

### Creative & Media

#### canvas-design
Creates beautiful visual art in PNG and PDF documents using design philosophy and aesthetic principles for posters, designs, and static pieces.

**Location:** `~/.config/claude-code/skills/canvas-design`

#### image-enhancer
Improves image and screenshot quality by enhancing resolution, sharpness, and clarity for professional presentations and documentation.

**Location:** `~/.config/claude-code/skills/image-enhancer`

#### slack-gif-creator
Creates animated GIFs optimized for Slack with validators for size constraints and composable animation primitives.

**Location:** `~/.config/claude-code/skills/slack-gif-creator`

#### theme-factory
Applies professional font and color themes to artifacts including slides, docs, reports, and HTML landing pages with 10 pre-set themes.

**Location:** `~/.config/claude-code/skills/theme-factory`

#### video-downloader
Downloads videos from YouTube and other platforms for offline viewing, editing, or archival with support for various formats and quality options.

**Location:** `~/.config/claude-code/skills/video-downloader`

---

### Development & Code Tools

#### artifacts-builder
Builds elaborate, multi-component Claude.ai HTML artifacts using modern frontend technologies including React, Tailwind CSS, and shadcn/ui.

**Location:** `~/.config/claude-code/skills/artifacts-builder`

#### changelog-generator
Automatically creates user-facing changelogs from git commits by analyzing history and transforming technical commits into customer-friendly release notes.

**Location:** `~/.config/claude-code/skills/changelog-generator`

#### mcp-builder
Guides creation of high-quality MCP (Model Context Protocol) servers for integrating external APIs and services with LLMs using Python or TypeScript.

**Location:** `~/.config/claude-code/skills/mcp-builder`

#### skill-creator
Provides guidance for creating effective Claude Skills that extend capabilities with specialized knowledge, workflows, and tool integrations.

**Location:** `~/.config/claude-code/skills/skill-creator`

#### webapp-testing
Tests local web applications using Playwright for verifying frontend functionality, debugging UI behavior, and capturing screenshots.

**Location:** `~/.config/claude-code/skills/webapp-testing`

---

### Document Processing

#### document-skills-docx
Skills for working with Microsoft Word documents including creation, editing, and formatting using DOCX format.

**Location:** `~/.config/claude-code/skills/document-skills-docx`

#### document-skills-pdf
Skills for working with PDF documents including creation, editing, forms, and advanced PDF operations.

**Location:** `~/.config/claude-code/skills/document-skills-pdf`

#### document-skills-pptx
Skills for working with PowerPoint presentations including creation, editing, and formatting using PPTX format.

**Location:** `~/.config/claude-code/skills/document-skills-pptx`

#### document-skills-xlsx
Skills for working with Excel spreadsheets including creation, editing, formulas, and data manipulation.

**Location:** `~/.config/claude-code/skills/document-skills-xlsx`

---

### Productivity & Organization

#### file-organizer
Intelligently organizes files and folders by understanding context, finding duplicates, and suggesting better organizational structures.

**Location:** `~/.config/claude-code/skills/file-organizer`

#### invoice-organizer
Automatically organizes invoices and receipts for tax preparation by reading files, extracting information, and renaming consistently.

**Location:** `~/.config/claude-code/skills/invoice-organizer`

#### raffle-winner-picker
Randomly selects winners from lists, spreadsheets, or Google Sheets for giveaways and contests with cryptographically secure randomness.

**Location:** `~/.config/claude-code/skills/raffle-winner-picker`

---

## Usage

### How Skills Work

Skills automatically activate based on context across all Claude platforms:

- **Automatic activation:** Claude detects when your task matches a skill's capabilities and activates it
- **Explicit invocation:** Mention a skill by name to ensure it's used
- **Skill chaining:** Multiple skills can work together on complex tasks
- **Platform-agnostic:** Skills work consistently across Claude.ai, Claude Code, and the API

### Usage Examples

#### Claude.ai (Web Interface)
```
"Create a PowerPoint presentation about our Q4 results"
→ Activates document-skills-pptx

"Help me brainstorm domain names for my startup"
→ Activates domain-name-brainstormer

"Analyze this meeting transcript for speaking patterns"
→ Activates meeting-insights-analyzer
```

#### Claude Code (CLI)
```bash
# Using document skills
"Create a PowerPoint presentation about our Q4 results"
# → Activates document-skills-pptx

# Using development tools
"Generate a changelog from my last 10 commits"
# → Activates changelog-generator

# Using creative skills
"Create a Slack GIF animation"
# → Activates slack-gif-creator

# Using productivity tools
"Organize all my invoice files by date and vendor"
# → Activates invoice-organizer
```

#### API Usage
```python
# Skills activate automatically in API calls too
response = client.messages.create(
    model="claude-3-5-sonnet-20241022",
    skills=[{"type": "custom", "content": skill_content}],
    messages=[{
        "role": "user",
        "content": "Create a Word document with our company guidelines"
    }]
)
# → Activates document-skills-docx
```

## Verification

To verify all skills are properly installed:

```bash
# List all installed skills
ls -1 ~/.config/claude-code/skills/

# Verify each skill has a SKILL.md file
find ~/.config/claude-code/skills/ -name "SKILL.md"
```

## Total Skills Installed

**24 skills** across 6 categories are currently installed and ready to use.

## Quick Reference: Skill File Paths

For uploading to Claude.ai, here are the direct paths to each SKILL.md file:

### Business & Marketing
- `brand-guidelines/SKILL.md`
- `competitive-ads-extractor/SKILL.md`
- `domain-name-brainstormer/SKILL.md`
- `internal-comms/SKILL.md`
- `lead-research-assistant/SKILL.md`

### Communication & Writing
- `content-research-writer/SKILL.md`
- `meeting-insights-analyzer/SKILL.md`

### Creative & Media
- `canvas-design/SKILL.md`
- `image-enhancer/SKILL.md`
- `slack-gif-creator/SKILL.md`
- `theme-factory/SKILL.md`
- `video-downloader/SKILL.md`

### Development & Code Tools
- `artifacts-builder/SKILL.md`
- `changelog-generator/SKILL.md`
- `mcp-builder/SKILL.md`
- `skill-creator/SKILL.md`
- `webapp-testing/SKILL.md`

### Document Processing
- `document-skills/docx/SKILL.md`
- `document-skills/pdf/SKILL.md`
- `document-skills/pptx/SKILL.md`
- `document-skills/xlsx/SKILL.md`

### Productivity & Organization
- `file-organizer/SKILL.md`
- `invoice-organizer/SKILL.md`
- `raffle-winner-picker/SKILL.md`

## Additional Resources

- [Claude Skills Documentation](https://docs.claude.com/en/api/skills-guide)
- [Awesome Claude Skills Repository](https://github.com/Jupdefi/awesome-claude-skills)
- [Creating Custom Skills](https://support.claude.com/en/articles/12512198-creating-custom-skills)
- [Claude.ai Skills Marketplace](https://claude.ai/marketplace)
