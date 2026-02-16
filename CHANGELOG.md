# Changelog

## [Unreleased]

### Changed

- Reduce dependency on external tools by replacing `sleep` with Bash `read -t`
  in spinner timing
  ([`b4f1fec`](https://github.com/octivi/bash-boilerplate/commit/b4f1fec))
- Improve Bash compatibility by reusing internal version checks and keeping
  behavior compatible with Bash 3.x
  ([`4a15d17`](https://github.com/octivi/bash-boilerplate/commit/4a15d17),
  [`ea14437`](https://github.com/octivi/bash-boilerplate/commit/ea14437))
- Expand and clarify project documentation (installation, testing, badges,
  security policy examples)
  ([`4dcffe4`](https://github.com/octivi/bash-boilerplate/commit/4dcffe4),
  [`ab91562`](https://github.com/octivi/bash-boilerplate/commit/ab91562),
  [`c14ba42`](https://github.com/octivi/bash-boilerplate/commit/c14ba42))

### Added

- Add minimalistic boilerplate variant via `octivi-bash-boilerplate-header`
  ([`39d80a8`](https://github.com/octivi/bash-boilerplate/commit/39d80a8))
- Add spinner support with multiple spinner styles
  ([`c4feeb2`](https://github.com/octivi/bash-boilerplate/commit/c4feeb2))
- Add helper functions to detect sourced execution and interactive mode
  ([`08cb93b`](https://github.com/octivi/bash-boilerplate/commit/08cb93b),
  [`e56dade`](https://github.com/octivi/bash-boilerplate/commit/e56dade))
- Add direct-execution option that runs `main()`
  ([`6c4e9a6`](https://github.com/octivi/bash-boilerplate/commit/6c4e9a6))
- Add updater support for projects where OBB was copy-pasted instead of sourced
  ([`b279b7e`](https://github.com/octivi/bash-boilerplate/commit/b279b7e))
- Add test coverage for minimum supported Bash version (4.4)
  ([`b60b1ac`](https://github.com/octivi/bash-boilerplate/commit/b60b1ac))

### Removed

- No user-facing removals.

### Fixed

- Prevent noisy TTY errors in `spin()` when running without a TTY
  ([`1c40146`](https://github.com/octivi/bash-boilerplate/commit/1c40146))
- Make `die()` log `ERROR` only for non-zero exit codes
  ([`6473cd9`](https://github.com/octivi/bash-boilerplate/commit/6473cd9))
- Correct release badge link in README
  ([`65df25c`](https://github.com/octivi/bash-boilerplate/commit/65df25c))

## [1.0.0] - 2025-12-16

### Changed

- Adopt SPDX-style copyright, contributor, and license headers
  ([`24cfa22`](https://github.com/octivi/bash-boilerplate/commit/24cfa22))
- Improve wording and documentation quality across the project
  ([`785e9eb`](https://github.com/octivi/bash-boilerplate/commit/785e9eb),
  [`e668479`](https://github.com/octivi/bash-boilerplate/commit/e668479))

### Added

- Publish first public version of Octivi Bash Boilerplate
  ([`8e830c5`](https://github.com/octivi/bash-boilerplate/commit/8e830c5))
- Add release and CI workflows (release automation, tests on PRs, yearly header
  maintenance)
  ([`f61a89d`](https://github.com/octivi/bash-boilerplate/commit/f61a89d),
  [`c073926`](https://github.com/octivi/bash-boilerplate/commit/c073926),
  [`269ca2c`](https://github.com/octivi/bash-boilerplate/commit/269ca2c),
  [`49aed9e`](https://github.com/octivi/bash-boilerplate/commit/49aed9e))
- Add references to related Bash resources (Awesome Bash and formatting tips)
  ([`c40cba2`](https://github.com/octivi/bash-boilerplate/commit/c40cba2),
  [`71e18a8`](https://github.com/octivi/bash-boilerplate/commit/71e18a8))

### Removed

- No user-facing removals.

### Fixed

- Stabilize CI for pull requests and release pipeline prerequisites
  ([`269ca2c`](https://github.com/octivi/bash-boilerplate/commit/269ca2c),
  [`e889ef2`](https://github.com/octivi/bash-boilerplate/commit/e889ef2))

<!-- Reference links (recommended) -->

[Unreleased]: https://github.com/octivi/bash-boilerplate/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/octivi/bash-boilerplate/releases/tag/v1.0.0
