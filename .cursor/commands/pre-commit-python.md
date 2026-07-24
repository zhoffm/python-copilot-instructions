# Pre-commit Hooks Setup for Python

## Overview

This prompt helps you set up pre-commit hooks for Python projects with ruff (lint + format), ty, and pytest.

All commands use `uv` per [Python Tooling Execution](../rules/python-tooling-execution.mdc) — never `pip install` or `python -m`.

## Steps

### 1. Install pre-commit

```bash
uv add --dev pre-commit
```

### 2. Create .pre-commit-config.yaml

```yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.5.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml
      - id: check-added-large-files
      - id: check-merge-conflict

  - repo: https://github.com/astral-sh/ruff-pre-commit
    rev: v0.15.22
    hooks:
      - id: ruff-check
        args: [--fix]
      - id: ruff-format

  - repo: https://github.com/astral-sh/ty-pre-commit
    rev: v0.0.56
    hooks:
      - id: ty

  - repo: local
    hooks:
      - id: pytest
        name: pytest
        entry: uv run pytest
        language: system
        pass_filenames: false
        always_run: true
        args: ["-v", "--tb=short"]
```

### 3. Install hooks

```bash
uv run pre-commit install
```

### 4. Run manually (optional)

```bash
# Run on all files
uv run pre-commit run --all-files

# Run on staged files
uv run pre-commit run
```

## Configuration Files

### pyproject.toml

```toml
[tool.ruff]
line-length = 100
target-version = "py314"
select = [
    "E",  # pycodestyle errors
    "W",  # pycodestyle warnings
    "F",  # pyflakes
    "I",  # isort
    "N",  # pep8-naming
    "UP", # pyupgrade
    "B",  # flake8-bugbear
    "C4", # flake8-comprehensions
]
ignore = []
fixable = ["ALL"]

# Note: ty's rule set doesn't map 1:1 to mypy's flags; `all = "error"` is the
# closest strict-equivalent to the old disallow_untyped_defs/warn_* settings.
[tool.ty.environment]
python-version = "3.14"

[tool.ty.rules]
all = "error"

[tool.pytest.ini_options]
testpaths = ["tests"]
python_files = ["test_*.py", "*_test.py"]
python_classes = ["Test*"]
python_functions = ["test_*"]
addopts = "-v --tb=short --strict-markers"
markers = [
    "unit: Unit tests",
    "integration: Integration tests",
    "slow: Slow tests",
]
```

## Usage

After setup, hooks will run automatically on `git commit`:

```bash
git add .
git commit -m "feat: add order processing"
# Hooks run automatically:
# - Lint with ruff check
# - Format with ruff format
# - Type check with ty
# - Run pytest
```

## Skip Hooks (Emergency Only)

```bash
git commit --no-verify -m "emergency fix"
```

## Benefits

- ✅ Consistent code formatting
- ✅ Catch errors before commit
- ✅ Ensure tests pass
- ✅ Automatic import sorting
- ✅ Type checking enforcement
- ✅ Team consistency
