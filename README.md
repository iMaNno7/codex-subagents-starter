# Codex Specialist Subagents

A reusable global Codex setup with seven focused custom agents, sample settings, invocation examples, and a copy-ready setup prompt.

## Included agents

| Agent | Focus | Model | Reasoning |
|---|---|---|---|
| `advisor` | Architecture, technical decisions, and trade-offs | `gpt-6.1-sol` | `high` |
| `pr_explorer` | Read-only repository and pull-request investigation | `gpt-6-luna` | `xhigh` |
| `reviewer` | Read-only correctness, security, performance, and regression review | `gpt-6.1-sol` | `high` |
| `docs_researcher` | Official API and framework documentation | `gpt-6-luna` | `xhigh` |
| `code_mapper` | Read-only execution paths and dependencies | `gpt-6-luna` | `xhigh` |
| `browser_debugger` | Browser reproduction and frontend investigation | `gpt-6.1-sol` | `medium` |
| `ui_fixer` | Focused frontend implementation when delegated | `gpt-6-luna` | `xhigh` |

Codex's built-in `default`, `worker`, and `explorer` agents are not duplicated. No Astra model is assigned.

## Install

For guided installation, open [`SETUP_PROMPT.md`](SETUP_PROMPT.md), copy its prompt, and run it in Codex from this repository. The prompt instructs Codex to inspect the local schema, back up files before edits, create only missing agents, and merge settings without replacing existing configuration.

For manual installation, copy only missing agent files:

```sh
mkdir -p ~/.codex/agents
cp -n agents/*.toml ~/.codex/agents/
```

Merge the relevant settings from [`config.toml.example`](config.toml.example) into the existing `~/.codex/config.toml`; do not replace the file. Merge the routing guidance from [`AGENTS.md`](AGENTS.md) into `~/.codex/AGENTS.md`, preserving unrelated instructions. If a same-named agent already exists, inspect it and keep its custom instructions.

Codex custom agents are standalone TOML files under `~/.codex/agents/` for user-wide availability. The documented fields include `name`, `description`, and `developer_instructions`; model and reasoning can be set per agent. See the [official Codex subagents documentation](https://learn.chatgpt.com/docs/agent-configuration/subagents).

## Model availability

The included model assignments match the intended setup, but model access and supported reasoning levels can vary by Codex version and account. Verify them in the installed Codex model catalog before installation. The setup prompt requires a confirmed non-Astra fallback when a listed model is unavailable; it does not silently switch to Astra.

The read-only roles are constrained by their instructions, not by OS-level isolation. All agents inherit the parent session's permissions, provider, and MCP servers. Keep credentials and personal configuration in your own local files; this repository contains no live Codex configuration or credentials.

## Claude Code equivalent

Claude Code's closest equivalent is a custom subagent. Claude stores user-wide definitions as Markdown files with YAML frontmatter in `~/.claude/agents/`; project-specific definitions go in `.claude/agents/`. Claude uses each agent's description for automatic routing. Codex instead uses TOML files in `~/.codex/agents/` and relies on its agent descriptions plus the active session and global routing instructions. The formats and some permission behavior differ, so the files in this repository cannot be copied directly into Claude Code. See [Claude Code custom subagents](https://code.claude.com/docs/en/sub-agents).

## Use

Ask for an agent by name in a normal Codex prompt. Examples are in [`examples/prompts.md`](examples/prompts.md). These examples do not imply native `@` mention or slash-command support.

## License

MIT. See [`LICENSE`](LICENSE).
