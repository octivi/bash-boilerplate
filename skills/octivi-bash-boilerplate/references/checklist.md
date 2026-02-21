# Bash Quality Checklist

Mark every item before finalizing a script.

## Pass/Fail Gates

| ID     | Level       | Gate                    | Pass criteria                                                                                      |
| ------ | ----------- | ----------------------- | -------------------------------------------------------------------------------------------------- |
| `Q-01` | Required    | Strict mode             | `set -euo pipefail` is enabled                                                                     |
| `Q-02` | Required    | `IFS` safety            | `IFS` is restricted to newline and tab                                                             |
| `Q-03` | Required    | Marker integrity        | Marker syntax is valid and paired (`# >>> OBB:BEGIN ...` / `# <<< OBB:END`)                        |
| `Q-04` | Required    | Marker isolation        | Business logic is outside OBB marker blocks                                                        |
| `Q-05` | Required    | Quoting                 | Expansions are quoted unless intentionally unquoted                                                |
| `Q-06` | Required    | CLI parsing             | Option parsing is deterministic (`getopts` preferred; alternatives must be explicit and justified) |
| `Q-07` | Required    | Exit semantics          | Exit codes are explicit and meaningful                                                             |
| `Q-08` | Required    | Cleanup                 | `trap` cleanup exists when side effects or temp files exist                                        |
| `Q-09` | Required    | Input validation        | Required flags/args are validated early with clear errors                                          |
| `Q-10` | Required    | Error channel           | Errors are written to stderr                                                                       |
| `Q-11` | Required    | Dangerous eval          | `eval` is absent, or documented and reviewed when unavoidable                                      |
| `Q-12` | Required    | Static lint             | Script is clean under `shellcheck` (or documented why unavailable)                                 |
| `Q-13` | Recommended | Usage quality           | `usage()` documents flags, defaults, examples                                                      |
| `Q-14` | Recommended | Logging quality         | Logging functions are consistent and meaningful                                                    |
| `Q-15` | Recommended | Structure               | Main flow is in `main()` and invoked once                                                          |
| `Q-16` | Recommended | Refactor compatibility  | Existing CLI behavior remains compatible unless change is requested                                |
| `Q-17` | Required    | Full-embedded readiness | For `full-embedded`, the `variant=full` block is populated before delivery                         |
