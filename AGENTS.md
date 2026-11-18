# Global Codex Agent Routing

## Default delegation

- Consider whether a specialized subagent can add meaningful value to each request.
- Delegate relevant work by default; keep trivial tasks on the main agent.
- The main agent coordinates work, resolves conflicting findings, and owns implementation decisions and the final result.
- Avoid duplicate investigations and unnecessary token use.

## User direction

- Follow explicit requests to use or avoid subagents.
- If the user names agents or gives an order, follow that selection and order.
- Never claim an agent was invoked unless it actually ran.
- If an agent is unavailable, report that limitation instead of simulating its work.

## Agent selection

| Agent | Responsibility |
|---|---|
| `advisor` | Architecture, design decisions, consultation, and trade-offs |
| `pr_explorer` | Repository investigation, pull-request analysis, and execution paths |
| `reviewer` | Correctness, security, performance, and regression review |
| `docs_researcher` | Official documentation, APIs, compatibility, and technical research |
| `code_mapper` | Code paths, dependencies, execution flows, and component relationships |
| `browser_debugger` | Browser debugging, UI reproduction, and frontend investigation |
| `ui_fixer` | Focused frontend implementation and validation |
| `explorer` | General read-only exploration |
| `worker` | General implementation and delegated coding |

## Execution rules

- Prefer parallel work for independent, read-only investigations.
- Respect dependencies and avoid concurrent edits to overlapping files.
- Keep read-only agents read-only; their instructions do not provide OS-level isolation.
- Respect configured concurrency, sandbox, approval, Git, and repository policies.
- Never assign Astra models to custom agents. Preserve existing model assignments and use a confirmed non-Astra default when none is configured.

## Suggested workflows

- **Architecture:** consult `advisor` when material design trade-offs exist.
- **Repository investigation:** use `pr_explorer` or `code_mapper` for focused traces.
- **Code review:** use `reviewer` for substantive changes.
- **Documentation:** use `docs_researcher` to verify current official sources.
- **Frontend:** use `browser_debugger` to reproduce issues and `ui_fixer` for a focused fix.
- **General implementation:** use the main agent or `worker`.

These are routing guidelines, not mandatory pipelines. Select only agents that add meaningful value.
