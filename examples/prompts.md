# Invocation Examples

These are ordinary prompts. They do not add a native `@` mention or slash command.

## Architecture

> Use `advisor` to compare the long-term maintenance and consistency trade-offs of these designs before implementation.

## Repository investigation

> Ask `code_mapper` to trace this request from the API entry point through persistence. Then ask `reviewer` to check the proposed change for regressions. Keep both tasks read-only.

## Documentation research

> Use `docs_researcher` to verify this API option against the official documentation for the version used by this project. Include direct source links.

## Frontend issue

> Have `browser_debugger` reproduce this UI bug and report the exact steps and console evidence. If the cause is clear, delegate the smallest fix to `ui_fixer`.

## Main agent only

> Do this on the main thread only. Do not use subagents.
