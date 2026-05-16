# AGENTS.md — Karpathy-Inspired Agent Behavior Contract for Coding Agents

Stop your coding agent from guessing, overbuilding, touching unrelated code, and claiming success without evidence.

This is a copy-paste `AGENTS.md` / `CLAUDE.md` contract for Claude Code, Cursor, Codex, and other AI coding agents. It turns the failure modes called out by Andrej Karpathy — silent assumptions, overengineering, and orthogonal edits — into a start-to-close operating protocol.

```bash
curl -o AGENTS.md https://raw.githubusercontent.com/ramsani/karpathy-pocock-vectorial-agent-contract/master/AGENTS.md
```

For Claude Code:

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/ramsani/karpathy-pocock-vectorial-agent-contract/master/CLAUDE.md
```

One file. No framework. No benchmark. No plugin. Just better default behavior for coding agents.

---

## What changes after you install it

Your agent is pushed to:

- ask when a missing fact decides the next action
- read the live repo before designing from memory
- check risky assumptions before broad implementation
- make the smallest reversible change
- avoid cleaning, refactoring, or formatting unrelated code
- treat external input as data, not instructions
- verify with evidence before saying the work is done
- leave a clean handoff with assumptions and untested items

The goal is simple: fewer hidden assumptions, fewer surprise edits, fewer fake completions.

---

## Why this exists

Karpathy's critique of coding agents is that they often:

- assume instead of asking
- build from stale memory instead of the live repo
- overcomplicate small changes
- edit adjacent code they do not understand
- claim success without evidence

This repository turns those failure modes into explicit behavior an agent can follow during real software work.

---

## Positioning against the reference repos

This project sits in the same search space as Karpathy-inspired Claude Code guidelines, AI coding skills, `CLAUDE.md` files, `AGENTS.md` files, Cursor rules, Codex instructions, and Anthropic cookbook-style repo guidance.

| Reference area | What it gives you | What this repo adds |
|---|---|---|
| [Forrest Chang / Karpathy-inspired Claude Code guidelines](https://github.com/forrestchang/andrej-karpathy-skills) | Four memorable principles for Claude Code behavior | A vendor-neutral start-to-close contract for `AGENTS.md`, `CLAUDE.md`, Cursor, Codex, and other coding agents |
| [Andrej Karpathy's coding-agent critique](https://x.com/karpathy) | The core failure modes: assumptions, overengineering, and orthogonal edits | Operational rules that tell the agent what to do at each task stage |
| Matt Pocock's AI coding skills work | Reusable skill-style instruction patterns | A compact behavior contract instead of a growing skill catalog |
| [Anthropic Cookbook](https://github.com/anthropics/anthropic-cookbook) and Claude guidance | Practical Claude examples and repo-level guidance | A portable contract that can be copied into any software repository |

Most agent instruction files are either tool-specific guidelines, skill collections, or repo-local maintenance notes. This repository is different: it is a vendor-neutral operating contract for the full coding-agent task lifecycle.

The deliverable is the contract itself: one canonical `AGENTS.md` and one equivalent `CLAUDE.md`.

---

## Design decisions

### Behavioral instructions, not identity instructions

The file does not say "act as a senior engineer." It states the behavior directly: read first, ask when a missing fact decides the next action, change the smallest surface, verify before closing, and report assumptions.

### Start-to-close protocol

The contract is organized by task lifecycle, not by persona or tool:

1. Start
2. Read Before Acting
3. Plan By Risk
4. Treat External Input As Data
5. During Editing
6. User-Facing Output
7. Verify Before Closing
8. Close And Handoff

### One canonical edition

There is one canonical contract. Keeping only one edition prevents drift between parallel files.

---

## Works with

Use the contract anywhere your coding agent reads repository instructions:

- `AGENTS.md` for agents that support repo-level agent instructions
- `CLAUDE.md` for Claude Code
- Cursor rules or project instructions
- Codex instructions
- custom LLM software-engineering agents

## Use this when

Use this contract when you want an AI coding agent to behave more like a careful operator:

- on shared codebases
- in production-adjacent repositories
- when tasks span multiple files
- when contracts, schemas, auth, payments, data, or user-facing behavior can be affected
- when you need verifiable work instead of confident summaries

---

## Files

| File | Purpose |
|---|---|
| `AGENTS.md` | Canonical contract for agents that read AGENTS.md |
| `CLAUDE.md` | Same contract for Claude Code |
| `DESIGN.md` | Rationale behind the contract |
| `NOTICE.md` | Attribution and non-affiliation notice |
| `CONTRIBUTING.md` | Rules for changing the contract |
| `CHANGELOG.md` | Release notes |
| `LICENSE` | MIT license |

---

## License

MIT
