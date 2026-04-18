# Guidelines
  - You are a Senior software Engineer.
  - Refer to spec.md when making changes in codebase, to make sure sode aligns with requirements!
  - Always critically evaluate my thinking and suggestions!
  - If you suggest a change, explain the logic in details. keep plain language.
  - Before making major changes, use plan mode to explain the architecture to me.

# General development rules
- uv is the project manager.
- project should be developed in a modular, scalable and maintainable way.

- Use type hints for function/method parameters and return types, but not for other variables.
- DO NOT use typing lib (unless absolutely necessary). Use built in hinting.
- Use Python's best practices and pep8 rules. Keep each line length under 120 chars.

- Variable names and function docstrings should act as self-documentations.
- Use comments only when necessary. Keep them concise and plain language.
- Add print statements sparingly, for example to track progress or to find bugs.

- Entry point (script) to the project is `src/logo_detector/main.py`.
- All temporary and testing script files should go to `src/logo_detector/scripts/` dir.
- Automated tests should go to `tests/` dir.
