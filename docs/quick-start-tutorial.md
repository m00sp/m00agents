# 🚀 Quick Start Tutorial: Using readme-creator Agent in Copilot CLI

This tutorial teaches you how to use the **readme-creator** agent in the Copilot CLI with hands-on practice exercises. Type the commands yourself to reinforce your learning!

---

## Part 1: Understanding the Basics

The Copilot CLI lets you interact with custom agents directly from your terminal. These agents are specialized AI personas designed for specific tasks.

### Key Commands Reference

| Command | Purpose |
|---------|---------|
| `copilot <prompt>` | Ask Copilot a question |
| `copilot /agent` | List all available agents |
| `copilot --agent=<agent-name> "<prompt>"` | Use a specific agent |
| `copilot --help` | Get help on CLI commands |

---

## Part 2: The readme-creator Agent

The **readme-creator** agent specializes in creating and improving README files. It understands:
- Project structure and purpose
- Clear documentation patterns
- README best practices (sections, formatting, links)
- Installation and usage examples

### What It Can Do

✅ Create new README files from scratch  
✅ Review and improve existing READMEs  
✅ Add missing sections (Installation, Usage, Contributing)  
✅ Reorganize content with proper structure  
✅ Add badges and formatting  
✅ Create Table of Contents  
✅ Fix links (relative vs absolute)  

### What It Won't Do

🚫 Modify code files  
🚫 Change project dependencies  
🚫 Remove existing documentation without asking  
🚫 Create misleading or inaccurate content  

---

## Part 3: Three Ways to Access the Agent

### Method 1: Explicit Agent Selection (Recommended for Learning)

```bash
copilot --agent=readme-creator "Your prompt here"
```

**Example:**
```bash
copilot --agent=readme-creator "Create a README for the m00agents project"
```

**Why use this method?**
- Clear and intentional
- Good for automation and scripting
- Makes it obvious which agent is handling your request

### Method 2: Interactive Agent Selection

```bash
copilot
```

Then type `/agent` in the interactive prompt and select from the list.

**Why use this method?**
- Good for exploring what agents are available
- Conversational flow
- Can ask follow-up questions in the same session

### Method 3: Auto-Detection (Advanced)

```bash
copilot "Use the readme-creator agent to improve our README"
```

Copilot will automatically infer which agent you want.

**Why use this method?**
- Natural language interaction
- Less memorization of agent names
- Good for casual use

---

## Part 4: Practice Exercises

### Exercise 1: View Agent Capabilities

**Goal:** Ask the readme-creator agent what it can do for your project

**Your task - Type this command:**
```bash
copilot --agent=readme-creator "What can you help me with for README files?"
```

**What to expect:**
- The agent will explain its capabilities
- It will ask clarifying questions about your project
- It might suggest areas where README could be improved

**Tips:**
- Take note of any specific capabilities that interest you
- The agent may ask follow-up questions about your repository

---

### Exercise 2: Analyze the Current README

**Goal:** Get feedback on the existing README.md

**Your task - Type this command:**
```bash
copilot --agent=readme-creator "Review the current README and tell me what's good and what could be improved"
```

**What to expect:**
- Analysis of current structure
- Suggestions for improvements
- Specific sections that could be better

**Tips:**
- Notice whether the agent finds the right README
- Pay attention to specific suggestions—these are actionable

---

### Exercise 3: Add a Specific Section

**Goal:** Improve a specific part of the README

**Your task - Type this command:**
```bash
copilot --agent=readme-creator "Add a 'Quick Start' section to the README that shows how to install and use the agents"
```

**What to expect:**
- A new "Quick Start" section (formatted, with examples)
- Integration with existing content
- Proper formatting and links

**Tips:**
- You can ask for the section as text first, then save it
- Or ask the agent to directly modify the README if you give it permission

---

### Exercise 4: Create a Complete README

**Goal:** Generate a fully-structured README from scratch

**Your task - Type this command:**
```bash
copilot --agent=readme-creator "Create a comprehensive README for the m00agents project with all standard sections"
```

**What to expect:**
- Title with badges
- Quick description
- Installation instructions
- Usage examples
- Project structure explanation
- Contributing guidelines
- License information
- Support section

**Tips:**
- The agent will generate a template
- You can ask it to adjust sections
- Review before applying it to your repository

---

### Exercise 5: Fix Specific Issues

**Goal:** Address particular README problems

**Your task - Choose one and type the command:**

**Option A - Add badges:**
```bash
copilot --agent=readme-creator "Add status and license badges to the top of the README"
```

**Option B - Improve links:**
```bash
copilot --agent=readme-creator "Review all links in the README. Use relative links for internal files and absolute links for external resources"
```

**Option C - Better formatting:**
```bash
copilot --agent=readme-creator "Improve the README formatting with better headings, code blocks, and bullet points"
```

