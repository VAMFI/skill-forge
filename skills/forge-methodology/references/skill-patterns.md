# Skill Patterns Reference

Comprehensive patterns derived from official Anthropic skills and documentation.

## Pattern 1: Document Generation Skills

Used by official skills like `xlsx`, `pptx`, `pdf`, `docx`.

**Structure:**
```
document-skill/
├── SKILL.md           # Generation instructions
├── scripts/
│   └── generator.py   # Core generation logic
└── resources/
    └── template.ext   # Base template
```

**SKILL.md Pattern:**
```markdown
---
name: document-type
description: This skill should be used when the user asks to "create [document]", "generate [document]", "make [document] file", or needs to produce [document type] output.
---

# [Document Type] Generation

## Capabilities
- [Capability 1]
- [Capability 2]

## Process
1. [Step 1]
2. [Step 2]

## Output Format
[Describe expected output]

## Examples
[Concrete examples]
```

## Pattern 2: Domain Expertise Skills

Provide specialized knowledge for a domain.

**Structure:**
```
domain-skill/
├── SKILL.md           # Core procedures
└── references/
    ├── concepts.md    # Domain concepts
    ├── patterns.md    # Common patterns
    └── pitfalls.md    # What to avoid
```

**SKILL.md Pattern:**
```markdown
---
name: domain-expertise
description: This skill should be used when the user asks to "[domain action 1]", "[domain action 2]", or works with [domain] systems.
---

# [Domain] Expertise

## When to Use
[Specific scenarios]

## Core Concepts
[Brief overview — details in references/concepts.md]

## Standard Procedures
1. [Procedure 1]
2. [Procedure 2]

## Additional Resources
- `references/concepts.md` — Detailed concept explanations
- `references/patterns.md` — Common implementation patterns
```

## Pattern 3: Workflow Automation Skills

Automate multi-step workflows.

**Structure:**
```
workflow-skill/
├── SKILL.md           # Workflow steps
├── scripts/
│   ├── step1.sh
│   └── step2.py
└── examples/
    └── complete-workflow.md
```

**SKILL.md Pattern:**
```markdown
---
name: workflow-automation
description: This skill should be used when the user asks to "[automate X]", "[execute workflow Y]", or needs to perform [multi-step process].
---

# [Workflow] Automation

## Overview
[Brief description of the workflow]

## Prerequisites
- [Requirement 1]
- [Requirement 2]

## Workflow Steps

### Step 1: [Name]
[Instructions]
Script: `scripts/step1.sh`

### Step 2: [Name]
[Instructions]
Script: `scripts/step2.py`

## Verification
[How to verify success]
```

## Pattern 4: Integration Skills

Connect to external systems or APIs.

**Structure:**
```
integration-skill/
├── SKILL.md           # Integration instructions
├── references/
│   └── api-reference.md
└── scripts/
    └── connector.py
```

**Key Elements:**
- Clear authentication requirements
- Error handling guidance
- Rate limiting considerations
- Security best practices

## Pattern 5: Analysis Skills

Analyze data or code.

**SKILL.md Pattern:**
```markdown
---
name: analysis-type
description: This skill should be used when the user asks to "analyze [subject]", "review [subject]", "audit [subject]", or needs insights about [domain].
---

# [Subject] Analysis

## Analysis Framework
1. [Analysis step 1]
2. [Analysis step 2]

## Metrics to Evaluate
- [Metric 1]: [What it indicates]
- [Metric 2]: [What it indicates]

## Output Format
[How to present findings]

## Red Flags
[What to watch for]
```

## Anti-Patterns to Avoid

### Anti-Pattern 1: Vague Descriptions
```yaml
# BAD
description: Helps with coding tasks.

# GOOD
description: This skill should be used when the user asks to "refactor Python code", "improve code quality", "apply PEP 8 formatting", or mentions Python code style improvements.
```

### Anti-Pattern 2: Second-Person Instructions
```markdown
# BAD
You should create the file first.
You need to validate the input.

# GOOD
Create the file first.
Validate the input before processing.
```

### Anti-Pattern 3: Monolithic SKILL.md
```
# BAD - Everything in one file
skill/
└── SKILL.md  (8,000 words)

# GOOD - Progressive disclosure
skill/
├── SKILL.md  (1,800 words)
└── references/
    ├── detailed-guide.md
    └── advanced-topics.md
```

### Anti-Pattern 4: Missing Source Citations
```markdown
# BAD
Kubernetes pods should have resource limits.

# GOOD
Kubernetes pods should have resource limits.
(Source: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/)
```

## Real-World Examples

### From anthropics/skills Repository

**xlsx skill** (Excel generation):
- Focuses on formulas, charts, formatting
- Includes Python scripts for generation
- Progressive disclosure: core in SKILL.md, details in scripts

**pdf skill** (PDF creation):
- Text, tables, images support
- Template-based approach
- Clear output specifications

### From plugin-dev Plugin

**hook-development skill**:
- Strong trigger phrases
- Lean body (1,651 words)
- 3 reference files for detailed content
- Working examples included

**agent-development skill**:
- Specific triggers
- Focused body (1,438 words)
- Complete agent examples
