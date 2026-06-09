# CLAUDE.md — Global User Instructions

This file provides guidance to Claude Code (claude.ai/code) across all sessions and projects.

## Council Discuss Protocol

**Trigger:** any message containing the phrase "council discuss" followed by an idea or proposal.

When triggered, execute the following workflow without waiting for further instruction:

### Step 1 — Discover agents (auto-scaling)
Glob `~/.claude/agents/*.md` and exclude `CLAUDE.md`. The resulting list is the active council. Any new `.md` file added to that directory automatically becomes a council member — no configuration needed.

### Step 2 — Run agents in parallel
Launch all discovered agents simultaneously. Pass each agent:
- The full proposal text
- An explicit instruction to document their step-by-step reasoning before delivering their final output
- A reminder to stay strictly within their defined perspective (as declared in their own frontmatter/system prompt)

### Step 3 — Write `shared_reasoning.md`
After all agents complete, write (or overwrite) `shared_reasoning.md` in the current working directory. Structure:

```
# Council Discussion: <one-line proposal summary>
Date: <today>

## <Agent Name> — Reasoning Chain
<step-by-step reasoning the agent documented>

## <Agent Name> — Reasoning Chain
<step-by-step reasoning the agent documented>
```

### Step 4 — Present balanced report
Output a final structured report with one clearly labeled section per agent. Enforce perspective discipline: the optimist delivers only the upside case, the devil's advocate delivers only the risk analysis. No agent may comment outside their lane.

Use this report structure:

```
# Council Report: <proposal>

## [Agent Name] ([their role])
<their output>

---

## [Agent Name] ([their role])
<their output>

---
```

### Step 5 — Council Consensus
After all agent sections, append a Council Consensus block using exactly this template:

```
## Council Consensus
---
Agent: Optimist
Recommendation: [1-2 sentence high-level summary of their stance]

Agent: Devil's Advocate
Recommendation: [1-2 sentence high-level summary of their stance]

Agent: Neutral Analyst
Recommendation: [1-2 sentence high-level summary of their stance]

The convergence point: [1 sentence stating what all agents agree on]

1. [Actionable step 1] - [Brief detail]
2. [Actionable step 2] - [Brief detail]
3. [Actionable step 3] - [Brief detail]
4. [Actionable step 4] - [Brief detail]

Alternative pivot suggested by [Agent Name]: [1-2 sentences explaining a lower-risk or alternate path surfaced during the discussion].
---
```
