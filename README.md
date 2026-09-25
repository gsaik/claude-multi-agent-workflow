# code-quality

A Claude Code plugin that bundles code review, test generation, and auto-formatting into a single workflow — run it after any meaningful change and get actionable feedback without switching tools.

## Components

| Component | Type | Purpose |
|---|---|---|
| `reviewer` | Agent | Read-only; finds bugs, missing error handling, and unclear names |
| `test-writer` | Agent | Writes or updates tests to cover the changes |
| `check` | Command | Runs reviewer and test-writer in parallel, then summarises findings |
| `review-guide` | Skill | Loaded before review to set the standard for what counts as a finding |
| `fmt` | Hook | Runs ESLint `--fix` on every saved JS file |

## Install

```bash
claude --plugin-dir .
```

Or install from the marketplace:

```
/plugin marketplace add https://github.com/gsaik/claude-multi-agent-workflow
/plugin install code-quality@gsaik
```

## Usage

```
/code-quality:check          # run the full review + test workflow
```

The `reviewer` and `test-writer` agents run in parallel. Once both finish, a summary step collects their output and prints a prioritised action list.

## Reload after edits

```
/reload-plugins
```
