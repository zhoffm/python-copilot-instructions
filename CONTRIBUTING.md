# Contributing to Copilot Instructions

Thank you for your interest in contributing to this project! This repository aims to provide high-quality coding instructions and prompts for Python development with GitHub Copilot.

## How to Contribute

### Adding New Instructions

1. **Follow the Template**: Use the structure defined in [meta-instructions.instructions.md](.github/instructions/meta-instructions.instructions.md)

2. **Naming Convention**: Use `<topic-name>.instructions.md`

3. **Required Sections**:

   - YAML frontmatter with description
   - Overview
   - Main content with examples
   - Validation checklist

4. **Code Examples**: Include both good (✅) and bad (❌) examples

5. **Testing**: Ensure examples are correct and follow Python best practices

### Adding New Prompts

1. **File Extension**: Use `.prompt.md`

2. **Content**: Provide step-by-step guidance for specific tasks

3. **Examples**: Include complete, working examples

### Adding New Chat Modes

1. **File Extension**: Use `.chatmode.md`

2. **Structure**:
   - Description
   - Behavior guidelines
   - Communication style
   - Priorities

### Adding New Cursor Rules

1. **Location**: Add to `.cursor/rules/`

2. **Naming Convention**: Use `<topic-name>.mdc`

3. **Required Frontmatter**:

   - `description`: Brief description (same text as the mirrored `.instructions.md` file)
   - `globs`: File pattern the rule applies to (mirrors `applyTo`), omit if always active
   - `alwaysApply`: `true` for always-active rules (mirrors omitting `applyTo`), `false` otherwise

4. **Content**: Should be the same body content as its mirrored `.github/instructions/*.instructions.md` file — only the frontmatter format and internal cross-reference links differ.

### Adding New Cursor Commands

1. **Location**: Add to `.cursor/commands/`

2. **File Extension**: Use `.md` (no special suffix)

3. **Content**: Mirrors either a `.prompt.md` file or a `.chatmode.md` file — chatmode-derived commands should reframe "You are in X mode" language as "Enter X mode for the rest of this conversation" since commands are invoked mid-conversation rather than being a persistent mode.

### Keeping Copilot and Cursor in Sync

This repository ships equivalent content for both GitHub Copilot (`.github/`) and Cursor (`.cursor/`, `AGENTS.md`). Whenever you add or update an instruction, prompt, or chat mode, make the matching change to its Cursor rule/command counterpart (and vice versa) in the same pull request, so the two ecosystems never drift apart.

## Pull Request Process

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-new-instruction`
3. Make your changes
4. Ensure all examples are correct
5. If you touched `.github/`, make the matching update under `.cursor/` (or `AGENTS.md`), and vice versa
6. Update README.md if needed
7. Commit using Conventional Commits: `feat(instructions): add async programming guide`
8. Push to your fork
9. Create a Pull Request

## Style Guide

- Write in English only
- Use clear, concise language
- Follow Python naming conventions in examples
- Include type hints in all Python examples
- Use Ruff formatting for code examples (`uv run ruff format`)
- Test all code examples

## Code Review Guidelines

Reviewers will check:

- [ ] Follows the meta-instructions format
- [ ] Examples are correct and working
- [ ] Clear and understandable
- [ ] Consistent with existing instructions
- [ ] No grammatical errors

## Questions?

Feel free to open an issue for discussion before submitting a large contribution.

Thank you for helping improve this project! 🎉
