# Create README

## Role

You're a senior expert Python software engineer with extensive experience in open source projects. You always make sure the README files you write are appealing, informative, and easy to read.

## Task

1. Take a deep breath, and review the entire project and workspace, then create a comprehensive and well-structured README.md file for the Python project.
2. Include the following sections where appropriate:
   - **Project Title** with a brief tagline
   - **Features** - Key capabilities and highlights
   - **Installation** - Step-by-step setup instructions including virtual environment
   - **Usage** - Clear examples with code snippets
   - **Configuration** - Environment variables or configuration files
   - **Development** - How to set up development environment
   - **Testing** - How to run tests with pytest
   - **API Documentation** - If applicable (FastAPI, Flask, etc.)
   - **Contributing** - Reference to CONTRIBUTING.md if it exists
   - **License** - Reference to LICENSE file if it exists
3. Use GFM (GitHub Flavored Markdown) for formatting, and GitHub admonition syntax where appropriate.
4. Do not overuse emojis, and keep the readme concise and to the point.
5. Do not include sections like "LICENSE", "CONTRIBUTING", "CHANGELOG" with full content. There are dedicated files for those sections.
6. If you find a logo or icon for the project, use it in the readme's header.
7. For Python projects, include:
   - Python version requirements (e.g., "Python 3.11+")
   - Environment and dependency setup with `uv` (see [Python Tooling Execution](../rules/python-tooling-execution.mdc)) — `uv sync` as the primary path, only mention pip/poetry if the project explicitly uses them
   - Pre-commit hooks setup if applicable
   - Type checking and linting commands run via `uv run <tool>`

## Example Structure

```markdown
# Project Name

> Brief, compelling description of what this project does

## Features

- ✨ Feature 1
- 🚀 Feature 2
- 🔒 Feature 3

## Requirements

- Python 3.11+
- [uv](https://docs.astral.sh/uv/)

## Installation

\`\`\`bash

# Create the virtual environment and install dependencies from the lock file

uv sync
\`\`\`

## Usage

\`\`\`python
from your_package import YourClass

# Example usage

instance = YourClass()
result = instance.do_something()
\`\`\`

## Configuration

Configure the application using environment variables:

\`\`\`bash
export API_KEY=your_api_key
export DATABASE_URL=postgresql://user:pass@localhost/db
\`\`\`

Or create a `.env` file:

\`\`\`env
API_KEY=your_api_key
DATABASE_URL=postgresql://user:pass@localhost/db
\`\`\`

## Development

### Setup

\`\`\`bash

# Install dependencies (including dev extras) from the lock file

uv sync

# Install pre-commit hooks

uv run pre-commit install
\`\`\`

### Running Tests

\`\`\`bash

# Run all tests

uv run pytest

# Run with coverage

uv run pytest --cov=src --cov-report=html

# Run specific test file

uv run pytest tests/test_module.py
\`\`\`

### Code Quality

\`\`\`bash

# Format code

uv run black .

# Lint

uv run ruff check .

# Type checking

uv run mypy src/
\`\`\`

## API Documentation

If this is a web API (FastAPI, Flask):

\`\`\`bash

# Run the server

uv run uvicorn main:app --reload

# Access API docs

open http://localhost:8000/docs
\`\`\`

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for details on how to contribute.

## License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.
\`\`\`

## Guidelines

- Be concise but comprehensive
- Include actual code examples from the project
- Show `uv` as the primary installation and dependency workflow (`uv sync`); only document pip/poetry if the project explicitly uses them instead of `uv`
- Show how to run tests and checks via `uv run <tool>` (see [Python Tooling Execution](../rules/python-tooling-execution.mdc)) — never `pip install` or `python -m`
- Use admonitions for important notes or warnings
- Keep the tone professional but friendly
- Ensure all code blocks have proper syntax highlighting
```
