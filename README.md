# Cralph

This project is inspired by and adapted from the original "Ralph" workflow in
`ralph-claude-code`. Full credit and thanks to the original work:
https://github.com/frankbria/ralph-claude-code


Shell tools to run the "Cralph" autonomous Codex loop, plus helpers to set up
new projects, import PRDs, and monitor progress.

## Requirements

- Codex CLI (`codex`) in your PATH
- `jq`
- `git`
- `tmux` (optional, for `--monitor` mode)

## Install

```bash
./install.sh
```

If `~/.local/bin` is not in your PATH, add it to your shell profile:

```bash
export PATH="$HOME/.local/bin:$PATH"
```

## Quick Start

Create a new Cralph project:

```bash
cralph-setup my-project
cd my-project
```

Edit `PROMPT.md` and `@fix_plan.md`, then run the loop:

```bash
cralph --monitor
```

If you prefer without tmux:

```bash
cralph
```

## Common Options

You can combine these flags based on how you want to run the loop:

- `--monitor`        Start a tmux session with the live dashboard
- `--show-output`    Stream Codex output to the terminal in real time
- `--verbose`        Log detailed progress updates while Codex runs
- `--timeout MIN`    Set Codex execution timeout (1-120 minutes)
- `--calls NUM`      Set max Codex calls per hour
- `--cmd CMD`        Override the Codex command

Example with output streaming:

```bash
cralph --show-output
```

Example with monitoring and output streaming:

```bash
cralph --monitor --show-output
```

## Import a PRD

Convert an existing spec into a Cralph project:

```bash
cralph-import path/to/requirements.md my-project
```

This generates:
- `PROMPT.md`
- `@fix_plan.md`
- `specs/requirements.md`

## Monitor

If you are not using `--monitor`, you can run:

```bash
cralph-monitor
```

## Uninstall

```bash
./install.sh uninstall
```


