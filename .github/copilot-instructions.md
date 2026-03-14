# Copilot Instructions for m👀agents Repository

This repository contains a collection of custom GitHub Copilot agents and instructions. Help future Copilot sessions work effectively by understanding this project's structure and conventions.

## High-Level Architecture

**m👀agents** is a toolkit for specializing GitHub Copilot with custom agents. The project provides:

- **Agents** (`.agent.md` files): Specialized AI personas for specific workflows—API building, testing, documentation, linting, deployment, etc.
- **Documentation**: Guides for creating and using custom agents
- **Templates**: Starter templates showing agent format and best practices

### Directory Structure

```
├── agents/              # Custom agent definitions (.agent.md files)
│   ├── api-builder.agent.md   # Creates REST endpoints and GraphQL resolvers
│   ├── test-creator.agent.md  # Writes unit tests and test coverage
│   ├── docs-creator.agent.md  # Generates comprehensive documentation
│   ├── lint-formater.agent.md # Runs linting and code formatting
│   ├── dev-deployer.agent.md  # Manages development deployments
│   ├── readme-creator.agent.md # Generates and updates README files
│   └── starter-template.md # Template showing agent format
├── docs/               # Documentation and guides
│   └── README.m00agents.md # Detailed guide for using custom agents
└── README.md           # Project overview
```

### Key Concepts

**Agent Format:**
- Agents are Markdown files with frontmatter (name, description) followed by YAML-style or text instructions
- Each agent defines: a persona, project knowledge, available tools, standards/conventions, and boundaries
- The `starter-template.md` shows the canonical format

**Agent Boundaries:**
- ✅ Agents typically can: modify code in defined directories (like `src/`), write tests, run specified commands
- ⚠️ Agents should ask before: schema changes, adding dependencies, modifying CI/CD
- 🚫 Agents must never: commit secrets, modify vendor directories, remove failing tests without authorization

## File Conventions

### Agent File Format

Each `.agent.md` file should contain:

1. **Frontmatter** (optional but recommended):
   ```
   ---
   name: agent-name
   description: One-sentence description
   ---
   ```

2. **Persona Section**: Expertise area and specialization

3. **Project Knowledge**: Tech stack, file structure, key technologies

4. **Tools**: Build, test, lint commands specific to the project

5. **Standards**: Naming conventions, code style examples

6. **Boundaries**: What agents can/should/must not do

### Naming Conventions

- Agent files: `kebab-case.agent.md` (e.g., `api-builder.agent.md`, `test-creator.agent.md`)
- Agent names in frontmatter: `your-agent-name` (kebab-case)
- Keep agent descriptions concise and action-oriented

## Development Commands

This is primarily a documentation and configuration repository. Common operations:

- **View agents**: Open any `.md` file in the `agents/` directory
- **Edit agents**: Modify agent definitions directly—test by loading them in VS Code or Copilot CLI
- **Create new agents**: Use `agents/starter-template.md` as a reference template
- **Check documentation**: Review `README.md` and `docs/README.m00agents.md` for integration guidelines

## Important Conventions

### When Creating/Editing Agents

1. **Always include boundaries**: Clarify what the agent can/should do and what requires user authorization
2. **Provide concrete examples**: Use real commands and code snippets, not generic descriptions
3. **Keep personas focused**: Each agent should specialize in one domain (API building, testing, docs, etc.)
4. **Reference tools available**: List specific commands agents should use (e.g., `npm test`, `pytest -v`)
5. **Follow the starter template format**: Consistency helps users understand agent capabilities quickly

### MCP Server Integration

Agents benefit from MCP servers for enhanced capabilities. **Recommended MCP servers for m👀agents:**

| MCP Server | Purpose | Use Case |
|-----------|---------|----------|
| **filesystem** | File system access | Agents that read/write code files, templates |
| **git** | Git repository operations | Agents that need to check history, create commits |
| **bash** / **shell** | Execute shell commands | Agents that run build, test, or lint commands |
| **github** | GitHub API access | Agents that interact with issues, PRs, workflows |
| **stdio** (language servers) | Language-specific analysis | TypeScript, Python, Go agents with deeper code understanding |

**When Creating/Using Agents:**
- Document required MCP servers in the agent definition (e.g., "Requires: git, bash, filesystem")
- Test agents with MCP servers configured to ensure they work correctly
- Link to MCP server documentation from: `https://github.com/modelcontextprotocol/servers`
- Document setup instructions if an agent requires specialized MCP configuration

### Documentation Standards

- Use Markdown with clear headers and bullet points
- Include concrete examples, not just explanations
- Keep language action-oriented and specific
- Reference the repository structure when explaining file locations

## Key Files to Know

- **README.md**: Project overview, why to use custom agents, licensing
- **agents/starter-template.md**: Canonical format for all new agents—always reference this
- **docs/README.m00agents.md**: Installation and activation guide for end users
- **.github/copilot-instructions.md**: This file; guidance for future Copilot sessions

## Integration Points

This repository is designed to be:

- **User-installable**: Agents can be downloaded and installed in `~/.copilot/agents`
- **Repository-scoped**: Agents can be placed in `.github/agents` for project-specific use
- **Organization-level**: Agents can be stored in organization `.github-private` repositories

When creating content, think about how agents will be discovered and used in different contexts.
