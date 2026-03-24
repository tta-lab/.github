# tta-lab

Open-source toolkit for AI agent operations. Not another code agent — the infrastructure that makes all code agents better.

## What We Build

We build composable, Unix-style tools that give AI agents autonomy: task routing, worker lifecycle, code intelligence, sandboxing, and inter-agent communication. One binary at a time, no cloud required.

### Core

| Repo | What it does |
|------|-------------|
| [**ttal-cli**](https://github.com/tta-lab/ttal-cli) | Agent ops CLI. Route tasks, spawn workers, ship PRs. The orchestration layer. |
| [**logos**](https://github.com/tta-lab/logos) | Bash-only reasoning engine. LLMs think in plain text, act with shell commands. No tool call overhead. |
| [**organon**](https://github.com/tta-lab/organon) | Structure-aware tools for agents. Tree-sitter code editing, web navigation, search. Stdin in, stdout out. |
| [**temenos**](https://github.com/tta-lab/temenos) | Filesystem sandboxing for agents. seatbelt (macOS) + bubblewrap (Linux). |
| [**agora**](https://github.com/tta-lab/agora) | Matrix protocol TUI for human-agent conversations. Charm-powered, markdown-rendered, task-aware. Potentially the best Matrix TUI out there. |

### Support

| Repo | What it does |
|------|-------------|
| [**diary**](https://github.com/tta-lab/diary) | Append-only diary CLI for agents and humans. Per-agent journals, daily entries. |

## Architecture

```
┌─────────────────────────────────────────────┐
│              Manager Plane                  │
│  Long-running agents: orchestrate, research,│
│  design. Persist across sessions.           │
├─────────────────────────────────────────────┤
│              ttal-cli                       │
│  Route tasks → spawn workers → ship PRs     │
│  One binary, composable commands, no cloud   │
├─────────────────────────────────────────────┤
│              Worker Plane                   │
│  Short-lived coders in git worktrees.       │
│  Implement → review → merge → disappear.    │
├──────────┬──────────┬────────────┬──────────┤
│  logos   │ organon  │  temenos   │  agora   │
│ reasoning│  tools   │  sandbox   │   chat   │
└──────────┴──────────┴────────────┴──────────┘
```

## Philosophy

- **Runtime agnostic** — ttal works with Claude Code, Codex, kit, or any agent runtime. It's the handle, not the blade.
- **Unix philosophy** — small tools that compose. Text as interface. Pipes over APIs.
- **Convention over configuration** — opinionated defaults for branch naming, PR workflow, task lifecycle, so agents don't have to decide.
- **Local-first, cloud-ready** — ttal works fully offline with taskwarrior and markdown plans. For teams that want more, we recommend [FlickNote](https://flicknote.app/) and [FlickTask](https://flicknote.app/) — LLM-powered knowledge capture with auto-categorization, tree-structured task management with subtasks, and cloud sync. When tasks have subtrees, agents can spawn workers to handle individual branches independently.

## Install

```bash
brew tap tta-lab/ttal
brew install ttal
```

## License

MIT
