# Design

This repository treats an agent instruction file as behavioral modeling, not role assignment, not rule sections, and not skill accumulation.

A role asks the model to infer what a good engineer would do. A rule section tells it what to obey in one block. A skill gives it a recipe for one situation. A behavioral contract defines the reusable conduct that makes expert work reliable across many situations.

The central idea is simple: do not store every expert behavior; store a compact basis that can generate them.

The target is not section compliance. The target is professional conduct shaped by composable, regulated, internalized behavior patterns.

The goal is to reduce avoidable coding-agent failures without making the instruction file so large that the agent stops following it.

## Design constraints

The contract should be:

- short enough to remain usable in real agent contexts
- explicit enough to avoid hidden interpretation
- general enough for public repositories
- strict enough to block unsafe or unverifiable work
- composable enough to avoid repeating the same rule in many forms
- compact enough that adding behavior does not require linear prompt growth

## Behavioral basis

The core design move is reduction.

Start with a large set of expected expert behaviors. Decompose that set into near-orthogonal behavioral components. Keep the components that are broadly reusable across repositories. Then recover the original behavior space by composing those components with context operators.

This is what “vectorial” means in this project:

```text
expert behavior space ≈ span(base behavioral vectors, context operators)
specialized behavior = base behavioral vectors × context operators × local details
```

Linear algebra gives the metaphor:

```text
find a basis → compose vectors → span a space
```

This project applies that metaphor to agent behavior:

```text
find a compact behavioral basis → compose it with context operators → span a larger space of aligned conduct
```

This is not a mathematical proof. It is a practical discipline for prompt design:

- avoid duplicate instructions
- avoid one recipe per situation
- isolate the behavior that transfers
- let context activate the right combination
- use small local details like coefficients that adjust priority, intensity, or target
- preserve coverage while shrinking the contract

## Skill distillation

A skill is a situated behavior package: trigger, procedure, domain assumptions, and expected outputs.

This contract treats useful skills as source material. The process is:

1. Identify the behavior the skill reliably produces.
2. Separate domain-specific assumptions from general agent behavior.
3. Extract the independent behavioral vectors.
4. Attach each vector to a condition or operator.
5. Preserve only what improves behavior across repositories.
6. Remove the situational recipe when the behavior can be recovered by composition.

The agent does not need to carry every skill if the underlying behavior has been internalized into the contract.

A skill teaches a recipe. A behavior teaches judgment.

## Base vectors

The full contract uses ten base vectors:

1. Intent
2. Evidence
3. Scope
4. Minimal Reversible Change
5. Contract Safety
6. External Input Boundary
7. Risk Gate
8. Verification
9. Change Capacity
10. Handoff

Each base vector covers a distinct behavioral dimension. A vector should remain only if removing it would leave a behavior that cannot be reconstructed from the others without new interpretation.

## Composition operators

Operators are not extra principles and not extra procedure sections. They are contextual regulators and multipliers.

For example:

```text
Contract Safety × Public Surface
= name the API/schema/CLI/env/file/user-facing surface and state compatibility impact
```

```text
Verification × Bug or Regression
= reproduce or inspect the failure, fix the cause, then verify against that failure mode
```

```text
Evidence × Contradiction Detection
= stated behavior does not override observed repository evidence
```

```text
Scope × Simplicity Pressure
= avoid abstractions, flags, providers, dependencies, or future flexibility unless required
```

```text
Contract Safety × Documentation Drift
= if changed behavior makes existing docs false, update docs or report the drift
```

This structure lets the contract stay compact while still producing specific behavior in practical situations.

## From skills to instincts

The desired outcome is not that the agent memorizes more procedures. The desired outcome is that the agent acts as if it had better engineering instincts.

When knowledge is internalized, behavior can change. This contract uses that human pattern as a design target for agents.

When a useful skill is distilled into vectors and operators, the agent can produce aligned behavior in neighboring situations that were never written as separate skills.

That is the leverage: new aligned conduct can emerge from combinations of existing behavioral components plus small task-specific details, instead of requiring a new instruction block for every case.

The skill is no longer just a recipe to execute. It becomes a behavioral influence that changes what the agent notices, asks, avoids, verifies, and reports.

That is the main product claim:

```text
Extract behavior from skills.
Integrate it into the behavioral basis.
Let operators compose it into new aligned conduct.
```

## Controlled specialization

Specialization does not require a new persona.

A bugfix workflow, high-risk workflow, public API workflow, unfamiliar-tool workflow, or documentation-drift workflow can be expressed as the same base contract multiplied by a different operator.

```text
specialized behavior = base vectors × context operators
```

This makes the behavior more inspectable than a role prompt because the specialization comes from visible conditions and obligations, not from an implied identity.

The aim is not to make the agent perform a role. The aim is to modify how it notices, decides, acts, verifies, and hands off work.

## Decision records

Decision records are gated.

An ADR should exist only when all three are true:

- the decision is costly to reverse
- the decision would surprise a future maintainer without context
- genuine alternatives existed

This prevents the contract from turning every choice into permanent process overhead.

## Why include CLAUDE.md?

`CLAUDE.md` is the same contract as `AGENTS.md`, included for Claude Code users. The behavior should not fork by tool unless a project intentionally needs tool-specific instructions.

The title may differ to match the filename. The behavioral content should stay equivalent.

## Why not just list every rule?

A long flat list becomes hard to follow. It also hides which rules are fundamental and which are contextual.

The base/operator split keeps invariant behavior separate from the conditions that specialize it.

## No certainty claim

This contract does not prove that every model will always behave correctly. The realistic claim is narrower:

- explicit obligations are easier to follow than vague principles
- contextual operators reduce silent interpretation
- blocking conditions make uncertainty and risk visible
- handoff format makes completion auditable
- behavior can be expanded by composition instead of by adding one instruction per case

The contract improves the agent's operating envelope; it does not replace review, tests, or engineering judgment.
