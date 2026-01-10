# TT - Tmux Tool

<p align="center">
  <img src="tt.png" alt="TT TUI" />
</p>

**TT** is a small(ish), whiptail-driven helper for managing tmux sessions without having to remember tmux commands.

It is intentionally, safe, and dependency-light, with careful handling around dialogs and return codes to avoid common `set -e` / whiptail pitfalls.

## Features
- Create, attach/switch, rename, and destroy tmux sessions
- View session, window, and pane information
- Kill the tmux server (with confirmation)
- Works whether you are inside or outside tmux
- Optional shortcut install (`tt` or fallback name)
- Linux-first (Debian/Ubuntu, Arch, Fedora, Alpine supported)

## Requirements
- `bash`
- `tmux`
- `whiptail` (on Alpine, provided by the `newt` package)

## Install
Clone or copy the script somewhere, then make it executable:

```bash
chmod +x tt
```

Run it:

```bash
./tt
```

### Install dependencies

Debian/Ubuntu:
```bash
sudo apt update
sudo apt install -y tmux whiptail
```

Arch:
```bash
sudo pacman -S tmux libnewt
```

Fedora:
```bash
sudo dnf install -y tmux newt
```

Alpine:
```bash
sudo apk add tmux newt
```

## Usage notes
- Menus use Select and Exit buttons.
- All confirmation prompts default to no.
- If you are already inside tmux, TT will offer tmux-safe actions (such as switching sessions) rather than nesting.
- Dialog handling is defensive and designed to behave correctly under `set -e`.

## Optional shortcut install
TT can install a shortcut into `/usr/local/bin` from the menu.

- It will prefer the name `tt` if available.
- If a command already exists, a safe fallback name is used.
- Existing non-symlink files are never overwritten.

## Configuration
None.

TT does not use config files, environment variables, or persistent state. All behaviour is interactive and runtime-only.

## License
Licensed under the GPLv3 or later.