**What to expect:**
- Specific improvements in one area
- Before/after comparison if you ask for it
- Ready-to-use content

---

## Part 5: Advanced Usage Patterns

### Chaining Commands

After getting suggestions, ask follow-up questions:

```bash
copilot --agent=readme-creator "Improve the README"
# Agent responds with suggestions
# Then you ask: "Can you make the installation section more detailed?"
```

### Working with Specific Sections

```bash
copilot --agent=readme-creator "Review only the 'Installation' section and suggest improvements"
```

### Asking About Style

```bash
copilot --agent=readme-creator "Make the README more concise and action-oriented"
```

### Getting Examples

```bash
copilot --agent=readme-creator "Show me examples of good README formatting for a Node.js project"
```

---

## Part 6: Agent Configuration (Project Knowledge)

The readme-creator agent performs better when it understands your project. You can help it by:

### Telling it About Your Tech Stack

```bash
copilot --agent=readme-creator "Create a README for a JavaScript/Node.js project that helps users understand GitHub Copilot agents"
```

### Specifying Project Type

```bash
copilot --agent=readme-creator "Create a README for a CLI tool written in Go that manages deployment workflows"
```

### Providing Context

```bash
copilot --agent=readme-creator "Our project is a collection of custom agents. Users install them locally or in their repos. Create a README that explains this clearly"
```

---

## Part 7: Common Scenarios

### Scenario A: New Project

```bash
copilot --agent=readme-creator "I'm starting a new Node.js API project. Create a README template I can use"
```

### Scenario B: Existing Project Needs Update

```bash
copilot --agent=readme-creator "Our README is outdated. Here's what changed: [describe changes]. Please update the relevant sections"
```

### Scenario C: Complex Setup

```bash
copilot --agent=readme-creator "Create clear installation instructions for a project that requires Docker, Node 18+, and environment variables. Make it beginner-friendly"
```

### Scenario D: Documentation for New Team Member

```bash
copilot --agent=readme-creator "Write a README section that helps new team members understand the project structure and get up to speed quickly"
```

---

## Part 8: Tips & Best Practices

### ✅ Do This

- **Be specific**: "Add installation steps for macOS, Windows, and Linux" (not "fix the README")
- **Provide context**: Tell the agent about your project type and audience
- **Ask for iterations**: "Now make it more concise" after getting initial suggestions
- **Review carefully**: Always read the generated content before using it
- **Use relative links**: Link to internal files, absolute URLs for external resources

### ❌ Avoid This

- ❌ Vague requests: "Make it better"
- ❌ No context: Agent might guess wrong about your project
- ❌ Large requests without sections: Break it into smaller tasks
- ❌ Trusting without reviewing: Always verify generated content

---

## Part 9: Next Steps

### After You Practice These Exercises

1. **Try creating a README** for one of your own projects
2. **Explore other agents** like `test-creator`, `docs-creator`, `api-builder`
3. **Combine agents** - Use docs-creator for CONTRIBUTING.md, readme-creator for README.md
4. **Read the agent definition** to understand its exact capabilities: `agents/readme-creator.agent.md`

### To Deepen Your Learning

- Read `.github/copilot-instructions.md` for the full repository context
- Check other `.agent.md` files to understand the format
- Explore the GitHub Copilot CLI documentation: `copilot --help`
- Create your own custom agent using `agents/starter-template.md`

---

## Part 10: Troubleshooting

**"Agent not found"**
- Make sure the agent file is in `.github/agents/` or `~/.copilot/agents/`
- Check the filename is `readme-creator.agent.md`

**"Agent not responding as expected"**
- Be more specific in your prompt
- Provide project context
- Ask it to explain what it will do before doing it

**"Generated README has errors"**
- Always review before applying
- Ask the agent to fix specific issues
- Verify links and formatting manually

---

## Quick Reference: One-Liners

```bash
# View agent capabilities
copilot --agent=readme-creator "What can you help me with?"

# Analyze current README
copilot --agent=readme-creator "Review the README and suggest improvements"

# Add a section
copilot --agent=readme-creator "Add a 'Features' section"

# Create from scratch
copilot --agent=readme-creator "Create a complete README"

# Fix formatting
copilot --agent=readme-creator "Improve formatting and structure"

# Add badges
copilot --agent=readme-creator "Add license and status badges"

# Make it concise
copilot --agent=readme-creator "Make the README more concise"

# Better examples
copilot --agent=readme-creator "Add code examples for each feature"
```

---

## Resources

- **Agent Definition**: `agents/readme-creator.agent.md`
- **Repository Instructions**: `.github/copilot-instructions.md`
- **Starter Template**: `agents/starter-template.md` (reference for all agents)
- **Main Documentation**: `docs/README.m00agents.md`

---

**Happy Learning! 🎉**

Start with Exercise 1, work through the exercises at your own pace, and don't hesitate to experiment. The best way to learn is by doing!
