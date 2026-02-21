# Octivi Bash Boilerplate (OBB)

[![GitHub Releases](https://img.shields.io/github/v/release/octivi/bash-boilerplate?sort=semver)](https://github.com/octivi/bash-boilerplate/releases)
[![License: MIT](https://img.shields.io/github/license/octivi/bash-boilerplate)](https://choosealicense.com/licenses/mit/)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org/)
[![Semantic Versioning](https://img.shields.io/badge/SemVer-2.0.0-blue)](https://semver.org/spec/v2.0.0.html)

> If you are writing a script that is more than 100 lines long, or that uses non-straightforward control flow logic, you
> should rewrite it in a more structured language now. --
> [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html)

## Octivi Bash Boilerplate (OBB)

Octivi Bash Boilerplate (OBB) is a lightweight starting point for Bash scripts that promotes consistent structure and
safe defaults. With ready-to-use helpers and auto-generated documentation, it helps you ship maintainable CLI utilities
faster and with fewer surprises.

## Octivi Bash Boilerplate (OBB) Header

Octivi Bash Boilerplate (OBB) Header is a minimalistic version of the Bash boilerplate for use in scripts.
Copy and paste this code at the beginning of your Bash script files.

## Key features

- Enforces [Unofficial Bash "Strict Mode"](http://redsymbol.net/articles/unofficial-bash-strict-mode/) to reduce
  hard-to-track runtime errors
- Enables verbose diagnostics through the `DEBUG` environment variable
- Honors the `NO_COLOR` ([disabling colors](https://no-color.org/)) and `FORCE_COLOR` environment variables and
  supports ANSI colors out of the box
- Exposes logging helpers for uniform, readable output
- Generates `-h` help text from inline comments, so documentation stays close to the code
- Handles option parsing through
  [POSIX getopts](https://stackoverflow.com/questions/192249/how-do-i-parse-command-line-arguments-in-bash/14203146#14203146)
  for predictable CLI behavior

## Requirements

- Bash 4.4 or newer

## Install

### AI agents skill

This repository is also available as a skill for AI agents.

Install it with:

```bash
npx skills add octivi/bash-boilerplate
```

### Manual

Download, verify checksums, and install all OBB files together:

```bash
# or use releases/latest/download/... URLs if you always want the latest release
curl -fsSLO https://github.com/octivi/bash-boilerplate/releases/download/v1.1.0/octivi-bash-boilerplate \
  && curl -fsSLO https://github.com/octivi/bash-boilerplate/releases/download/v1.1.0/octivi-bash-boilerplate-header \
  && curl -fsSLO https://github.com/octivi/bash-boilerplate/releases/download/v1.1.0/octivi-bash-boilerplate-update \
  && curl -fsSL https://github.com/octivi/bash-boilerplate/releases/download/v1.1.0/octivi-bash-boilerplate.sha256 \
  | sha256sum -c - \
  && curl -fsSL https://github.com/octivi/bash-boilerplate/releases/download/v1.1.0/octivi-bash-boilerplate-header.sha256 \
  | sha256sum -c - \
  && curl -fsSL https://github.com/octivi/bash-boilerplate/releases/download/v1.1.0/octivi-bash-boilerplate-update.sha256 \
  | sha256sum -c - \
  && sudo install -m 0644 octivi-bash-boilerplate /usr/local/share/octivi-bash-boilerplate \
  && sudo install -m 0644 octivi-bash-boilerplate-header /usr/local/share/octivi-bash-boilerplate-header \
  && sudo install -m 0755 octivi-bash-boilerplate-update /usr/local/share/octivi-bash-boilerplate-update \
  || { echo "Checksum verification failed; aborting installation." >&2; exit 1; }
```

### Ansible

Install all OBB files with checksum verification:

```yaml
- name: "Install Octivi Bash Boilerplate files"
  ansible.builtin.get_url:
    # or use releases/latest/download/... URLs if you always want the latest release
    url: "https://github.com/octivi/bash-boilerplate/releases/download/v1.1.0/{{ item.name }}"
    dest: "/usr/local/share/{{ item.name }}"
    owner: "root"
    group: "root"
    mode: "{{ item.mode }}"
    checksum: "sha256:https://github.com/octivi/bash-boilerplate/releases/download/v1.1.0/{{ item.name }}.sha256"
  loop:
    - { name: "octivi-bash-boilerplate", mode: "0644" }
    - { name: "octivi-bash-boilerplate-header", mode: "0644" }
    - { name: "octivi-bash-boilerplate-update", mode: "0755" }
  register: "__obb_download"
  until: __obb_download is succeeded
  retries: 5
  delay: 2
```

## Quick start: use OBB in scripts (with markers)

The easiest workflow is to keep OBB in a marked block and let
`octivi-bash-boilerplate-update` inject/update the content for you.

### Header variant (minimal)

Use this when you only need strict mode and base constants.

```bash
#!/usr/bin/env bash

# >>> OBB:BEGIN variant=header
# <<< OBB:END

main() {
  echo "Hello from header mode"
}

main "$@"
```

Then update the marked block:

```bash
/usr/local/share/octivi-bash-boilerplate-update ./your-script
```

### Full variant (helpers + logging + checks)

Use this when you want OBB helper functions like `print`, `error`, `die`, `require_command`, etc.

Important: place the full OBB marker block at the end of the script and keep your own logic above it.

```bash
#!/usr/bin/env bash
#/ Usage: your-script [OPTIONS]
#/ Example:
#/   your-script --help

main() {
  print "Hello from full mode"
}

# >>> OBB:BEGIN variant=full
# <<< OBB:END
```

Then update the marked block:

```bash
/usr/local/share/octivi-bash-boilerplate-update ./your-script
```

To pin the inserted block to a specific release:

```bash
/usr/local/share/octivi-bash-boilerplate-update -u 1.1.1 ./your-script
```

## Update inlined OBB blocks

Use `octivi-bash-boilerplate-update` to update scripts where OBB was copy-pasted (not sourced).

```bash
/usr/local/share/octivi-bash-boilerplate-update ./script-a ./script-b
/usr/local/share/octivi-bash-boilerplate-update -u 1.1.1 ./script-a
/usr/local/share/octivi-bash-boilerplate-update --variant header ./script-a ./script-b
```

`--variant` accepts `full` or `header`. Without `--variant`, each marked block must define
`variant=full|header` in its `# >>> OBB:BEGIN ...` marker.

When `-u/--use` is set, the script downloads release assets and verifies their `.sha256` checksums before updating any
target files.

If a target file has no OBB markers, it is skipped with a warning.

The updater writes explicit markers around embedded blocks:

```bash
# >>> OBB:BEGIN variant=full source=github version=v1.1.1
...
# <<< OBB:END
```

## Projects that use Octivi Bash Boilerplate

- [BorgBackup Wrapper](https://github.com/octivi/borg-backup-wrapper) - a wrapper around the deduplicating archiver
  [BorgBackup](https://www.borgbackup.org/) that streamlines everyday tasks across multiple repositories.

## How to test on a specific Bash version

The easiest way is to use Docker, for example to test Bash 3.2:

```bash
docker run -it --rm -v "$PWD":/work -w /work bash:3.2 bash
```

## Other resources

[Awesome Bash - A curated list of delightful Bash scripts and resources](https://github.com/awesome-lists/awesome-bash)

### Style guides

- [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html)
- [Bash FAQ](https://mywiki.wooledge.org/BashFAQ)
- [Pure Bash Bible](https://github.com/dylanaraps/pure-bash-bible)
- [Unix shell script tactics — best practices style guide](https://github.com/SixArm/unix-shell-script-tactics)
- [Shell Scripts Matter](https://dev.to/thiht/shell-scripts-matter)
- [Bash tips: Colors and formatting](https://misc.flogisoft.com/bash/tip_colors_and_formatting)

### Boilerplates

- [BASH3 Boilerplate (b3bp)](https://bash3boilerplate.sh/)
- <https://github.com/xwmx/bash-boilerplate>
- <https://github.com/oxyc/bash-boilerplate>
- <https://github.com/ralish/bash-script-template>
- <https://github.com/andrei-pavel/bash-boilerplate>

### Tools

- [ShellCheck](https://www.shellcheck.net/)
- [Shellharden](https://github.com/anordal/shellharden)

## License

All content is provided under the terms of [The MIT License](LICENSE).
