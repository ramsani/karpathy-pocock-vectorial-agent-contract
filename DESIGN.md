# Design Notes — Why This File Works

Most AGENTS.md files are lists of preferences. This one is behavioral engineering. The distinction matters technically, not just philosophically.

---

## The core hypothesis

Modern LLMs are sufficiently capable that they don't need to simulate an expert to produce expert-level output. What they need is a reduction of the behavioral space at each decision point.

The failure modes Karpathy identified — silent assumptions, overcomplicated solutions, orthogonal damage — are not intelligence failures. They are default behavior in the absence of constraints. The model is doing what its training distribution makes most probable when no specific constraint applies.

For multi-step work, this means constraints must force the agent to identify and test the assumption most likely to invalidate the plan before broad implementation.

The job of an agent configuration file is not to make the model smarter. It is to make certain behaviors more probable than their failure-mode alternatives at the exact moment a decision is made.

For user-facing work, constraints must also force explicit UX-state coverage and explicit reporting of unverified UX quality. For delivery-facing work, constraints must separate evidence from acceptance and require stronger gates for trust-critical flows.

---

## Behavioral engineering vs. identity engineering

There are two architectures for agent instruction files:

**Identity engineering** tells the model who to be:
> "Act as a senior software engineer with 20 years of experience..."

**Behavioral engineering** tells the model what to do, how, and why:
> "Edit only what the request requires. Do not reformat, clean unrelated code, refactor nearby code, change local style or add unrequested improvements."

Identity engineering has a structural problem: the model must first construct and maintain a fictional persona, then derive the correct behavior from that persona. This introduces two failure points — persona construction and behavior derivation — and consumes context window maintaining an identity that produces no direct output value.

Behavioral engineering eliminates both failure points. The instruction operates at the decision layer directly. No persona to maintain. No derivation required.

This file uses only behavioral engineering. There are no roles, no personas, no "act as." Only constraints on what to do, how to do it, and why that constraint exists.

---

## The minimum executable unit

Each rule in this file follows a deliberate structure:

**What** to do → **How** to do it → **Why** that constraint exists

This is not stylistic. It is the minimum unit of instruction that allows a capable model to apply a rule correctly in edge cases it has never seen.

"What" alone produces literal compliance that fails at boundaries. "What + how" produces mechanical execution that fails at judgment calls. "What + how + why" produces a model that can reconstruct the correct behavior even in situations the rule author didn't anticipate — because the intent is encoded in the instruction, not left to inference.

---

## Semantic precision as engineering

Every instruction in this file was audited from inside the agent's perspective — line by line, word by word. The criterion: can this sentence be evaluated as true or false at the moment of execution, without inferring external context?

Terms that failed that test were replaced:

| Replaced | With |
|----------|------|
| "use judgment" | "apply only the rules directly relevant to the request" |
| "trivial tasks" | "single-step tasks with no risk of side effects" |
| "if the assumption is safe" | "if proceeding cannot cause an irreversible or hard-to-detect error" |
| "foreign changes" | "changes not made by you" |
| "vertical slices" | "steps that each deliver something observable and independently verifiable" |
| "orphans" | "dead code created by your change" |
| "decorative tests" | "tests that pass without covering behavior" |
| "preserve change capacity" | "keep the codebase easy to change" |
| "trustworthy microcopy" | "text that accurately describes what each action does" |
| "main flow" | "synchronous execution path" |
| "compact handoff" | "limited to what another agent needs to continue" |

This is not editing for clarity. It is engineering for determinism. Each replacement reduces the distance between the instruction and the decision — which is the only variable a configuration file can control.

---

## Context window as a design constraint

Every token in a configuration file competes with the tokens that carry actual task information. This creates a real engineering tradeoff: more instructions reduce failure modes but also reduce the effective context available for the task.

This file is designed around that constraint:

- 12 rules cover the failure modes that actually appear in production — not an exhaustive taxonomy
- Each rule is written at the minimum length that preserves the what+how+why structure
- No rule contains theory, examples, or justification beyond what the model needs to execute
- Identity instructions are eliminated entirely — they consume context without improving behavior

The result is maximum behavioral coverage per token.

---

## Why this is technically correct for current LLMs

LLMs generate tokens by sampling from probability distributions conditioned on context. A configuration file works by shifting those distributions — making certain outputs more probable at each decision point.

Behavioral instructions shift distributions directly at the decision layer. Identity instructions shift distributions indirectly, via persona construction, which introduces variance between the intended behavior and the actual output.

RLHF and modern alignment training reinforce specific behaviors, not identities. A file written in the language of behavior — concrete actions with stated rationale — is more aligned with how these models were trained than a file written in the language of persona.

This is not a claim that behavioral instructions guarantee perfect adherence. Models are probabilistic and no instruction set eliminates variance entirely. It is a claim that behavioral instructions minimize the distance between the instruction and the decision — which is the maximum any configuration file can achieve with current architectures.

---

## What this file is not

It is not a prompt that makes the model smarter. The model's intelligence is fixed.

It is not a simulation of an expert. Expert simulation requires identity maintenance that consumes context and introduces derivation variance.

It is not a comprehensive methodology. It is a minimal set of behavioral constraints derived from real production failure patterns.

It is a set of probability shifts — designed to make the model's defaults less probable and the correct behaviors more probable, at the exact moments those decisions are made.
