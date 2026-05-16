# Karpathy-Pocock Vectorial Agent Contract

A behavioral basis for coding agents.

We do not store every expert behavior. We store a compact basis that can generate them.

This repo turns agent skills into agent instincts.

Instead of installing a growing list of situational skills, it extracts the expert behavior behind those skills and composes it through a compact `AGENTS.md` / `CLAUDE.md` contract.

**The goal:** broader aligned agent behavior with less prompt growth, less context overhead, and more verifiable work.

> More aligned behavior. Less prompt mass.
>
> Composition can replace accumulation.

Inspired by Andrej Karpathy's coding-agent failure modes and Matt Pocock's composable agent skills work. Independent project. Not affiliated with or endorsed by either author or their projects.

---

## The product

Copy one file into a repo:

```bash
curl -o AGENTS.md https://raw.githubusercontent.com/ramsani/karpathy-pocock-vectorial-agent-contract/master/AGENTS.md
```

The agent gets a compact behavioral contract that pushes it to:

- ask before guessing
- read the repo before designing
- keep scope narrow
- avoid speculative abstractions
- make surgical, reversible changes
- name public contract changes
- stop before risky work
- verify before claiming success
- leave an auditable handoff

For tight context windows, use `AGENTS.min.md` instead.

---

## Core thesis

A useful skill contains more than a procedure. It contains transferable expert behavior.

A skill says:

```text
When this situation appears, follow this recipe.
```

This contract asks:

```text
What behavior makes that recipe work?
What part is domain-specific?
What part transfers across repositories?
What condition should activate it?
How can it compose with other behaviors?
```

The reusable parts become behavioral vectors and context operators.

**A skill teaches a recipe. A behavior teaches judgment.**

---

## From skills to instincts

Most agent systems grow by adding more skills. That works, but it increases context and creates a long catalog of situational recipes.

This project takes the opposite path:

1. Start with a large set of expected expert behaviors.
2. Decompose them into near-orthogonal behavioral components.
3. Keep the components that are broadly reusable.
4. Add context operators that multiply those components when conditions appear.
5. Recompose them into the original behavior space.
6. Generate new aligned behavior in adjacent situations without adding a new skill for each case.

That is the practical meaning of “vectorial” here.

Linear algebra gives the metaphor:

```text
find a basis → compose vectors → span a space
```

This repo applies that idea to agent behavior:

```text
find a compact behavioral basis → compose it with context operators → span a larger space of aligned coding-agent conduct
```

It is not a mathematical proof. It is a design discipline: reduce behavior to reusable basis vectors, then recover specificity through composition.

---

## Why Karpathy + Pocock

Karpathy clearly named common coding-agent failures:

> "The models make wrong assumptions on your behalf and just run along with them without checking. They don't manage their confusion, don't seek clarifications, don't surface inconsistencies, don't present tradeoffs, don't push back when they should."

> "They really like to overcomplicate code and APIs, bloat abstractions."

Pocock showed a practical delivery form: small, useful, composable agent skills for real engineering work.

This repo connects those ideas differently:

```text
Karpathy identifies the failure modes.
Pocock demonstrates composable engineering skills.
This project extracts the behavioral substrate behind both.
```

The result is not a larger skill catalog. It is a smaller behavioral basis.

---

## Skill catalog vs vectorial contract

| Skill catalog | Vectorial contract |
|---|---|
| Adds procedures | Extracts behavior |
| Grows by accumulation | Grows by composition |
| Many situational recipes | Few reusable behavioral vectors |
| Tool or workflow specific | Agent-behavior focused |
| More context per new case | More reuse across cases |
| Teaches what to do | Teaches how to decide |

---

## The 10 base vectors

These are the independent behavioral dimensions in the contract:

| # | Vector | Prevents |
|---|---|---|
| 1 | Intent | Wrong assumptions, silent interpretation |
| 2 | Evidence | Designing from memory instead of repo |
| 3 | Scope | Expanding beyond what was requested |
| 4 | Minimal Reversible Change | Overengineering, unnecessary abstractions |
| 5 | Contract Safety | Silent changes to APIs, schemas, auth, user behavior |
| 6 | External Input Boundary | Treating pasted/logged/generated content as instructions |
| 7 | Risk Gate | Proceeding through high-risk work without authorization |
| 8 | Verification | Claiming success without evidence |
| 9 | Change Capacity | Introducing debt without naming it |
| 10 | Handoff | Ending without auditable status |

