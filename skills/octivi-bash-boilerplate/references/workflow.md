# OBB Workflow (Canonical)

This is the canonical procedure for new scripts, refactors, and mode migrations.

## 1. Capture Contract

- Define purpose in one sentence.
- Define CLI input contract: flags, args, env vars, defaults.
- Define output contract: stdout/stderr format and exit codes.
- Define side effects and cleanup strategy.

## 2. Choose One Integration Mode

| Mode            | Choose when                                        | Notes                                                  |
| --------------- | -------------------------------------------------- | ------------------------------------------------------ |
| `header`        | Small, straightforward scripts                     | Keep local helpers minimal and explicit                |
| `full-source`   | Medium/large scripts with reusable helpers         | Source OBB library via `OBB_PATH` or runtime discovery |
| `full-embedded` | Medium/large scripts requiring standalone delivery | Keep `variant=full` marker block at script end         |

If uncertain between full variants, prefer `full-source` during active development and `full-embedded` for portable distribution.

## 3. Copy Ready Template

Copy exactly one template:

```bash
cp skills/octivi-bash-boilerplate/assets/templates/<header-only-script|full-obb-script-source|full-obb-script-embedded> ./script.sh
```

Template payloads are generated from root OBB sources by release tooling:

```bash
scripts/generate-skill-templates
```

## 4. Implement Logic Outside Markers

- Keep all business logic outside OBB marker blocks.
- Keep functions focused and side effects explicit.
- Parse options deterministically (prefer `getopts`; document alternatives if needed).
- Validate required input early and return explicit exit codes.

## 5. Update OBB Marker Blocks

- Use:
  `octivi-bash-boilerplate-update ./script.sh`
- For `full-embedded`, ensure block is populated before delivery.
- Never manually edit generated OBB payload inside marker blocks.

## 6. Validate With Pass/Fail Gates

- Run `bash -n` on touched scripts.
- Run `shellcheck` where available.
- Apply all required checks from `references/checklist.md`.
- For refactors, verify backward compatibility unless change was requested.

## 7. Delivery Summary

Always report:

- Selected mode and why.
- Commands run and validation result.
- Compatibility impact.
- Residual risk and follow-up items.
