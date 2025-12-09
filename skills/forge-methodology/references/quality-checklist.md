# Skill Quality Checklist

Comprehensive validation criteria for ensuring skill quality before delivery.

## Pre-Creation Checklist

Before writing any skill content:

- [ ] User requirements clearly understood
- [ ] Domain identified and disambiguated
- [ ] Official documentation sources identified
- [ ] Research plan created

## Structure Validation

### SKILL.md File

- [ ] File exists at `skill-name/SKILL.md`
- [ ] Valid YAML frontmatter (starts and ends with `---`)
- [ ] `name` field present (kebab-case, no spaces)
- [ ] `description` field present
- [ ] `version` field present (semantic versioning)
- [ ] Markdown body is present and substantial

### Directory Structure

- [ ] Skill directory uses kebab-case naming
- [ ] Only necessary subdirectories created
- [ ] All referenced files exist
- [ ] No orphaned files without references

```
skill-name/           ✓ kebab-case
├── SKILL.md         ✓ required
├── references/      ✓ if detailed content needed
├── examples/        ✓ if code examples needed
└── scripts/         ✓ if utility scripts needed
```

## Description Quality

### Trigger Phrase Requirements

- [ ] Uses third-person voice
- [ ] Starts with "This skill should be used when..."
- [ ] Includes 3-5 specific trigger phrases in quotes
- [ ] Phrases match actual user queries
- [ ] Not vague or generic

**Scoring:**
| Score | Criteria |
|-------|----------|
| Excellent | 5+ specific phrases, clear scenarios |
| Good | 3-4 specific phrases |
| Acceptable | 2 phrases with clear context |
| Poor | 1 phrase or vague description |
| Fail | Missing phrases or generic |

### Example Evaluation

```yaml
# EXCELLENT
description: This skill should be used when the user asks to "deploy to Kubernetes", "create K8s deployment", "write Kubernetes manifests", "configure kubectl", "set up K8s cluster", or mentions Kubernetes deployment workflows.

# GOOD
description: This skill should be used when the user asks to "deploy to Kubernetes", "create K8s manifests", or works with Kubernetes deployments.

# POOR
description: This skill helps with Kubernetes.

# FAIL
description: Kubernetes deployment skill.
```

## Content Quality

### Writing Style

- [ ] Uses imperative/infinitive form throughout
- [ ] No second-person voice ("you should...")
- [ ] Active voice preferred
- [ ] Clear, concise instructions
- [ ] Consistent terminology

**Check for these patterns:**

| Pattern | Correct | Incorrect |
|---------|---------|-----------|
| Instructions | "Create the file" | "You should create the file" |
| Process | "Validate input first" | "You need to validate input" |
| Guidance | "Use the API endpoint" | "You can use the API endpoint" |

### Size and Organization

- [ ] SKILL.md body ≤ 2,000 words
- [ ] If > 2,000 words, content moved to references/
- [ ] Clear section headings
- [ ] Logical flow from overview to details
- [ ] No duplicate information across files

**Word count targets:**
| Content | Target | Maximum |
|---------|--------|---------|
| SKILL.md body | 1,500-2,000 | 3,000 |
| Individual reference file | 2,000-4,000 | 6,000 |
| Total skill content | Unlimited | - |

### Completeness

- [ ] Overview section explains purpose
- [ ] Prerequisites listed (if any)
- [ ] Step-by-step procedures included
- [ ] Examples provided
- [ ] Edge cases addressed
- [ ] Error handling guidance (if applicable)

## Accuracy Validation

### Source Verification

- [ ] All facts traced to official sources
- [ ] Source URLs documented in references/sources.md
- [ ] Retrieval dates recorded
- [ ] Version information included where relevant

### Uncertain Content Handling

- [ ] Unverified information clearly marked
- [ ] Inferred guidance labeled as such
- [ ] Assumptions documented
- [ ] Alternatives noted where applicable

**Marking uncertain content:**
```markdown
**Note:** The following is based on community best practices
and should be verified for your specific environment.
```

### Currency Check

- [ ] Information is current (within 12 months)
- [ ] Deprecated features not recommended
- [ ] Breaking changes noted
- [ ] Version compatibility stated

## Progressive Disclosure Validation

### Level 1: Metadata
- [ ] name is descriptive and unique
- [ ] description is comprehensive (~50-100 words)
- [ ] Metadata alone sufficient to decide relevance

### Level 2: SKILL.md Body
- [ ] Core concepts present
- [ ] Essential procedures included
- [ ] References to detailed content
- [ ] Usable without loading Level 3

### Level 3: References/Examples
- [ ] Detailed content in references/
- [ ] Working examples in examples/
- [ ] Utility scripts in scripts/
- [ ] Each file focused on specific topic

## Security Review

- [ ] No hardcoded credentials
- [ ] No sensitive data in examples
- [ ] External connections documented
- [ ] Security considerations section included
- [ ] Input validation guidance (if applicable)

## Final Validation

### Self-Test Questions

1. Would this trigger correctly?
   - Read the description aloud
   - Does it match what users would say?

2. Can Claude execute this?
   - Are instructions clear and actionable?
   - Are prerequisites available?

3. Is it accurate?
   - Can every fact be traced to a source?
   - Are uncertain items marked?

4. Is it complete?
   - Does it cover the main use cases?
   - Are edge cases addressed?

5. Is it lean?
   - Is SKILL.md under 2,000 words?
   - Is detailed content in references?

### Sign-Off Checklist

Before delivering the skill:

- [ ] All structure validations pass
- [ ] Description quality is "Good" or better
- [ ] Content uses correct writing style
- [ ] All facts have sources
- [ ] Progressive disclosure implemented
- [ ] Security review completed
- [ ] Self-test questions answered positively

## Common Issues and Fixes

| Issue | Detection | Fix |
|-------|-----------|-----|
| Weak triggers | Description < 50 words | Add specific trigger phrases |
| Second person | Contains "you should" | Rewrite in imperative form |
| Too long | SKILL.md > 2,000 words | Move content to references/ |
| No sources | references/sources.md missing | Add citation file |
| Orphan files | Files not referenced in SKILL.md | Add references or remove files |
| Generic content | No domain-specific details | Research and add specifics |