---

## The context operators

Operators activate only when their condition appears. They do not replace the base vectors; they multiply them.

| Operator | When it activates | Adds |
|---|---|---|
| First Contact | New repo or unknown context | Read before proposing |
| Active Context | Task spans files, steps, decisions, or risks | Keep state explicit |
| Scope Expansion | Work is too broad to verify as one unit | Propose a slice first |
| Direction Change | User request conflicts with prior decision | Name the conflict |
| Contradiction Detection | Claims conflict with observed repo evidence | Prefer observed evidence |
| Bug or Regression | Fixing a bug or failed test | Reproduce or inspect before fixing |
| Public Surface | APIs, schemas, CLI, env, file formats, auth, user behavior | Name compatibility impact |
| Documentation Drift | Behavior changes docs describe | Update docs or report drift |
| High Risk | Production, secrets, auth, payments, privacy, migrations, deletion | Stop and confirm |
| External Tool | Unfamiliar tool, library, API, framework, service | Read docs or local usage first |
| Simplicity Pressure | Abstraction, flags, dependencies, speculative flexibility | Use existing code first |
| User-Visible Truth | Cost, latency, privacy, destructive or irreversible behavior | Do not hide impact |

---

## Behavioral algebra

```text
specialized behavior = base vectors × context operators
behavior space ≈ span(base behavioral vectors, context operators)
```

Examples:

```text
Simplicity Pressure × Minimal Reversible Change
= do not add abstraction unless it reduces an existing risk or the requested outcome requires it
```

```text
Risk Gate × High Risk
= stop before execution, report rollback path and available evidence
```

```text
Contract Safety × Public Surface
= name the affected API/schema/CLI/env/file/user-facing surface and state compatibility impact
```

```text
Evidence × Contradiction Detection
= stated behavior does not override observed repository evidence
```

The important property: when a useful skill is distilled into vectors and operators, the agent can behave correctly in neighboring situations that were never written as separate skills.

In practice, small added details can act like coefficients: they change the intensity, priority, or target of existing behavioral vectors without requiring a whole new procedure.

---

## Block conditions

The agent must stop and ask, or report a blockage, before proceeding when:

- required context is missing and no safe assumption is possible
- multiple valid interpretations exist and choosing silently could change the result
- stated behavior conflicts with observed repository evidence and affects the decision
- the requested change conflicts with user intent, contracts, tests, docs, or prior decisions
- the task requires destructive, irreversible, production, secret, payment, privacy, migration, deletion, or data movement actions
- verification cannot be performed and presenting success would be risky
- the task is too broad to verify as one unit and no smaller slice has been defined

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

## Files

- `AGENTS.md` — full behavioral contract
- `CLAUDE.md` — same contract for Claude Code users, with Claude-specific filename
- `AGENTS.min.md` — compressed version for tight context windows
- `OPERATORS.md` — operator catalog
- `DESIGN.md` — design notes on reduction and composition
- `COVERAGE.md` — rule-level coverage matrix
- `EXAMPLES.md` — behavior examples
- `NOTICE.md` — attribution and independence statement

---

## How to know it is working

These rules are working when:

- diffs are smaller and easier to review
- fewer changes are rewritten due to overengineering
- ambiguity is surfaced before implementation
- contradictions between claims and repo evidence are named early
- success claims include evidence instead of confidence
- unrelated code remains untouched
- handoffs are short, specific, and auditable

---

## Attribution

Inspired by Andrej Karpathy's public guidance on LLM coding failures and Matt Pocock's public coding-agent skills work.

This is an independent project. It is not affiliated with or endorsed by Andrej Karpathy, Matt Pocock, `multica-ai/andrej-karpathy-skills`, or `mattpocock/skills`.

The goal is not to replace those works. It is to extract the transferable behaviors behind them and express those behaviors as a compact, composable contract for coding agents.
