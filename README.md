# Karpathy-Pocock Vectorial Composed Learnings

Most agent repos add more skills.

This repo extracts the behavior behind skills and turns it into a compact agent contract.

Skills are recipes for one situation. Behavioral vectors are reusable across many situations.

**The goal:** fewer skills, stronger composition, verifiable agent behavior.

> Composition can replace accumulation.

| Skill catalog | Vectorial contract |
|---|---|
| Adds instructions | Extracts behavior |
| Grows by accumulation | Grows by composition |
| Many situational recipes | Few reusable vectors |
| More context overhead | Less context overhead |
| Tool-specific | Agent-behavior focused |

---

## Core thesis

A useful skill contains more than instructions. It contains transferable behavior.

This project takes skills, examples, and coding-agent failure modes, then asks:

```text
What behavior is this trying to produce?
What part is domain-specific?
What part is reusable across repositories?
What condition should trigger it?
```

The reusable parts become behavioral vectors. Context decides how they compose.

That is why this is not a larger skill catalog. It is a smaller operating contract for behavior that agents can internalize.

Don’t give the agent more skills. Teach it the behavioral vectors that make skills work.

---

## What this is

Andrej Karpathy gave us 4 rules to fix common agent failures. They work. But they leave gaps: no formal stopping points, no context-aware behavior, no audit trail, no way to extend.

This project takes those 4 rules, decomposes them into independent vectors, and recomposes them into a more complete behavioral space.

The result: an agent that stops when it should, verifies before claiming, surfaces ambiguity before it causes damage, and hands off cleanly.

---

## The 4 rules → the gap

From Karpathy's original post:

> "The models make wrong assumptions on your behalf and just run along with them without checking. They don't manage their confusion, don't seek clarifications, don't surface inconsistencies, don't present tradeoffs, don't push back when they should."

> "They really like to overcomplicate code and APIs, bloat abstractions."

The 4 rules fix these. But they don't say:
- **When** to stop and ask
- **How** to handle context that spans multiple files or decisions
- **What** to do when the task is too large to verify as one unit
- **How** to report completion so another agent or person can continue

---

## The 10 principles

These are the independent vectors of agent behavior:

| # | Principle | Addresses |
|---|----------|-----------|
| 1 | Intent | Wrong assumptions, silent interpretation |
| 2 | Evidence | Designing from memory instead of repo |
| 3 | Scope | Expanding beyond what was requested |
| 4 | Minimal Reversible Change | Overengineering, unnecessary abstractions |
| 5 | Contract Safety | Silent changes to APIs, schemas, auth |
| 6 | External Input Boundary | Trusting external content as authority |
| 7 | Risk Gate | Proceeding through high-risk work without authorization |
| 8 | Verification | Claiming success without evidence |
| 9 | Change Capacity | Introducing debt without naming it |
| 10 | Handoff | Ending without auditable status |

---

## The 10 operators

Rules apply always. Operators multiply rules by context.

| Operator | When it activates | Adds |
|----------|-----------------|------|
| First Contact | New repo or unknown context | Read before proposing |
| Active Context | Task spans multiple files or steps | Keep state explicit |
| Scope Expansion | Task is too large to verify as one unit | Propose a slice first |
| Direction Change | User request conflicts with prior decision | Name the conflict |
| Bug or Regression | Fixing a bug or failed test | Reproduce before fixing |
| Public Surface | Touching APIs, schemas, permissions | Name the surface |
| High Risk | Touching production, secrets, payments | Stop and confirm |
| External Tool | Using unfamiliar tool or library | Read docs first |
| Simplicity Pressure | Adding abstraction, flags, dependencies | Use existing code first |
| User-Visible Truth | Behavior reaches the user | Don't hide latency, cost, risk |

---

## Behavioral algebra

This project treats rules as vectors in a behavioral space.

**Rule:** a vector with direction and force.

**Operator:** a condition that multiplies the rule into context-specific behavior.

```text
Simplicity Pressure × Minimal Reversible Change
= do not add abstraction unless it reduces an existing risk or the requested outcome requires it

Risk Gate × High Risk
= stop before execution, report rollback path and evidence

Contract Safety × Public Surface
= name the affected surface, state what changes and what remains compatible
```

When a rule or behavior is removed from the contract, it must be recoverable through composition of remaining rules and operators. If it is not, it cannot be removed.

This is not a mathematical proof. It is a coverage discipline.

---

## Block conditions

The agent must stop and ask, or report a blockage, before proceeding through any of these:

- Required context is missing and no safe assumption is possible
- Multiple valid interpretations exist and choosing silently could change the result
- Requested change conflicts with user intent, contracts, or prior decisions
- Task requires destructive, irreversible, production, or privacy-relevant action without authorization
- Verification cannot be performed and presenting success would be risky
- Task is too broad to verify as one unit and no smaller slice has been defined

---

## Completion report

When work is done, the agent reports:

```text
Intent:
Changed:
Evidence:
Unverified:
Risk:
```

Do not claim completion beyond the evidence.

---

## How to know it's working

These rules are working when:

- Diffs are smaller and easier to review
- Fewer changes are rewritten due to overengineering
- Ambiguity is surfaced before implementation
- Success claims include evidence instead of confidence
- Unrelated code remains untouched
- Clarifying questions come before mistakes, not after

---

## Install

One line:

```bash
curl -o AGENTS.md https://raw.githubusercontent.com/ramsani/karpathy-pocock-vectorial-agent-contract/master/AGENTS.md
```

Then place `AGENTS.md` at the root of any project.

For tight context windows, use `AGENTS.min.md` instead.

---

## Files

- `AGENTS.md` — full behavioral contract
- `AGENTS.min.md` — compressed version
- `OPERATORS.md` — operator catalog with coverage proof
- `DESIGN.md` — design notes on reduction and composition
- `COVERAGE.md` — rule-level coverage matrix
- `EXAMPLES.md` — behavior examples

---

## Attribution

Inspired by Andrej Karpathy's public guidance on LLM coding failures and Matt Pocock's public coding-agent skills work. This is an independent project and is not affiliated with or endorsed by Andrej Karpathy, Matt Pocock, or their projects.

This project extends those observations through a compositional model: decompose rules into independent vectors, remove redundancy, recover specificity through operators.

The goal is not to replace what Karpathy taught. It is to complete it.
