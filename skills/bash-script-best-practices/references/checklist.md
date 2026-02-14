# Bash Quality Checklist

Mark every item before finalizing a script.

## Must pass

- Strict mode enabled: `set -euo pipefail`
- `IFS` limited to newline and tab
- All variable expansions are quoted unless intentionally unquoted
- Option parsing implemented with `getopts`
- Exit codes are explicit and meaningful
- Cleanup logic uses `trap` where side effects exist
- Input validation exists for required flags and positional arguments
- Errors are written to stderr
- No use of `eval` unless absolutely required and reviewed
- Script is clean under ShellCheck

## Should pass

- `usage()` documents flags, defaults, and examples
- Logging functions (`info`, `warn`, `error`) are consistent
- Functions are small and named by behavior
- Main flow is placed in `main()` and called at file end
- Temporary files are created with `mktemp` and removed in cleanup

## Refactor-specific checks

- Existing CLI flags and outputs stay backward compatible unless requested
- Risky behavior changes are isolated and justified in the summary
- Changes are incremental and easy to review
