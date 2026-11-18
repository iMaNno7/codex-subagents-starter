# Global Setup Prompt

Copy the prompt below into Codex from the root of this repository.

```text
Set up the custom Codex agents in this repository as global agents for this user.

Before changing anything:
1. Read the official Codex subagents documentation: https://learn.chatgpt.com/docs/agent-configuration/subagents
2. Inspect the installed Codex version and local configuration schema. Confirm the supported global agent paths, TOML fields, model identifiers, and reasoning-effort values. Do not guess.
3. Inspect ~/.codex/config.toml, ~/.codex/AGENTS.md, and every existing file in ~/.codex/agents/ before editing.
4. Create a timestamped backup of each existing global file that you will modify. Preserve the original content and permissions where possible.

Preservation requirements:
- Make only the global Codex changes required to install these agents and their routing guidance.
- Do not modify project files, Git branches, commits, or remote repositories.
- Do not delete, replace, reset, or rewrite existing configuration.
- Do not change the main agent's model, permissions, sandbox, approval policy, or other session defaults.
- Do not modify existing Skills, MCP servers, plugins, hooks, or unrelated agent settings.
- Do not add or configure an MCP server. The docs_researcher must use documentation tools already available or other official sources.
- Create only missing files under ~/.codex/agents/. If a same-named agent already exists, leave it untouched and report the difference; never overwrite its custom instructions.
- Merge configuration keys into ~/.codex/config.toml without replacing the file or existing tables. Preserve all unrelated values.
- Add the routing section from this repository's AGENTS.md to ~/.codex/AGENTS.md only if the equivalent section is missing. Preserve every unrelated instruction.

Agent/model requirements:
- Install the seven agent definitions from agents/: advisor, pr_explorer, reviewer, docs_researcher, code_mapper, browser_debugger, and ui_fixer.
- Preserve each agent's model and reasoning assignment when the installed Codex version and account support it:
  - advisor: gpt-6.1-sol, high
  - pr_explorer: gpt-6-luna, xhigh
  - reviewer: gpt-6.1-sol, high
  - docs_researcher: gpt-6-luna, xhigh
  - code_mapper: gpt-6-luna, xhigh
  - browser_debugger: gpt-6.1-sol, medium
  - ui_fixer: gpt-6-luna, xhigh
- Never use an Astra model. Verify model and reasoning support locally. If a listed model is unavailable, use another confirmed non-Astra model with a compatible reasoning level; if no compatible model is confirmed, stop before changing that assignment and report the limitation.
- Merge the supported values from config.toml.example into the existing [agents] table: enable agents and set the concurrency limit to 6. Use gpt-6.1-sol with medium reasoning as the default only if both are confirmed supported. Otherwise use a verified non-Astra model and compatible effort; if none is confirmed, preserve the existing default and report the limitation. Do not add undocumented settings.
- Do not duplicate or replace Codex built-in agents such as default, worker, and explorer.

Validation:
1. Parse/validate every installed agent TOML and the resulting config.toml with the installed Codex schema.
2. Confirm the seven custom agent names are discoverable and the built-in agents remain available.
3. Confirm no custom agent or default subagent model is Astra and report any unavailable model or unsupported reasoning level.
4. Run safe, read-only invocation checks for advisor, reviewer, and code_mapper if the installed Codex client supports them.
5. Report the backup location, exact files changed, validation performed, and whether a new session or Desktop restart is needed.

Do not claim a check passed unless you performed it. If a required change could overwrite or break existing configuration, stop before that change and report the specific conflict.
```
