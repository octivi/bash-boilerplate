# OBB Integration Guide

Choose one integration mode per script.

## Mode selection

| Mode        | Choose when                                                      | Tradeoff                        |
| ----------- | ---------------------------------------------------------------- | ------------------------------- |
| Full OBB    | Script is medium/large, needs richer helpers and consistent logs | More code and structure         |
| Header-only | Script is small and straightforward                              | Fewer helpers, more manual code |

## Full OBB mode

- Start from `assets/templates/full-obb-script`.
- Source `octivi-bash-boilerplate` (default `/usr/local/share/octivi-bash-boilerplate`, override with `OBB_PATH`).
- Keep strict mode, getopts parsing, trap cleanup, and structured logging.
- Prefer this mode when the script has multiple functions or non-trivial control flow.

## Header-only mode

- Start from `assets/templates/header-only-script`.
- Copy the header block from `octivi-bash-boilerplate-header` into the script (do not source the header file directly).
- Keep the script compact while preserving strict mode and safe parsing.
- Prefer this mode when the script has minimal options and short flow.

## Migration guidance

- For refactors, select mode based on script complexity and expected lifespan.
- If uncertain, pick Full OBB for maintainability.
