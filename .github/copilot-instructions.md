# Copilot instructions

## Language Policy

All instructions and prompts in this repository must be written in English. This applies to:

- All rule and instruction files in `.github/instructions/`
- All prompt files in `.github/prompts/`
- All documentation and code comments intended for contributors

## Development code generation

When working with Python code, follow these instructions very carefully.

It is **EXTREMELY important that you follow the instructions in the rule files very carefully.**

### Workflow implementation

**IMPORTANT:** Always follow these steps when implementing new features:

1. Consult any relevant instructions files listed below and start by listing which rule files have been used to guide the implementation (e.g. `Instructions used: [clean-architecture.instructions.md, domain-driven-design.instructions.md]`).

2. Follow TDD when it is possible. Always start new changes by writing new test cases (or changing existing tests).
   Remember to consult [Unit and Integration Tests](./instructions/unit-and-integration-tests.instructions.md) for details on how to write tests with pytest.

3. Always run `uv run pytest` (or `pytest` with the `uv`-managed virtual environment activated) to verify that all tests pass before committing your changes. Never use `python -m pytest`.
   Don't ask to run the tests, just do it. If you are not sure how to run the tests, ask for help.
   You can also use `uv run pytest-watch` to run the tests automatically when you change the code.
   See [Python Tooling Execution](./instructions/python-tooling-execution.instructions.md) for the full policy on running tools and managing dependencies with `uv`.

4. Fix any linting errors with `uv run ruff` and type checking warnings using `uv run ty` before going to the next step.

5. Ensure code coverage is maintained or improved. Use `uv run pytest --cov` to check coverage.

When you see paths like `/[project]/features/[feature]/` in rules, replace [project] with the name of the project you are working on (e.g. `ordering`), and `[feature]` with the name of the feature you are working on (e.g. `verify_or_add_payment`).

## Python-specific guidelines

- Use type hints for all function signatures and class attributes
- Follow PEP 8 style guide (enforced by ruff formatting and linting)
- Use Pydantic models for data structures
- Prefer composition over inheritance
- Use context managers for resource management
- Follow the Zen of Python principles
