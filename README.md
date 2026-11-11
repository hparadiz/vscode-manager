# vscode-manager

Small shell scripts for managing a downloaded stable Linux x64 installation of
Visual Studio Code.

## Files

- `update-code.sh` downloads and extracts the stable build, creates a `current`
  symlink, and links `code.desktop` into `~/.local/share/applications/`.
- `link-global.sh` creates `/usr/bin/code` pointing to `current/bin/code` in this
  checkout. It requires permission to write to `/usr/bin`.
- `code.desktop` provides an application launcher and actions for comparing files
  or opening an existing window.
- `disable-sync-activity-bar.css` is an optional custom CSS snippet that hides the
  Accounts activity bar item. The scripts do not install or apply it.

## Usage

Requires Bash, curl, tar, and standard GNU command-line utilities. Run from the
checkout root:

```sh
./update-code.sh
```

The updater creates `current` with `ln -s`; it does not replace an existing
`current` symlink. Review and update that link when changing the selected version.
Ensure `~/.local/share/applications/` exists before running the updater.

The desktop entry expects `/usr/bin/code` and uses a local icon path. Adjust the
entry for your installation before registering it. Review `link-global.sh` before
running it with administrative permissions; it also expects the checkout root as
the working directory and does not replace an existing `/usr/bin/code`.

Downloaded VS Code distributions, archives, and the local `current` link are
excluded from version control.
