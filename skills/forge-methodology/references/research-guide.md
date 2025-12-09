# Research Methodology Guide

Comprehensive guide for conducting research before skill generation.

## Research Philosophy

**The Fundamental Law:**
> NEVER trust LLM tokens for facts that can be verified. ALWAYS use tools as senses.

- Training data = potentially stale beliefs
- Tool outputs = ground truth from reality
- When in doubt, sense the world before acting

## Tool Selection Matrix

| Research Need | Primary Tool | Fallback |
|---------------|--------------|----------|
| Claude Code patterns | DeepWiki (`anthropics/claude-code`) | WebFetch GitHub |
| Library APIs | Context7 | WebFetch official docs |
| Current information | WebSearch | WebFetch news sites |
| GitHub repo understanding | DeepWiki | WebFetch raw files |
| Specific page content | WebFetch | WebSearch for alternatives |

## Research Workflow

### Step 1: Identify Information Needs

Before researching, categorize what you need:

1. **Structural information**: How should the skill be formatted?
   - Source: Claude Code documentation

2. **Domain knowledge**: What does the skill need to teach?
   - Source: Official domain documentation

3. **Best practices**: What patterns work well?
   - Source: Official examples, expert sources

4. **Current state**: Is this information recent?
   - Source: WebSearch with date filters

### Step 2: Claude Code Documentation Research

**Always start here for any skill creation.**

```
DeepWiki Query:
Repository: anthropics/claude-code
Question: "What is the current SKILL.md format? What frontmatter fields are required? What are best practices for skill descriptions?"
```

**Key pages to fetch:**
- `https://github.com/anthropics/skills/blob/main/README.md`
- `https://github.com/anthropics/claude-code/blob/main/plugins/README.md`
- `https://www.anthropic.com/news/skills`

### Step 3: Domain Research Protocol

For any domain (e.g., Kubernetes, Python testing, databases):

**Phase A: Identify Official Sources**
```
WebSearch: "[domain] official documentation"
WebSearch: "[domain] getting started guide site:[official-domain]"
```

**Phase B: Fetch and Extract**
```
WebFetch: [Official documentation URL]
Prompt: "Extract the key concepts, procedures, and best practices. Include version information."
```

**Phase C: Find Best Practices**
```
WebSearch: "[domain] best practices 2024 2025"
WebSearch: "[domain] common mistakes to avoid"
```

**Phase D: Library Documentation (if applicable)**
```
Context7: resolve-library-id for "[library-name]"
Context7: get-library-docs with topic="[specific-topic]"
```

### Step 4: Cross-Reference and Validate

After gathering information:

1. **Compare sources**: Do they agree?
2. **Check dates**: Is information current?
3. **Identify conflicts**: Note disagreements
4. **Resolve conflicts**: Prefer official sources

## Source Evaluation Criteria

### Tier 1: Official Sources (Highest Trust)

**Characteristics:**
- Published by the project/company itself
- URLs include official domains
- Version-specific documentation
- Maintained and updated

**Examples:**
- docs.anthropic.com
- kubernetes.io/docs
- docs.python.org
- Official GitHub repos

**Trust level:** Accept as authoritative

### Tier 2: Established Technical Sources

**Characteristics:**
- Well-known technical references
- Peer-reviewed or curated
- Regular updates
- Clear authorship

**Examples:**
- MDN Web Docs
- RFC documents
- OWASP guides
- AWS/GCP/Azure docs

**Trust level:** Accept with source citation

### Tier 3: Community Sources

**Characteristics:**
- User-contributed content
- Variable quality
- May be outdated
- Requires verification

**Examples:**
- Stack Overflow (high-vote answers)
- Dev.to articles
- Medium technical posts
- GitHub discussions

**Trust level:** Use with caution, verify against Tier 1/2

### Tier 4: General Web

**Characteristics:**
- Unknown authorship
- Potentially outdated
- May contain errors
- SEO-optimized content

**Trust level:** Avoid if possible, mark as "unverified" if used

## Research Documentation

### Citation Format

For each fact in the skill, document:

```markdown
## Sources

### Claude Code Skill Format
- Source: https://github.com/anthropics/skills
- Retrieved: 2024-12-08
- Key finding: SKILL.md requires name and description frontmatter

### [Domain] Best Practices
- Source: [URL]
- Retrieved: [Date]
- Key finding: [What was learned]
```

### Handling Uncertainty

When information cannot be verified:

```markdown
**Note:** The following guidance is based on common practice
rather than official documentation. Verify with your specific
environment before implementation.
```

Or:

```markdown
<!-- UNVERIFIED: Could not find official documentation for this.
     Based on: [source] -->
```

## Common Research Scenarios

### Scenario 1: Creating a Skill for a Popular Framework

```
1. DeepWiki: anthropics/claude-code → skill format
2. Context7: resolve-library-id → framework library
3. Context7: get-library-docs → API reference
4. WebFetch: Framework official docs → best practices
5. WebSearch: "[framework] common patterns 2024"
```

### Scenario 2: Creating a Skill for Internal Tooling

```
1. DeepWiki: anthropics/claude-code → skill format
2. Read: Internal documentation files
3. Grep: Existing code for patterns
4. Ask user: Clarify undocumented behaviors
```

### Scenario 3: Creating a Skill for Emerging Technology

```
1. DeepWiki: anthropics/claude-code → skill format
2. WebSearch: "[technology] documentation"
3. WebSearch: "[technology] getting started 2024"
4. WebFetch: Multiple sources for verification
5. Note: Mark information as "emerging, may change"
```

## Research Pitfalls to Avoid

### Pitfall 1: Assuming Training Data is Current
```
# BAD
"I know that React 18 uses..."

# GOOD
Let me verify the current React patterns...
[Uses Context7 to fetch React documentation]
```

### Pitfall 2: Single Source Reliance
```
# BAD
Found one blog post about X, using it.

# GOOD
Found blog post about X.
Verifying against official documentation...
Cross-referencing with Stack Overflow discussions...
```

### Pitfall 3: Ignoring Version Information
```
# BAD
"Kubernetes uses the following approach..."

# GOOD
"Kubernetes 1.28+ uses the following approach..."
(Source: kubernetes.io, retrieved 2024-12-08)
```

### Pitfall 4: Missing Recent Changes
```
# BAD
Using patterns from 2022 documentation

# GOOD
WebSearch: "[technology] changelog 2024"
WebSearch: "[technology] breaking changes recent"
```

## Research Checklist

Before concluding research:

- [ ] Claude Code skill format verified from official docs
- [ ] Domain official documentation fetched
- [ ] Multiple sources consulted
- [ ] Version information recorded
- [ ] Dates of retrieval documented
- [ ] Conflicts identified and resolved
- [ ] Uncertain information marked
- [ ] Sources documented for citation
