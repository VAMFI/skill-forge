---
name: forge-skill
description: Create a research-grounded, high-quality Claude Code skill with automatic documentation verification
argument-hint: <skill-description> [--output <directory>]
allowed-tools:
  - Task
  - AskUserQuestion
  - Read
---

# Forge Skill Command

Create a high-quality Claude Code skill with research-grounded content.

## What This Command Does

This command triggers the `skill-forge` agent to autonomously:

1. **Research Claude Code documentation** — Verify current SKILL.md format
2. **Research domain documentation** — Fetch official docs for the skill's domain
3. **Design the skill structure** — Plan SKILL.md and supporting files
4. **Create all skill files** — With proper format and citations
5. **Validate the skill** — Check against quality criteria

## Usage

```
/skill-forge:forge-skill <description of the skill you want>
```

### Examples

```
/skill-forge:forge-skill Create a skill for Kubernetes deployment best practices

/skill-forge:forge-skill Build a skill for Python pytest testing patterns

/skill-forge:forge-skill I need a skill that helps with PostgreSQL database optimization

/skill-forge:forge-skill Create a skill for React component development --output ./my-plugin/skills
```

## Arguments

**skill-description** (required)
Describe what the skill should do. Be specific about:
- The domain (e.g., Kubernetes, Python, React)
- The specific use cases (e.g., deployment, testing, optimization)
- Any version requirements (e.g., Python 3.11+, K8s 1.28+)

**--output** (optional)
Directory where the skill should be created. If not specified, the agent will ask.

## Process

When invoked, this command:

1. Launches the `skill-forge` agent with your description
2. The agent researches official documentation
3. The agent asks clarifying questions if needed
4. The agent creates the skill with proper citations
5. The agent validates and reports results

## What Makes This Different

Unlike template-based skill creation, this command:

- **Researches first** — Fetches current official documentation
- **Verifies facts** — Never generates from training data alone
- **Cites sources** — Includes references/sources.md with URLs
- **Follows patterns** — Uses official Anthropic skill format

## Output

The agent creates a skill directory with:

```
skill-name/
├── SKILL.md              # Core instructions (lean)
├── references/
│   ├── detailed-guide.md # Detailed content
│   └── sources.md        # Citation URLs
└── examples/             # Working code (if applicable)
```

## Instructions for Claude

When this command is invoked:

1. Load the forge-methodology skill for reference patterns
2. Launch the skill-forge agent using the Task tool:
   ```
   Task tool
   subagent_type: skill-forge:skill-forge
   prompt: "Create a skill for: [user's description]. Follow the complete research workflow. Ask about output location."
   ```
3. Wait for the agent to complete
4. Report the results to the user

If the user provides `--output`, include it in the prompt:
```
prompt: "Create a skill for: [description]. Output to: [directory]. Follow the complete research workflow."
```

## Tips

- **Be specific** — "Python testing" is vague; "pytest unit testing patterns" is better
- **Mention versions** — If you need specific version support, say so
- **Describe use cases** — What should the skill help users do?

## Security Note

The created skills will be grounded in official documentation. However, always review generated skills before use in production environments.
