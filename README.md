# DevTools Cheat Sheet

A single-page reference for a terminal-centric development environment built around Zsh, Tmux, and Neovim.

**Live site:** [https://richtxteditor.github.io/devtools](https://richtxteditor.github.io/devtools)

## What's covered

- ![Zsh](https://img.shields.io/badge/Zsh-000?logo=zsh&logoColor=white) Shell and navigation (zoxide, eza, bat, fzf)
- ![macOS](https://img.shields.io/badge/macOS-000?logo=apple&logoColor=white) System and config management
- ![Git](https://img.shields.io/badge/Git-000?logo=git&logoColor=F05032) Git workflow and aliases
- ![tmux](https://img.shields.io/badge/tmux-000?logo=tmux&logoColor=1BB91F) Tmux multiplexer keybindings
- ![Neovim](https://img.shields.io/badge/Neovim-000?logo=neovim&logoColor=57A143) Neovim editor shortcuts (files, LSP, diagnostics)
- ![Testing](https://img.shields.io/badge/Testing-000?logo=vitest&logoColor=6E9F18) Testing, debugging, and task running
- ![Runtimes](https://img.shields.io/badge/Runtimes-000?logo=nodedotjs&logoColor=5FA04E) Runtime and language setup (Node, Python, Ruby, Lua, Shell, JSON/YAML, HTML/CSS/Tailwind, Django, SQL, C/C++, TypeScript)
- ![DevDocs](https://img.shields.io/badge/DevDocs-000?logo=readthedocs&logoColor=8CA1AF) DevDocs offline documentation and current-file doc lookup
- ![direnv](https://img.shields.io/badge/direnv-000?logo=gnu-bash&logoColor=white) Project-local environments and `.venv` auto-loading

## direnv quick start

`direnv` does not activate a virtualenv just because a `.venv` directory exists. Add an `.envrc` file in the project root and approve it once:

```sh
printf '%s\n' 'source .venv/bin/activate' > .envrc
direnv allow
```

For Django or other framework projects, extend `.envrc` with any required environment variables, such as `DJANGO_SETTINGS_MODULE`.

## Built with

Plain HTML, CSS, and JavaScript. No frameworks or build tools. Hosted on GitHub Pages.

## Related

This cheat sheet documents the setup from [dotfiles](https://github.com/richtxteditor/dotfiles).

## Source-backed maintenance workflow

The page is still a static GitHub Pages site, but keybind rows now have a metadata layer in `data/keybinds.js`.
Each entry is tagged with:

- `type`: shortcut, command, alias, function, or setup-note
- `origin`: dotfiles-custom, plugin-default, app-default, or manual-note
- `platform`: all, macos, linux, or macos/linux
- `mode`: normal, insert/select, command-line, typed-command, interactive-shell, tmux, etc.
- `source`: the dotfiles path/line range or upstream default/docs reference
- `confidence`: high/medium/low

Run the audit after changing dotfiles or before publishing the cheat sheet:

```sh
python3 scripts/audit-dotfiles-keybinds.py
python3 scripts/audit-dotfiles-keybinds.py --json
```

The audit compares obvious mappings, Ghostty keybinds, tmux binds, zsh aliases, and shell functions from `/Users/what/Sites/dotfiles` against the online cheat-sheet metadata. Review any “possible missing signals” and either add them to `data/keybinds.js` or intentionally leave them out if they are noisy/internal.
