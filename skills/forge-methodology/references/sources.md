# Official Documentation Sources

Authoritative sources for skill creation, verified and catalogued.

**Last Updated:** 2024-12-08

## Claude Code & Skills Documentation

### Primary Sources

| Source | URL | Content |
|--------|-----|---------|
| Official Skills Repo | https://github.com/anthropics/skills | Skill examples, format specification |
| Claude Code Repo | https://github.com/anthropics/claude-code | Plugin and skill documentation |
| Skills Announcement | https://www.anthropic.com/news/skills | Feature overview, capabilities |
| Skills Engineering Blog | https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills | Progressive disclosure, best practices |
| Claude Cookbooks | https://github.com/anthropics/claude-cookbooks/blob/main/skills/README.md | API usage, custom skill creation |
| Plugins README | https://github.com/anthropics/claude-code/blob/main/plugins/README.md | Plugin architecture |

### Support Documentation

| Source | URL | Content |
|--------|-----|---------|
| What are Skills? | https://support.claude.com/en/articles/12512176-what-are-skills | User guide |
| Creating Custom Skills | https://support.claude.com/en/articles/12512198-creating-custom-skills | Creation tutorial |
| Skills API Quickstart | https://docs.claude.com/en/api/skills-guide | API integration |

## SKILL.md Format Specification

From official sources, the required format is:

### Frontmatter (Required)

```yaml
---
name: skill-name-kebab-case
description: This skill should be used when the user asks to "[phrase 1]", "[phrase 2]"...
version: 1.0.0
---
```

**Source:** https://github.com/anthropics/skills (README.md)

### Directory Structure

```
skill-name/
├── SKILL.md         # Required
├── scripts/         # Optional: Executable code
├── resources/       # Optional: Templates, data
└── references/      # Optional: Detailed docs
```

**Source:** https://github.com/anthropics/claude-cookbooks/blob/main/skills/README.md

## Key Quotes from Official Sources

### On Skill Description

> "The `name` and `description` in YAML frontmatter determine when Claude will use the skill. Be specific about what the skill does and when to use it."

**Source:** DeepWiki analysis of anthropics/claude-code

### On Progressive Disclosure

> "Skills load in stages to minimize token usage... agents with filesystem and code execution capabilities don't require entire skill contents in their context window—they navigate and discover information on demand."

**Source:** https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills

### On Security

> "While this makes them powerful, it also means that malicious skills may introduce vulnerabilities in the environment where they're used or direct Claude to exfiltrate data and take unintended actions. We recommend installing skills only from trusted sources."

**Source:** https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills

### On Skill Creation Best Practices

> "Structure for scale: When the SKILL.md file becomes unwieldy, split its content into separate files and reference them."

**Source:** https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills

### On Iteration

> "Iterate with Claude: As you work on a task with Claude, ask Claude to capture its successful approaches and common mistakes into reusable context and code within a skill."

**Source:** https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills

## Tools for Research

### DeepWiki

For comprehensive repository understanding:
```
mcp__deepwiki__ask_question
Repository: anthropics/claude-code
Question: [Your question about skills/plugins]
```

### Context7

For library documentation:
```
mcp__context7__resolve-library-id
libraryName: [library name]

mcp__context7__get-library-docs
context7CompatibleLibraryID: [resolved ID]
topic: [specific topic]
```

### WebFetch

For specific page content:
```
WebFetch
url: [documentation URL]
prompt: "Extract [specific information needed]"
```

### WebSearch

For current information:
```
WebSearch
query: "[topic] official documentation 2024 2025"
```

## Version Information

### Claude Code Skills

- Skills feature added in Claude Code version 2.0.20
- Skills are supported across Claude.ai, Claude Code, Claude Agent SDK, and Claude Developer Platform
- API beta headers required: `skills-2025-10-02`

**Source:** DeepWiki analysis, https://github.com/anthropics/claude-cookbooks

### Plugin Architecture

- Plugins in public beta as of October 2025
- Skills vs Commands: Commands require explicit `/command` trigger, Skills activate automatically

**Source:** https://www.anthropic.com/news/claude-code-plugins

## Changelog

### 2024-12-08
- Initial compilation of official sources
- Verified SKILL.md format against multiple sources
- Documented progressive disclosure pattern
- Added security considerations from official blog
