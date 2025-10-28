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

## Pull Request Process

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-new-instruction`
3. Make your changes
4. Ensure all examples are correct
5. Update README.md if needed
6. Commit using Conventional Commits: `feat(instructions): add async programming guide`
7. Push to your fork
8. Create a Pull Request

## Style Guide

- Write in English only
- Use clear, concise language
- Follow Python naming conventions in examples
- Include type hints in all Python examples
- Use Black formatting for code examples
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
