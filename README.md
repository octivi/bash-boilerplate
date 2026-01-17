# Octivi Bash Boilerplate (OBB)

[![license](https://img.shields.io/github/license/octivi/bash-boilerplate)](https://choosealicense.com/licenses/mit/)

> If you are writing a script that is more than 100 lines long, or that uses non-straightforward control flow logic, you
> should rewrite it in a more structured language now. --
> [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html)

## Octivi Bash Boilerplate (OBB)

Octivi Bash Boilerplate (OBB) is a lightweight starting point for Bash scripts that promotes consistent structure and
safe defaults. With ready-to-use helpers and auto-generated documentation, it helps you ship maintainable CLI utilities
faster and with fewer surprises.

## Octivi Bash Boilerplate (OBB) Header

Octivi Bash Boilerplate (OBB) Header is minimalistic version of the bash boilerplate to be used in scripts.
Just copy and paste this code at the beginning of your bash script files.

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

## Install

### Manual

Just download

```
# or https://github.com/octivi/bash-boilerplate/releases/latest/download/octivi-bash-boilerplate if you want always latest release
sudo curl -fL -o /usr/local/share/octivi-bash-boilerplate https://github.com/octivi/bash-boilerplate/releases/download/v1.0.0/octivi-bash-boilerplate
```

### Ansible

One simple task to install `octivi-bash-boilerplate`

```
- name: 'Install Octivi Bash Boilerplate (OBB)'
  ansible.builtin.get_url:
    # or https://github.com/octivi/bash-boilerplate/releases/latest/download/octivi-bash-boilerplate if you want always latest release
    url: 'https://github.com/octivi/bash-boilerplate/releases/download/v1.0.0/octivi-bash-boilerplate'
    dest: '/usr/local/share/bash-boilerplate'
    owner: 'root'
    group: 'root'
    mode: '0644'
    # or https://github.com/octivi/bash-boilerplate/releases/latest/download/octivi-bash-boilerplate.sha256 if you want always latest release
    checksum: 'sha256:https://github.com/octivi/bash-boilerplate/releases/download/v1.0.0/octivi-bash-boilerplate.sha256'
  register: '__bash_boilerplate_download'
  until: __bash_boilerplate_download is succeeded
  retries: 5
  delay: 2
```

## Projects that use Octivi Bash Boilerplate

- [BorgBackup Wrapper](https://github.com/octivi/borg-backup-wrapper) - a wrapper around the deduplicating archiver
  [BorgBackup](https://www.borgbackup.org/) that streamlines everyday tasks across multiple repositories.

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
