# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this directory is

This is `~/.claude/agents/` — the user-level custom agents directory for Claude Code. Each `.md` file here defines a subagent that Claude Code can spawn via the `Agent` tool.

## Agent file format

Each agent is a single Markdown file with a YAML frontmatter block followed by the system prompt body:

```markdown
---
name: agent-slug          # kebab-case identifier used in Agent tool calls
description: "..."        # when to invoke this agent — this text is read by the orchestrator
model: sonnet             # model tier: sonnet | opus | haiku
color: red                # display color in the UI
memory: project           # memory scope: project | user | none
---

System prompt content here...
```

### Frontmatter fields

| Field | Required | Notes |
|---|---|---|
| `name` | Yes | Lowercase kebab-case; must be unique across all agent files |
| `description` | Yes | The orchestrating Claude reads this to decide when to invoke; write it as a trigger condition |
| `model` | No | Defaults to the session model if omitted |
| `color` | No | Visual indicator in the UI |
| `memory` | No | What memory scope the agent has access to |

## Agents in this directory

- **devils-advocate** (`devils-advocate.md`) — Critical scrutiny agent. Pressure-tests ideas, surfaces blind spots, applies pre-mortem reasoning. Invoked when a user presents an optimistic proposal that would benefit from challenge.
- **optimist-maximalist** (`optimist-maximalist.md`) — Best-case extrapolation agent. Traces the most favorable realistic trajectory for any idea, naming what must be true for it to materialize. Deliberately one-sided toward upside.
- **neutral-analyst** (`neutral-analyst.md`) — Evidence-based assessment agent. Separates facts from assumptions, maps genuine trade-offs, and calibrates confidence without advocacy in either direction. Invoked when an unbiased, grounded read is needed.

These three agents are designed as complementary council members: one challenges, one champions, one renders a clear-eyed verdict.

## Adding a new agent

Create a new `.md` file in this directory. The `description` field is the most important part — it determines when the orchestrator will automatically invoke the agent. Write it as a clear trigger condition (see existing files for examples).

## Testing an agent

In a Claude Code session, reference the agent by name in a prompt or describe a scenario that matches its `description`. The orchestrating Claude will invoke it via the `Agent` tool. You can also explicitly request it: "Use the devils-advocate agent on this plan."
