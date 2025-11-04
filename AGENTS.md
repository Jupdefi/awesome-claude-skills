# Claude Code Skills - Agent Documentation

This document provides a comprehensive list of all Claude Skills available in this repository that can be used with Claude Code, Claude.ai, and the Claude API.

## Installation

All skills from this repository have been installed to `~/.config/claude-code/skills/` for use with Claude Code.

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

These skills are automatically loaded when you start Claude Code. They activate contextually based on your requests:

- **Automatic activation:** Claude Code will automatically use the relevant skill when your task matches its capabilities
- **Explicit invocation:** You can mention a skill by name to ensure it's used
- **Skill chaining:** Multiple skills can work together on complex tasks

## Examples

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

## Additional Resources

- [Claude Skills Documentation](https://docs.claude.com/en/api/skills-guide)
- [Awesome Claude Skills Repository](https://github.com/Jupdefi/awesome-claude-skills)
- [Creating Custom Skills](https://support.claude.com/en/articles/12512198-creating-custom-skills)
