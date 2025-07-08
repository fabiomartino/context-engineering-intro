# Context Engineering Starter Template

A comprehensive template for getting started with Context Engineering - the discipline of engineering context for AI coding assistants so they have all the necessary information to complete tasks from start to finish.

> **Context Engineering outperforms prompt engineering by an order of magnitude – and offers far more structure and reliability than informal 'vibe coding'. This template is optimized for use with the CLAUDE Code.**

## 🚀 Quick Start

```bash
# 1. Clone this template
git clone https://github.com/coleam00/Context-Engineering-Intro.git
cd Context-Engineering-Intro

# 2. Set up your project rules (optional - template provided)
# Edit CLAUDE.md to add your project-specific guidelines

# 3. Add examples (highly recommended)
# Place relevant code examples in the `examples/` folder

# 4. Create your initial feature request
# Edit INITIAL.md with your feature requirements

# 5. Generate a comprehensive PRP (Product Requirements Prompt – a detailed implementation blueprint for AI assistants)
# In Claude Code (Anthropic's coding assistant), run:
/generate-prp INITIAL.md

# 6. Execute the PRP to implement your feature
# In Claude Code (Anthropic's coding assistant), run:
/execute-prp PRPs/your-feature-name.md
```

## 📚 Table of Contents

- [What is Context Engineering?](#what-is-context-engineering)
- [Template Structure](#template-structure)
- [Step-by-Step Guide](#step-by-step-guide)
- [Writing Effective INITIAL.md Files](#writing-effective-initialmd-files)
- [The PRP Workflow](#the-prp-workflow)
- [Using Examples Effectively](#using-examples-effectively)
- [Best Practices](#best-practices)
- [Common Pitfalls](#common-pitfalls)
- [Resources](#resources)

## What is Context Engineering?

Context Engineering represents a paradigm shift from traditional prompt engineering:

### Prompt Engineering vs. Context Engineering

**Prompt Engineering:**

- Focuses on clever wording and specific phrasing
- Limited to how you phrase a task
- Like giving someone a sticky note

**Context Engineering:**

- A complete system for providing comprehensive context
- Includes documentation, examples, rules, patterns, and validation
- Like writing a full screenplay with all the details

### Why Context Engineering Matters

1. **Reduces AI Failures**: Most agent failures aren't model failures - they're context failures
2. **Ensures Consistency**: AI follows your project patterns and conventions
3. **Enables Complex Features**: AI can handle multi-step implementations effectively when given proper context
4. **Self-Correcting**: Validation loops allow AI to fix its own mistakes

## Template Structure

```text
context-engineering-intro/
├── .claude/
│   ├── commands/
│   │   ├── generate-prp.md         # Generates comprehensive PRPs
│   │   └── execute-prp.md          # Executes PRPs to implement features
│   └── settings.local.json         # Claude Code Permissions
├── PRPs/
│   ├── templates/
│   │   └── prp_base.md             # Base template for PRPs
│   └── EXAMPLE_multi_agent_prp.md  # Example of a complete PRP
├── examples/                       # Your code examples (critical!)
├── CLAUDE.md                       # Project-wide rules for the AI assistant
├── INITIAL.md                      # Initial feature request definition
├── INITIAL_EXAMPLE.md              # Example INITIAL.md
└── README.md                       # Context Engineering starter guide (this file)
```

Additional templates and support for RAG-based architectures (Retrieval-Augmented Generation) will be included in a future update.

## Step-by-Step Guide

### 1. Set Up Global Rules (CLAUDE.md)

The `CLAUDE.md` file contains project-wide rules that the AI assistant will follow in every conversation. The template includes:

- **Project awareness**: Reading planning docs, checking tasks
- **Code structure**: File size limits, module organization
- **Testing requirements**: Unit test patterns, coverage expectations
- **Style conventions**: Language preferences, formatting rules
- **Documentation standards**: Docstring formats, commenting practices

**You can use the provided template as-is or customize it for your project.**

### 2. Create Your Initial Feature Request

Edit `INITIAL.md` to describe what you want to build:

```markdown
## FEATURE:
[Describe what you want to build - be specific about functionality and requirements]

## EXAMPLES:
[List any example files in the examples/ folder and explain how they should be used]

## DOCUMENTATION:
[Include links to relevant documentation, APIs, or internal resources such as your MCP (Model Control Protocol) server]

## OTHER CONSIDERATIONS:
[Mention any gotchas, specific requirements, or things AI assistants commonly miss]
```

**See `INITIAL_EXAMPLE.md` for a complete example.**

### 3. Generate the PRP

PRPs (Product Requirements Prompts) are comprehensive implementation blueprints that include:

- Complete context and documentation
- Implementation steps with validation
- Error handling patterns
- Test requirements

They are similar to PRDs (Product Requirements Documents), but PRPs are tailored specifically for AI coding assistants and include strict context and validation logic.

Here's a quick comparison:

**PRD (Product Requirements Document):**
- Written for human developers
- May include ambiguous goals
- Often high-level and descriptive

**PRP (Product Requirements Prompt):**
- Written to instruct an AI coding agent
- Requires specificity and validation
- Operational and execution-oriented

Run in Claude Code:

```bash
/generate-prp INITIAL.md
```

**Note:** The slash commands are custom commands defined in `.claude/commands/`. You can view their implementation:
- `.claude/commands/generate-prp.md` - See how it researches and creates PRPs
- `.claude/commands/execute-prp.md` - See how it implements features from PRPs

The `$ARGUMENTS` variable in these commands represents the input passed after the slash command name (e.g., `INITIAL.md` or `PRPs/your-feature.md`). This is a placeholder used inside `.claude/commands/*.md` files to reference user-supplied input dynamically.

This command will:
1. Read your feature request
2. Research the codebase for patterns
3. Search for relevant documentation
4. Create a comprehensive PRP in `PRPs/your-feature-name.md`

### 4. Execute the PRP

Once generated, execute the PRP to implement your feature:

```bash
/execute-prp PRPs/your-feature-name.md
```

The AI coding assistant will:

1. Read all context from the PRP
2. Create a detailed feature implementation plan with step-by-step guidance
3. Execute each step with validation
4. Run tests and fix any issues
5. Ensure all success criteria are met

## Writing Effective INITIAL.md Files

For a broader comparison between human-readable and AI-specific requirements, see the [PRD vs PRP comparison](#3-generate-the-prp) in the Generate the PRP section.

### Key Sections Explained

**FEATURE**: Be specific and comprehensive

- ❌ "Build a web scraper"
- ✅ "Build an async web scraper using BeautifulSoup that extracts product data from e-commerce sites, handles rate limiting, and stores results in PostgreSQL"

**EXAMPLES**: Leverage the examples/ folder

- Place relevant code patterns in `examples/`
- Reference specific files and patterns to follow
- Explain what aspects should be mimicked

**DOCUMENTATION**: Include all relevant resources

- API documentation URLs
- Library guides
- MCP server documentation
- Database schemas

**OTHER CONSIDERATIONS**: Capture important details

- Authentication requirements
- Rate limits or quotas
- Common pitfalls
- Performance requirements

## The PRP Workflow

### How /generate-prp Works

1. **Research Phase**

   - Analyzes your codebase for patterns
   - Searches for similar implementations
   - Identifies conventions to follow

2. **Documentation Gathering**

   - Fetches relevant API docs
   - Includes library documentation
   - Adds gotchas and quirks

3. **Blueprint Creation**

   - Creates step-by-step implementation plan
   - Includes validation gates
   - Adds test requirements

4. **Quality Check**

   - Scores confidence level (1-10)
   - Ensures all context is included

### How /execute-prp Works

1. **Load Context**: Reads the entire PRP
2. **Plan**: Creates a detailed task list using the TodoWrite system (a planning module within Claude Code)
3. **Execute**: Implements each component
4. **Validate**: Runs tests and linting
5. **Iterate**: Fixes any issues found
6. **Complete**: Ensures all requirements met

See `PRPs/EXAMPLE_multi_agent_prp.md` for a complete example of what gets generated.

## Using Examples Effectively

The `examples/` folder is **critical** for success. AI coding assistants perform much better when they can see patterns to follow.

### What to Include in Examples

1. **Code Structure Patterns**

   - How you organize modules
   - Import conventions
   - Class/function patterns

2. **Testing Patterns**

   - Test file structure
   - Mocking approaches
   - Assertion styles

3. **Integration Patterns**

   - API client implementations
   - Database connections
   - Authentication flows

4. **CLI Patterns**

   - Argument parsing
   - Output formatting
   - Error handling

### Example Structure

```text
examples/
├── README.md           # Explains what each example demonstrates
├── cli.py              # CLI implementation pattern
├── agent/              # Agent architecture patterns
│   ├── agent.py        # Agent creation pattern
│   ├── tools.py        # Tool implementation pattern
│   └── providers.py    # Multi-provider pattern
└── tests/              # Testing patterns
    ├── test_agent.py   # Unit test patterns
    └── conftest.py     # Pytest configuration
```

## Best Practices

### 1. Be Explicit in INITIAL.md

- Don't assume the AI knows your preferences
- Include specific requirements and constraints
- Reference examples liberally

### 2. Provide Comprehensive Examples

- More examples = better implementations
- Show both what to do AND what not to do
- Include error handling patterns

### 3. Use Validation Gates

- PRPs include test commands that must pass
- AI will iterate until all validations succeed
- This helps ensure the implementation works correctly on the first execution

### 4. Leverage Documentation

- Include official API docs
- Add MCP server resources
- Reference specific documentation sections

### 5. Customize CLAUDE.md

- Add your conventions
- Include project-specific rules
- Define coding standards

## Common Pitfalls

Avoid these frequent mistakes to get the most out of Context Engineering:

- **Skipping examples**: Without patterns to follow, the AI assistant will produce generic or inconsistent code.
- **Vague FEATURE descriptions**: The more specific your `INITIAL.md`, the better the results.
- **Neglecting CLAUDE.md**: Without rules and structure, implementations may drift from your project's conventions.
- **Forgetting validations**: If tests or linting steps are not included, PRPs may result in incomplete or non-functional implementations.

## Resources

- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Context Engineering Best Practices](https://www.philschmid.de/context-engineering)

---

**Start engineering your context today — and unlock the full potential of AI-powered development in your team, your product, and your workflow.**
