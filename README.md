# m👀agents

<div align="center">

[![Made with ❤️ by Copilot](https://img.shields.io/badge/Made%20with%20%E2%9D%A4%EF%B8%8F%20by-Copilot-ff69b4?style=flat-square)](https://github.com/github/copilot-docs)
![Beginner Friendly](https://img.shields.io/badge/Beginner-Friendly-brightgreen?style=flat-square)

**A collection of beginner-friendly custom GitHub Copilot agents to get you started with AI-assisted development.**

</div>

## 🎯 What is m👀agents?

m👀agents is a starter toolkit of custom agents designed for developers new to GitHub Copilot. It provides ready-to-use agents that enhance Copilot's capabilities for common tasks like creating documentation and code templates.

Whether you're exploring custom agents for the first time or building on existing skills, this collection demonstrates how to create and use specialized AI personas in your workflow.

## 🚀 Quick Start

### Get the Agents

**Option 1: Clone for local experimentation**
```bash
git clone https://github.com/m00sp/m00agents.git
cd m00agents
```

**Option 2: Fork to your GitHub account**
```bash
# Visit: https://github.com/m00sp/m00agents/fork
# Then clone your fork
git clone https://github.com/YOUR-USERNAME/m00agents.git
cd m00agents
```

### Install Agents Locally

Copy agents to your local Copilot configuration:

```bash
# Copy to user-level agents (available in all projects)
cp agents/*.agent.md ~/.copilot/agents/
```

Or for repository-specific use:
```bash
# Copy to repository-level agents (available only in this project)
mkdir -p .github/agents
cp agents/*.agent.md .github/agents/
```

### Use an Agent in Copilot CLI

```bash
# List available agents
copilot /agent

# Or specify an agent directly
copilot --agent=docs-creator --prompt "Create documentation for..."
copilot --agent=readme-creator --prompt "Generate a README..."
```

## 📦 Available Agents

This repository includes the following agents:

| Agent | Purpose |
|-------|---------|
| **readme-creator** | Creates comprehensive and well-structured README files |
| **docs-creator** | Generates clear, user-friendly documentation |

Each agent is tailored to help you quickly produce professional results with minimal setup.

## 📚 Learn More

- **[Quick Start Tutorial](docs/quick-start-tutorial.md)** - Step-by-step guide to understanding and using Copilot agents
- **[Detailed Agent Guide](docs/README.m00agents.md)** - In-depth documentation about custom agents and how to create your own
- **[Agent Template](agents/starter-template.agent.md)** - Reference template for building your own custom agents

## 🎓 About Custom Agents

Custom agents are specialized AI personas you can create to enhance Copilot for specific workflows. You can:

- Define them at the **user level** (all your projects)
- Define them at the **repository level** (one specific project)
- Define them at the **organization level** (for teams)

Learn more in the [official GitHub Copilot documentation](https://docs.github.com/en/copilot/customizing-copilot).

## 📖 Repository Structure

```plaintext
m00agents/
├── agents/              # Custom Copilot agents (.agent.md files)
├── docs/                # Guides and tutorials
├── assets/              # Icons and visual assets
├── instuctions/         # Project guidelines
└── README.md            # This file
```

## 🔗 Credits & Inspiration

This project was inspired by:

- 📖 [How to write a great agents.md](https://github.blog/ai-and-ml/github-copilot/how-to-write-a-great-agents-md-lessons-from-over-2500-repositories/) by Matt Nigh - Essential reading for agent creators
- ⭐ [Awesome GitHub Copilot](https://github.com/github/awesome-copilot) - Community collection of Copilot resources

## ℹ️ Disclaimer

The agents in this repository are examples created for learning and experimentation. GitHub does not verify, endorse, or guarantee their functionality or security. Always inspect agents and their documentation before use.

---

<div align="center">

**Made with ❤️ by Copilot**

![Copilot Icon](assets/icons8-github-copilot-48.png)

</div>
