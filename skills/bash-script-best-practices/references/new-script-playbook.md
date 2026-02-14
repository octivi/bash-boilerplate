# New Script Playbook (Greenfield)

Use this flow for creating a script from scratch.

## 1. Capture requirements

- Define command purpose in one sentence.
- Define input contract: required/optional flags, positional args, env vars.
- Define output contract: stdout format, stderr format, exit codes.

## 2. Select a template

- Use `assets/templates/full-obb-script` for richer CLI scripts.
- Use `assets/templates/header-only-script` for compact scripts.
- Rename placeholders before adding task-specific logic.

## 3. Implement CLI and validation first

- Implement `usage()` and keep it updated with actual behavior.
- Parse options with `getopts`.
- Validate required flags early and fail fast with clear errors.

## 4. Implement behavior in focused functions

- Keep one function for one responsibility.
- Avoid global mutable state when possible.
- Return status codes from functions and handle errors explicitly.

## 5. Add reliability features

- Add `trap` cleanup when creating temp files or external side effects.
- Make logging consistent and timestamped when useful.
- Ensure the script behaves safely under strict mode.

## 6. Final quality gate

- Run the checklist in `references/checklist.md`.
- Fix all must-pass items.
