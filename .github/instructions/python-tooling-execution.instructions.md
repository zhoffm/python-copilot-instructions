---
description: "Require uv for running Python tools, scripts, and dependency management"
---

# Python Tooling Execution Instructions

## Overview

This project manages its Python environment and dependencies with [`uv`](https://docs.astral.sh/uv/). Every Python tool (`pytest`, `ruff`, `mypy`, `ty`, `black`, `uvicorn`, `pre-commit`, etc.) and every Python script must be run through `uv`, either directly or via an activated `uv`-managed virtual environment.

## Allowed Ways to Run Tools

Only two invocation patterns are acceptable:

1. **`uv run <tool>` (preferred)** — runs the tool inside the project's `uv`-managed environment without requiring manual activation. Use this by default, especially in documentation, CI, and one-off commands.

   ```bash
   uv run pytest
   uv run ruff check --fix .
   uv run mypy src/
   uv run uvicorn api.main:app --reload
   uv run python script.py
   ```

2. **Activate the `uv`-managed virtual environment, then invoke the tool directly.** Once `.venv` (created by `uv venv` or `uv sync`) is activated, call the tool by its own name, never through `python -m`.

   ```bash
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   pytest
   ruff check --fix .
   mypy src/
   ```

## Forbidden Patterns

❌ **Never** invoke a tool as a `python -m` module, even if it happens to work:

```bash
python -m pytest      # Bad: use `pytest` (venv active) or `uv run pytest`
python -m ruff check  # Bad: use `ruff check` (venv active) or `uv run ruff check`
python script.py      # Bad: use `uv run python script.py` or activate venv then `python script.py`
```

❌ **Never** install or manage dependencies with `pip`, `pip-tools`, `poetry`, or `venv` directly:

```bash
pip install pytest           # Bad
python -m venv .venv         # Bad
pip install -r requirements.txt  # Bad
```

✅ Use `uv` for all dependency management instead:

```bash
uv add <package>              # Add or upgrade a dependency
uv add --dev <package>        # Add a dev-only dependency
uv remove <package>           # Remove a dependency
uv sync                       # Reinstall all dependencies from the lock file
uv venv                       # Create the virtual environment
```

## Scripts and Entry Points

- Run standalone scripts with `uv run script.py`, not `python script.py`.
- For scripts with inline dependency metadata (PEP 723), keep dependencies in sync with `uv add <package> --script script.py` / `uv remove <package> --script script.py` / `uv sync --script script.py`.
- Configure `pre-commit` local hooks, Makefiles, and CI pipelines to call tools as `uv run <tool>` so they work without requiring a pre-activated shell.

## Documentation and Generated Content

When writing README files, setup guides, or prompt/instruction templates that show installation or usage commands, always present the `uv` workflow (`uv sync`, `uv run <tool>`) as the primary path. A `pip`/`venv` fallback may only be mentioned if the user explicitly asks for one.

## Validation Checklist

- [ ] All tool invocations use `uv run <tool>` or assume an activated `uv`-managed venv
- [ ] No `python -m <tool>` invocations for tools that have their own entry point
- [ ] No `pip install`, `pip-tools`, or `poetry` commands
- [ ] No `python -m venv` — environments are created with `uv venv` or `uv sync`
- [ ] Generated docs/READMEs show `uv` as the primary workflow
