# m👀agents

[![Powered by m👀agents](https://img.shields.io/badge/Powered_by-Awesome_Copilot-blue?logo=githubcopilot)](https://github.com/m00sp/m00agents)

✅
This repository contains a collection of custom agents and instructions to supercharge your GitHub Copilot experience across different domains, languages, and use cases.

## 🚀 What is Custom m👀Agents Copilot?

This repository provides a comprehensive toolkit for enhancing GitHub Copilot with specialized:

- **👉 [Awesome Agents](docs/README.m00agents.md)** - Specialized GitHub Copilot agents that integrate with MCP servers to provide enhanced capabilities for specific workflows and tools


### 🤖 Custom m👀Agents

Custom agents can be used in Copilot coding agent (CCA), VS Code, and Copilot CLI (coming soon). For CCA, when assigning an issue to Copilot, select the custom agent from the provided list. In VS Code, you can activate the custom agent in the agents session, alongside built-in agents like Plan and Agent.

You can define custom agents at the user, repository, or organization/enterprise level:

| Type | Locations | Scope |
| ---- | --------- | ----- |
| User-level custom agent | local <mark>~/.copilot/agents</mark> directory | All projects |i
| Repository-level custom agent | <mark>.github/agents</mark> directory in your local and remote reporitories | Current project |
  Organization and Enterprise-level custom agent | <mark>/agents</mark> directory in the <mark>.github-private repository in an organization or enterprise | All projects under your organization and enterprise account

 In the case of naming conflicts, a system-level agent overrides a repository-level agent, and the repository-level agent would override an organization-level agent.

Custom agents can be used in three ways:

- Using the slash command in the CLI's interactive interface to select from the list of available custom agents:

```
/agent
```

- Calling out to the custom agent directly in a prompt:

```
Use the refactoring agent to refactor this code block
```

Copilot will automatically infer the agent you want to use.

- Specifying the custom agent you want to use with the command-line option. For example:

```
copilot --agent=refactor-agent --prompt "Refactor this code blockk"
```

## 🎯 Why Use Awesome GitHub Copilot?

- **Productivity**: Pre-built agents and instructions save time and provide consistent results.
- **Best Practices**: Benefit from community-curated coding standards and patterns.
- **Specialized Assistance**: Access expert-level guidance through specialized custom agents.
- **Continuous Learning**: Stay updated with the latest patterns and practices across technologies.

## 📖 Repository Structure

```plaintext
├── instructions/     # Coding standards and best practices (.instructions.md)
├── agents/           # AI personas and specialized modes (.agent.md)
├── hooks/            # Automated hooks for Copilot coding agent sessions
├── workflows/        # Agentic Workflows for GitHub Actions automation
├── plugins/          # Installable plugins bundling related items
├── scripts/          # Utility scripts for maintenance
└── skills/           # AI capabilities for specialized tasks
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🛡️ Security & Support

- **Security Issues**: Please see our [Security Policy](SECURITY.md)
- **Support**: Check our [Support Guide](SUPPORT.md) for getting help
- **Code of Conduct**: We follow the [Contributor Covenant](CODE_OF_CONDUCT.md)

## ℹ️ Disclaimer

The customizations in this repository are sourced from and created by third-party developers. GitHub does not verify, endorse, or guarantee the functionality or security of these agents. Please carefully inspect any agent and its documentation before installing to understand permissions it may require and actions it may perform.

## 📚 Sources:

- [About Custom Agents](https://docs.github.com/en/enterprise-cloud@latest/copilot/concepts/agents/coding-agent/about-custom-agents) - Official GitHub Docs
- [How to write a great agents.md: Lessons from over 2,500 repositories](https://github.blog/ai-and-ml/github-copilot/how-to-write-a-great-agents-md-lessons-from-over-2500-repositories/) - GitHub Blog
- [Awesome GitHub Copilot Repo](https://github.com/github/awesome-copilot - Awesome GitHub Copilot Repo
- [Awesome GitHub Copilot Website](https://awesome-copilot.github.com/) - Awesome GitHub Copilot Website
- https://agents.md/

## 📚 Additional Resources

- [VS Code Copilot Customization Documentation](https://code.visualstudio.com/docs/copilot/copilot-customization) - Official Microsoft documentation
- [GitHub Copilot Chat Documentation](https://code.visualstudio.com/docs/copilot/chat/copilot-chat) - Complete chat feature guide
- [VS Code Settings](https://code.visualstudio.com/docs/getstarted/settings) - General VS Code configuration guide
