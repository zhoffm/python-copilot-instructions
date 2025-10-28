# Quick Start Guide

## Repository Structure

```
copilot-instructions/
├── .github/
│   ├── copilot-instructions.md      # Main Copilot configuration
│   ├── instructions/                # Coding rules and standards (9 files)
│   │   ├── clean-architecture.instructions.md
│   │   ├── coding-style-python.instructions.md
│   │   ├── conventional-commits.instructions.md
│   │   ├── domain-driven-design.instructions.md
│   │   ├── follow-up-question.instructions.md
│   │   ├── meta-instructions.instructions.md
│   │   ├── object-calisthenics.instructions.md
│   │   ├── security-and-owasp.instructions.md        # NEW: OWASP security for Python
│   │   └── unit-and-integration-tests.instructions.md
│   ├── prompts/                     # Reusable prompts (4 files)
│   │   ├── create-readme.prompt.md                   # NEW: Generate README files
│   │   ├── fastapi-setup.prompt.md
│   │   ├── pre-commit-python.prompt.md
│   │   └── python-mcp-server-generator.prompt.md     # NEW: MCP server scaffold
│   └── chatmodes/                   # AI personas (6 files)
│       ├── architect.chatmode.md
│       ├── debug.chatmode.md                         # NEW: Systematic debugging
│       ├── python-expert.chatmode.md
│       ├── tdd-green.chatmode.md                     # NEW: TDD implementation phase
│       ├── tdd-red.chatmode.md                       # NEW: TDD test-first phase
│       └── tdd-refactor.chatmode.md                  # NEW: TDD cleanup phase
├── .vscode/
│   ├── settings.json                # Python development settings
│   └── extensions.json              # Recommended extensions
├── .gitignore                       # Python-specific ignores
├── CODEOWNERS                       # Code ownership
├── CONTRIBUTING.md                  # Contribution guidelines
├── LICENSE                          # MIT License
├── pyproject.toml.example           # Example Python configuration
└── README.md                        # This file
```

## How to Use

### 1. For Your Repository

Copy this structure to your Python project:

```bash
# Copy the entire .github folder
cp -r .github /path/to/your/project/

# Or just specific files you need
cp .github/copilot-instructions.md /path/to/your/project/.github/
```

### 2. Instructions Files

Located in `.github/instructions/`, these define **always-active** coding rules:

- **clean-architecture.instructions.md**: Layer separation (Domain, Application, Infrastructure)
- **domain-driven-design.instructions.md**: DDD patterns (Entities, Value Objects, Aggregates)
- **coding-style-python.instructions.md**: PEP 8, type hints, Black, Ruff
- **unit-and-integration-tests.instructions.md**: pytest best practices
- **object-calisthenics.instructions.md**: OOP design rules
- **conventional-commits.instructions.md**: Commit message format
- **follow-up-question.instructions.md**: AI asks questions before generating code

### 3. Prompts

Located in `.github/prompts/`, these are **reusable templates**:

- **pre-commit-python.prompt.md**: Set up pre-commit hooks with Black, Ruff, mypy, pytest
- **fastapi-setup.prompt.md**: Create FastAPI application structure

Use prompts in Copilot Chat:

```
@workspace Use the pre-commit-python prompt to set up hooks
```

### 4. Chat Modes

Located in `.github/chatmodes/`, these define **AI personas**:

- **architect.chatmode.md**: Acts as a software architect (planning, diagrams)
- **python-expert.chatmode.md**: Acts as Python expert (code, tests, best practices)

Activate in Copilot Chat:

```
/mode architect
```

## Key Features

### Python-Specific Adaptations

- ✅ **pytest** instead of xUnit/NUnit
- ✅ **Black + Ruff + mypy** instead of .NET formatters
- ✅ **FastAPI** examples instead of ASP.NET
- ✅ **Type hints** everywhere
- ✅ **Dataclasses** and **Pydantic** for models
- ✅ **Protocols** for dependency inversion
- ✅ **Pre-commit hooks** instead of Husky

### TDD Workflow

The main `.github/copilot-instructions.md` enforces:

1. Consult relevant instruction files
2. Write tests FIRST (TDD)
3. Run `pytest` to verify
4. Fix linting errors (Ruff, Black, mypy)
5. Check coverage (`pytest --cov`)

## Example Workflow

### Creating a New Feature

1. **Copilot reads instructions** automatically
2. **You ask**: "Create an order processing use case"
3. **Copilot asks** (follow-up-question.instructions.md):
   - What should this use case do?
   - Should it follow DDD patterns?
   - What tests are needed?
4. **You answer** the questions
5. **Copilot generates**:
   - Tests first (TDD)
   - Domain entities
   - Use case implementation
   - Repository interface
6. **Copilot runs** `pytest` automatically
7. **Copilot checks** Black/Ruff/mypy

## Customization

### Add Your Own Instructions

1. Create `your-topic.instructions.md` in `.github/instructions/`
2. Follow the format in `meta-instructions.instructions.md`
3. Include frontmatter, examples, and checklist

### Add Your Own Prompts

1. Create `your-task.prompt.md` in `.github/prompts/`
2. Provide step-by-step guidance
3. Include complete examples

### Add Your Own Chat Modes

1. Create `your-persona.chatmode.md` in `.github/chatmodes/`
2. Define behavior, style, and priorities

## Quick Reference

### Run Tests

```bash
pytest                           # Run all tests
pytest tests/unit/               # Run unit tests only
pytest --cov                     # With coverage
pytest -v --tb=short             # Verbose with short traceback
```

### Format Code

```bash
black .                          # Format all files
ruff check --fix .               # Lint and auto-fix
mypy src/                        # Type checking
```

### Pre-commit

```bash
pre-commit install               # Install hooks
pre-commit run --all-files       # Run manually
```

## Learning Path

1. **Start with**: `copilot-instructions.md` - understand the workflow
2. **Then read**: `clean-architecture.instructions.md` - understand the structure
3. **Next**: `domain-driven-design.instructions.md` - understand DDD patterns
4. **Finally**: `coding-style-python.instructions.md` - understand Python conventions

## Next Steps

1. ✅ Copy this structure to your project
2. ✅ Customize instructions for your needs
3. ✅ Set up pre-commit hooks
4. ✅ Configure your editor (.vscode/settings.json)
5. ✅ Start using Copilot with these instructions!

## Resources

- [Conventional Commits](https://www.conventionalcommits.org/)
- [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
- [Domain-Driven Design](https://martinfowler.com/bliki/DomainDrivenDesign.html)
- [pytest Documentation](https://docs.pytest.org/)
- [FastAPI Documentation](https://fastapi.tiangolo.com/)

## Questions?

Open an issue or refer to `CONTRIBUTING.md` for contribution guidelines.

Happy coding! 🐍✨
