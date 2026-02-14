# Refactor Playbook (Brownfield)

Use this flow for improving an existing Bash script safely.

## 1. Baseline before changes

- Record current CLI behavior: flags, positional args, default values, exit codes.
- Record output behavior: stdout/stderr shape and important messages.
- Identify risky zones: unquoted expansions, ad-hoc parsing, hidden side effects.

## 2. Define compatibility target

- Keep user-facing behavior stable unless the request says otherwise.
- If breaking changes are required, make them explicit and controlled.

## 3. Apply incremental hardening

- Introduce strict mode and `IFS` carefully.
- Replace ad-hoc argument parsing with `getopts`.
- Fix quoting issues and avoid word-splitting bugs.
- Introduce `trap`-based cleanup where side effects exist.
- Normalize error handling and exit codes.

## 4. Keep changes reviewable

- Change one concern at a time.
- Preserve names and interfaces where possible.
- Add short comments only where logic is non-obvious.

## 5. Verify and summarize

- Run the checklist in `references/checklist.md`.
- Summarize what changed, what stayed compatible, and any residual risk.
