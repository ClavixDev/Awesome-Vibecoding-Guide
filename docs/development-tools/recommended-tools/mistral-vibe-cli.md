# Mistral Vibe CLI — The Open Source Coding Agent 🚀

> **The Open Source Champion**: Mistral Vibe CLI is a powerful, open-source command-line coding assistant powered by the state-of-the-art Devstral 2 model. It brings agentic coding to your terminal with a "safety first" approach and deep project awareness.

## Why Mistral Vibe is a "Vibe"

Mistral Vibe isn't just another CLI tool; it's a fully-fledged coding agent that understands your entire project context. It combines the power of Mistral's new Devstral 2 models with a slick, interactive CLI experience that feels native to your workflow.

### Key Differentiators

**Devstral 2 Powered:**
- Built on the Devstral 2 (123B) and Devstral Small 2 (24B) models
- **SOTA Open Model**: Achieves 72.2% on SWE-bench Verified
- **Cost-Efficient**: Up to 7x more cost-efficient than Claude Sonnet at real-world tasks

**Project-Aware Context:**
- Automatically scans your file structure and Git status
- Understands your entire codebase, not just the file you're editing
- Enables architecture-level reasoning for complex refactors

**Powerful Toolset:**
- **Interactive Chat**: Conversational interface that breaks down complex tasks
- **File Manipulation**: Read, write, and patch files with precision
- **Smart Search**: Recursive code search with `grep` (ripgrep support)
- **Shell Integration**: Execute shell commands in a stateful terminal

**Safety & Control:**
- **Safety First**: Features tool execution approval by default
- **Highly Configurable**: Customize models, providers, and tool permissions via `config.toml`
- **Transparent**: Open-source (Apache 2.0) so you know exactly what it's doing

## Installation & Setup

Getting started with Mistral Vibe is incredibly fast.

**One-line Install (Linux/macOS):**
```bash
curl -LsSf https://mistral.ai/vibe/install.sh | bash
```

**Using uv:**
```bash
uv tool install mistral-vibe
```

**Using pip:**
```bash
pip install mistral-vibe
```

**Integration:**
Mistral Vibe is also available as an extension in **[Zed](./zed.md)**, allowing you to use it directly inside your favorite IDE.

## Pricing: Free for Now! 💸

Currently, the Mistral Vibe CLI and the Devstral 2 models powering it are **free to use** via the Mistral API.

- **Devstral 2 (123B)**: Free via API (currently)
- **Devstral Small 2 (24B)**: Free via API (currently)

*Note: After the free period, API pricing will apply ($0.40/$2.00 per million tokens for Devstral 2).*

## When to Use Mistral Vibe

| Scenario | Use Mistral Vibe |
|----------|------------------|
| **Budget Coding** | ✅ **Perfect Choice** (Free SOTA models) |
| **Open Source Preference** | ✅ **Best Choice** (Open weights & code) |
| **Privacy/Control** | ✅ **Great Option** (Run local models supported) |
| **Complex Refactors** | ✅ **Strong Contender** (Project-aware context) |

## Pro Tips for the Vibe

### 1. Interactive Mode
Simply run `vibe` to enter the interactive loop. Use `@` to reference files for smart autocompletion and context loading.

### 2. Auto-Approval
For faster iterations, use the `--auto-approve` flag (or toggle with `Shift+Tab`) to let the agent execute tools without manual confirmation.
```bash
vibe --auto-approve
```

### 3. Smart References
Don't copy-paste paths. Use the smart referencing system:
```bash
> Refactor the @src/main.py file to improve error handling
```

## The Bottom Line

Mistral Vibe CLI is a fantastic addition to the vibecoder's toolkit. It offers a premium, agentic coding experience for **free** (currently), powered by models that rival the best in the industry. If you're looking for an open-source alternative to Claude Code or just want to try the new Devstral models, Mistral Vibe is a must-try.

---

**Related:**
- [Mistral AI](../../ai-model-providers/honorable-mentions/mistral-ai.md) — The provider behind the magic
- [Zed](./zed.md) — Official IDE integration

Back: [Development Tools](../README.md)
