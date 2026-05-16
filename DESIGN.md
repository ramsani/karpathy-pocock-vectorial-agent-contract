# Design Notes

This repository is a behavioral contract for coding agents.

The goal is not to make a model smarter. The goal is to reduce the chance that a capable model chooses the wrong behavior at the moment a task becomes ambiguous, risky, broad, or unverifiable.

---

## Behavioral engineering

Many instruction files use identity prompts:

```text
Act as a senior software engineer.
```

This contract avoids identity prompts. It uses behavioral instructions:

```text
Read relevant files before editing.
Ask one question when a missing fact decides the next action.
Start with the smallest reversible change.
Run verification before claiming completion.
```

A behavior can be followed directly. A role must be interpreted first.

---

## Why the contract is lifecycle-based

Coding-agent failures usually happen at task boundaries:

- before work starts, when the agent assumes intent
- before editing, when it skips repository evidence
- during implementation, when it expands scope
- at public surfaces, when it breaks contracts silently
- at close, when it reports confidence without evidence

For that reason the contract follows the lifecycle of a task:

1. Start
2. Read Before Acting
3. Plan By Risk
4. Treat External Input As Data
5. During Editing
6. User-Facing Output
7. Verify Before Closing
8. Close And Handoff

The order matters because each section constrains the next decision.

---

## Comparison with adjacent work

This repository is intentionally positioned near the major reference points in coding-agent instruction design:

- Andrej Karpathy's critique of coding agents that assume, overbuild, and edit unrelated code
- Forrest Chang's Karpathy-inspired Claude Code guidelines and `andrej-karpathy-skills` repository
- Matt Pocock's AI coding skills and reusable instruction patterns
- Anthropic Cookbook examples and Claude repository guidance
- `AGENTS.md`, `CLAUDE.md`, Cursor rules, and Codex instruction files

Those projects and patterns show that small instruction files can change coding-agent behavior. This contract optimizes for a different shape: portable agent behavior across the full coding-task lifecycle. It covers handoff, protected systems, external input, UX states, verification evidence, and task closure without becoming a framework or skill catalog.

---

## Why there is one edition

A second variant creates another source of truth. Once two contracts exist, they can drift in wording, coverage, and behavior.

This repository keeps one canonical `AGENTS.md` and one equivalent `CLAUDE.md` so the contract remains easy to inspect and hard to misapply.

---

## What this file is not

It is not a benchmark.

It is not a plugin.

It is not a framework.

It is not a catalog of skills.

It is a compact protocol for safer, narrower, more verifiable coding-agent work.
