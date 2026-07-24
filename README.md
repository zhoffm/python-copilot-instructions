# 🚀 Copilot Instructions Repository

Welcome to the **Copilot Instructions** repository!  
This project provides a set of best practices, coding rules, and prompt instructions to guide AI-assisted development, especially with GitHub Copilot and similar tools for Python projects.

## 📚 What does this repository do?

- Defines clear coding standards and architectural rules (e.g., Domain-Driven Design, testing strategies).
- Provides prompt and instruction files for consistent, high-quality code generation.
- Helps teams and AI tools follow the same guidelines for maintainable, robust, and expressive Python code.

## 🛠️ How to use this repository

1. **Clone the repository**  
   Open your terminal and run:
   ```bash
   git clone https://github.com/your-username/copilot-instructions.git
   ```
2. **Explore the instructions**
   - **Using GitHub Copilot?** Check the `.github/instructions/` folder for coding rules and best practices, review prompt files in `.github/prompts/` for AI guidance, and read `.github/copilot-instructions.md` for Copilot-specific and Python-specific workflow rules.
   - **Using Cursor?** The same content is mirrored under `.cursor/rules/` (equivalent to `.github/instructions/`) and `.cursor/commands/` (equivalent to `.github/prompts/` + `.github/chatmodes/`), with `AGENTS.md` at the repo root as the Cursor equivalent of `copilot-instructions.md`.
3. **Apply the rules**
   - Follow the documented standards in your projects.
   - Use these files to configure Copilot or other AI tools for consistent code generation.

## ✨ Features

- 🏛️ Domain-Driven Design (DDD) guidelines ([see instructions](.github/instructions/domain-driven-design.instructions.md))
- 🧪 Unit & Integration testing best practices with pytest ([see instructions](.github/instructions/unit-and-integration-tests.instructions.md))
- 📝 English-only documentation policy
- 🤖 Copilot and AI prompt instructions
- 🔄 TDD-first workflow for Python (see `copilot-instructions.md`)
- ❓ Follow-up Question Enforcement ([see instructions](.github/instructions/follow-up-question.instructions.md))  
   AI must ask clarifying questions and show confidence before code generation.
- 🐍 Python coding style with PEP 8 and type hints ([see instructions](.github/instructions/coding-style-python.instructions.md))
- 🎨 Clean Architecture for Python ([see instructions](.github/instructions/clean-architecture.instructions.md))
- 🔧 Pre-commit hooks setup for Python projects ([see prompts](.github/prompts/pre-commit-python.prompt.md))
- 📦 `uv`-first tooling policy — `uv run <tool>` over `pip`/`python -m` ([see instructions](.github/instructions/python-tooling-execution.instructions.md))

## 📂 Repository Structure

- `.github/instructions/` — All coding rules and best practices (Markdown)
- `.github/prompts/` — Prompt files for Copilot and AI tools
- `.github/chatmodes/` — Chatmode files to configure Copilot/AI behavior (e.g. `architect`)
- `.github/copilot-instructions.md` — Main Copilot and Python workflow rules
- `.cursor/rules/` — Cursor equivalent of `.github/instructions/` (`.mdc` files)
- `.cursor/commands/` — Cursor equivalent of `.github/prompts/` + `.github/chatmodes/`
- `AGENTS.md` — Cursor equivalent of `.github/copilot-instructions.md`
- `.vscode/` — VS Code settings for Python development
- `README.md` — This file

## 🧑‍💼 What is a chatmode?

A **chatmode** is a configuration file (in `.github/chatmodes/`) that defines how Copilot or another AI assistant should behave in a specific context or workflow. For example, the `architect` chatmode makes the AI act as an experienced architect and technical lead, focusing on planning, documentation, and Markdown-only outputs. Chatmodes can set the tone, priorities, and constraints for the AI during a session or project.

Chatmode conventions (required file structure, naming, and expected behavior) are documented in [CONTRIBUTING.md](CONTRIBUTING.md) rather than in a dedicated meta-chatmode file.

## 📏 What is an instruction?

An **instruction** is a Markdown file (in `.github/instructions/`) that defines coding rules, architectural standards, and best practices for the project. Instructions are always active and must be followed for all code and documentation generated in the repository. They ensure consistency, maintainability, and alignment with the project's technical vision (e.g., DDD, testing, commit conventions).

A **meta-instruction** is a special instruction file (e.g., `meta-instructions.instructions.md`) that defines how to write, structure, and validate other instruction files. Meta-instructions ensure that all instructions follow a consistent format and best practices across the repository.

## 💡 What is a prompt?

A **prompt** is a template or guidance file (in `.github/prompts/`) used to help Copilot or another AI tool generate code or documentation in a specific style or for a particular use case. Prompts are reusable and can steer the AI in a particular direction for a given task, such as enforcing TDD, writing API documentation, or generating test cases.

## 🧑‍💻 How to contribute

Contributions are welcome!  
Feel free to open issues or submit pull requests to improve the rules, add new practices, or update documentation.

---

> ⚡ **Coming soon:**
>
> - A hands-on workshop to help you understand and build AI-powered Python solutions step by step!
> - Rules and best practices for API endpoints with FastAPI/Flask, feature slicing, and observability.
> - Advanced testing strategies with pytest, coverage, and test fixtures.

Happy coding! 💡✨  
If you have any questions, don't hesitate to open an issue or reach out.
