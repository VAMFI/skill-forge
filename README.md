# Skill Forge

**Autonomously create research-grounded, high-quality Claude Code skills.**

Unlike template-based skill creation, Skill Forge researches official documentation and domain sources before generating any content. Every fact is verified, every procedure is sourced.

## Why Skill Forge?

| Traditional Approach | Skill Forge Approach |
|----------------------|----------------------|
| Copy template patterns | Research official docs first |
| Generic skill structure | Tailored to verified patterns |
| May use outdated information | Fetches current documentation |
| Trial and error | Grounded in proven practices |
| No citations | Full source documentation |

## Features

- **Research-First Architecture** — Fetches Claude Code docs and domain docs before generation
- **Source Verification** — Every fact traced to official documentation
- **Citation Included** — `sources.md` with all URLs and retrieval dates
- **Official Format** — Follows latest Anthropic skill patterns
- **Progressive Disclosure** — Lean SKILL.md with detailed references/

## Installation

### One-Liner (Recommended)

```bash
claude --add-plugin https://github.com/VAMFI/skill-forge
```

### Alternative Methods

**Via Git Clone:**
```bash
git clone https://github.com/VAMFI/skill-forge ~/.claude/plugins/skill-forge
```

**Manual Download:**
```bash
# Download and extract to plugins directory
curl -L https://github.com/VAMFI/skill-forge/archive/main.tar.gz | tar -xz -C ~/.claude/plugins/
mv ~/.claude/plugins/skill-forge-main ~/.claude/plugins/skill-forge
```

**Per-Session Usage:**
```bash
claude --plugin-dir /path/to/skill-forge
```

## Usage

### Command

```bash
/skill-forge:forge-skill Create a skill for Kubernetes deployment best practices

/skill-forge:forge-skill Build a skill for Python pytest testing

/skill-forge:forge-skill I need a skill for PostgreSQL optimization --output ./my-plugin/skills
```

### What Happens

1. **Research Phase**: Agent fetches:
   - Claude Code skill documentation (DeepWiki, WebFetch)
   - Domain official documentation (WebSearch, WebFetch, Context7)

2. **Design Phase**: Agent plans:
   - Trigger phrases for description
   - SKILL.md structure
   - Reference files needed

3. **Create Phase**: Agent generates:
   - SKILL.md with proper frontmatter
   - references/ with detailed content
   - sources.md with citations

4. **Validate Phase**: Agent checks:
   - Structure completeness
   - Description quality
   - Source documentation

## Components

### Agent: `skill-forge`

The main autonomous agent that:
- Researches documentation
- Designs skill structure
- Creates all files
- Validates output

**Tools Used:**
- WebSearch, WebFetch (web research)
- DeepWiki (GitHub repo analysis)
- Context7 (library documentation)
- Read, Write, Bash (file operations)
- TodoWrite (progress tracking)

### Skill: `forge-methodology`

Core knowledge for skill creation:
- Official SKILL.md format
- Research methodology
- Quality checklist
- Source hierarchy

### Command: `/forge-skill`

Entry point for skill creation with argument support.

## Research Sources

The agent consults these authoritative sources:

| Source | Content |
|--------|---------|
| [anthropics/skills](https://github.com/anthropics/skills) | Official skill examples |
| [anthropics/claude-code](https://github.com/anthropics/claude-code) | Plugin documentation |
| [Anthropic News](https://www.anthropic.com/news/skills) | Skills feature overview |
| [Engineering Blog](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) | Best practices |
| [Claude Cookbooks](https://github.com/anthropics/claude-cookbooks) | API usage |

Plus domain-specific official documentation via WebSearch/WebFetch/Context7.

## Source Credibility Hierarchy

The agent prioritizes sources in this order:

1. **Official documentation** (highest trust)
2. **Official GitHub repos**
3. **Authoritative tech sources** (MDN, framework docs)
4. **Verified community** (high-vote Stack Overflow)
5. **General web** (marked as unverified)

## Output Structure

Created skills follow this structure:

```
skill-name/
├── SKILL.md                 # Core instructions (≤2,000 words)
├── references/
│   ├── detailed-guide.md    # Extended content
│   ├── patterns.md          # Common patterns
│   └── sources.md           # All citations
└── examples/                # Working code (if applicable)
    └── example.sh
```

## Example Session

```
User: /skill-forge:forge-skill Create a skill for Kubernetes deployment

Agent: I'll create a research-grounded skill for Kubernetes deployment.
       Let me research the official documentation first...

[Agent fetches Claude Code skill format from DeepWiki]
[Agent fetches Kubernetes official docs]
[Agent researches K8s deployment best practices]

Agent: Where should I create this skill?
       1. ./skills/kubernetes-deployment/
       2. Custom path

User: Option 1

[Agent creates skill with full citations]

Agent: ✓ Skill created at ./skills/kubernetes-deployment/

       Files:
       - SKILL.md (1,847 words)
       - references/deployment-patterns.md
       - references/kubectl-reference.md
       - references/sources.md (12 citations)

       Sources consulted:
       - kubernetes.io/docs (official)
       - anthropics/skills (official)
       - CNCF best practices guide
```

## Security

- Skills are grounded in official documentation
- No hardcoded credentials
- Always review generated skills before production use
- The agent follows Anthropic's security guidelines

## Requirements

- Claude Code with plugin support
- Internet access for documentation fetching
- MCP servers: DeepWiki, Context7 (optional but recommended)

## License

MIT

## Contributing

Contributions welcome! Please ensure any changes maintain the research-first philosophy.
