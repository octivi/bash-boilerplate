# Changelog

## [v1.1.0] - 2026-02-19

### Changed

- Rename updater command from `update-octivi-bash-boilerplate` to `octivi-bash-boilerplate-update` and align update/install paths for distributed artifacts ([`743c2c5`](https://github.com/octivi/bash-boilerplate/commit/743c2c5)) (Marcin Engelmann)
- Improve portability and runtime compatibility by keeping support for older Bash variants and removing dependency on external `sleep` in spinner timing ([`ea14437`](https://github.com/octivi/bash-boilerplate/commit/ea14437), [`debbaf1`](https://github.com/octivi/bash-boilerplate/commit/debbaf1), [`4a15d17`](https://github.com/octivi/bash-boilerplate/commit/4a15d17), [`b4f1fec`](https://github.com/octivi/bash-boilerplate/commit/b4f1fec)) (Marcin Engelmann)

### Added

- Add a minimalistic boilerplate variant for scripts that need only the core header block ([`39d80a8`](https://github.com/octivi/bash-boilerplate/commit/39d80a8)) (Marcin Engelmann)
- Add helpers to detect whether the script is sourced and whether the shell session is interactive ([#3](https://github.com/octivi/bash-boilerplate/issues/3)) ([`08cb93b`](https://github.com/octivi/bash-boilerplate/commit/08cb93b), [`e56dade`](https://github.com/octivi/bash-boilerplate/commit/e56dade)) (Marcin Engelmann)
- Add spinner support with multiple styles and associative lookup for spinner definitions ([#4](https://github.com/octivi/bash-boilerplate/issues/4)) ([`c4feeb2`](https://github.com/octivi/bash-boilerplate/commit/c4feeb2), [`3a8793f`](https://github.com/octivi/bash-boilerplate/commit/3a8793f), [`afe1523`](https://github.com/octivi/bash-boilerplate/commit/afe1523)) (Marcin Engelmann)
- Add an option to execute scripts directly by calling `main()` and add updater support for embedded (copy-pasted) OBB blocks ([`6c4e9a6`](https://github.com/octivi/bash-boilerplate/commit/6c4e9a6), [`b279b7e`](https://github.com/octivi/bash-boilerplate/commit/b279b7e)) (Marcin Engelmann)
- Add startup Bash version validation and fail early when running below Bash 4.4 ([`b60b1ac`](https://github.com/octivi/bash-boilerplate/commit/b60b1ac)) (Marcin Engelmann)

### Fixed

- Log `ERROR` in `die()` only when the exit code is non-zero ([`6473cd9`](https://github.com/octivi/bash-boilerplate/commit/6473cd9)) (Marcin Engelmann)
- Silence TTY errors in `spin()` when running without an attached TTY ([`1c40146`](https://github.com/octivi/bash-boilerplate/commit/1c40146)) (Marcin Engelmann)
- Fix executable permission on `octivi-bash-boilerplate-update` so the updater can run directly after installation ([`afbb03d`](https://github.com/octivi/bash-boilerplate/commit/afbb03d)) (Marcin Engelmann)

## [v1.0.0] - 2025-12-16

### Added

- Publish the first public release of Octivi Bash Boilerplate ([`7813171`](https://github.com/octivi/bash-boilerplate/commit/7813171), [`8e830c5`](https://github.com/octivi/bash-boilerplate/commit/8e830c5)) (Marcin Engelmann)

[v1.1.0]: https://github.com/octivi/bash-boilerplate/releases/tag/v1.1.0
[v1.0.0]: https://github.com/octivi/bash-boilerplate/releases/tag/v1.0.0
