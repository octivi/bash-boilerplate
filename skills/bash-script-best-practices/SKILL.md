---
name: bash-script-best-practices
description: Create and refactor Bash scripts using strict mode, getopts, safe quoting, traps, structured logging, and ShellCheck-ready patterns. Use when asked to create a new Bash script, refactor an existing script, harden Bash error handling, standardize CLI behavior, or align scripts with Octivi Bash Boilerplate practices.
---

# Bash Script Best Practices

Follow this workflow for every task.

## 1. Define the script contract

- Identify required inputs, optional inputs, outputs, exit code semantics, and side effects.
- Confirm compatibility constraints before changing existing behavior.
- Capture the CLI shape early: flags, positional args, defaults, and validation rules.

## 2. Choose integration style

- Read `references/obb-integration.md`.
- Choose `full OBB` when rich logging, helper functions, and larger script structure are needed.
- Choose `header-only` when the script is small and minimalism is preferred.

## 3. Execute the right playbook

- For new scripts, use `references/new-script-playbook.md` and start from `assets/templates/`.
- For existing scripts, use `references/refactor-playbook.md` and preserve CLI compatibility unless asked otherwise.

## 4. Enforce Bash safety baseline

- Enforce strict mode and predictable `IFS`.
- Use `getopts` for option parsing.
- Quote expansions unless unquoted behavior is intentionally required.
- Add `trap` handlers for cleanup and reliable error handling.
- Keep logging consistent and machine-readable when practical.

## 5. Finish with quality gate

- Run through `references/checklist.md`.
- Resolve all must-have checklist failures before finalizing.
- Explicitly call out residual risk if any checklist item cannot be satisfied.
