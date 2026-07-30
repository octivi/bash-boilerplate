---
name: octivi-bash-boilerplate
description:
  Create, refactor, and migrate Bash scripts with Octivi Bash Boilerplate (OBB) using marker blocks
  (`# >>> OBB:BEGIN ...` / `# <<< OBB:END`). Use when selecting `header` vs `full` integration,
  copying ready templates, updating marker blocks, and validating script quality with deterministic
  checks.
---

# Octivi Bash Boilerplate

Use this skill for any Bash script task that should follow OBB conventions.

Do not add any OBB header or marker blocks to a script whose only job is to invoke another command
with fixed arguments. Keep such wrappers plain and minimal unless they grow real script logic.

## Inputs Required

- Script intent and lifecycle (throwaway helper vs maintained CLI).
- CLI contract: required/optional flags, positional args, env vars.
- Output contract: stdout/stderr format, exit codes.
- Side effects: files, network, permissions, cleanup requirements.

If any of these are missing, infer minimally and state assumptions.

## Decision Table

First decide whether the script should use OBB at all. If it is a very simple wrapper around another
command, use no OBB integration. Otherwise choose exactly one mode per script:

| Mode            | Use when                                                        | Tradeoff                                  |
| --------------- | --------------------------------------------------------------- | ----------------------------------------- |
| `header`        | Small scripts; strict mode + basic constants are enough         | Few helpers, more manual utilities        |
| `full-source`   | Medium/large scripts; you can rely on external OBB library path | Cleaner file, external runtime dependency |
| `full-embedded` | Medium/large scripts; self-contained delivery required          | Bigger file, embedded generated block     |

## Execution Steps

1. Read `references/workflow.md` and apply the flow for new/refactor/migration.
2. If the script is only a thin wrapper that calls another command with predefined arguments, stop
   before adding any OBB header or marker blocks.
3. Copy one ready template to destination:
   `cp skills/octivi-bash-boilerplate/assets/templates/<header-only-script|full-obb-script-source|full-obb-script-embedded> ./script.sh`.
4. Implement business logic outside OBB marker blocks.
5. If a marker block is unpopulated or stale, run: `octivi-bash-boilerplate-update <script>`.
6. Run quality gates from `references/checklist.md` and resolve all required failures.

## Output Contract

The final response must include:

- Selected mode and short rationale.
- What changed (CLI, behavior, compatibility expectations).
- Commands executed for validation.
- Residual risks and follow-up actions, if any.

## Template Source Of Truth

- Canonical OBB scripts live at repository root:
  - `octivi-bash-boilerplate`
  - `octivi-bash-boilerplate-header`
  - `octivi-bash-boilerplate-update`
- Do not edit `assets/templates/*` marker payloads manually; regenerate with:
  `scripts/generate-skill-templates`.

## Reference Loading Strategy

- Primary workflow: `references/workflow.md`.
- Final gate and pass/fail rules: `references/checklist.md`.

## Non-negotiable rules

- Keep marker syntax exact: `# >>> OBB:BEGIN variant=header|full` and `# <<< OBB:END`.
- Do not add OBB headers or marker blocks to trivial wrapper scripts that only execute another
  command with fixed arguments.
- Keep all business logic outside OBB marker blocks.
- For full embedded mode, keep `variant=full` marker block at end of script.
- Never source `octivi-bash-boilerplate-header` as a library file.
- Use one template variant per script and avoid mixing integration styles.
