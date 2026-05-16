# Design

This repository treats an agent instruction file as behavioral modeling, not role assignment.

A role asks the model to infer what a good engineer would do. A behavioral contract tells the model what must happen, what must not happen, when to stop, and what evidence is required before claiming success.

The goal is to reduce avoidable coding-agent failures without making the instruction file so large that the agent stops following it.

## Design constraints

The contract should be:

- short enough to remain usable in real agent contexts
- explicit enough to avoid hidden interpretation
- general enough for public repositories
- strict enough to block unsafe or unverifiable work
- composable enough to avoid repeating the same rule in many forms

## Skill distillation

A skill is a situated behavior package: trigger, procedure, domain assumptions, and expected outputs.

This contract treats useful skills as source material. The process is:

1. Identify the behavior the skill reliably produces.
2. Separate domain-specific assumptions from general agent behavior.
3. Extract the independent behavioral vectors.
4. Attach each vector to a condition or operator.
5. Preserve only what improves behavior across repositories.

The agent does not need to carry every skill if the underlying behavior has been internalized into the contract.

This is the practical reason for the vector model: composition can replace accumulation.

## Behavioral basis

The full contract uses ten base rules:

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

Each base rule covers a distinct behavioral dimension. A rule should remain only if removing it would leave a behavior that cannot be reconstructed from the others without new interpretation.

## Composition operators

Operators are not extra principles. They are contextual multipliers.

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

This structure lets the contract stay compact while still producing specific behavior in practical situations. Decision records are also gated: an ADR should exist only when the decision is costly to reverse, surprising without context, and based on real alternatives.

## Controlled specialization

Specialization does not require a new persona.

A bugfix workflow, high-risk workflow, public API workflow, or unfamiliar-tool workflow can be expressed as the same base contract multiplied by a different operator.

```text
specialized behavior = base rules × context operators
```

This makes the behavior more inspectable than a role prompt because the specialization comes from visible conditions and obligations, not from an implied identity.

## Why include CLAUDE.md?

`CLAUDE.md` is the same contract as `AGENTS.md`, included for Claude Code users. The behavior should not fork by tool unless a project intentionally needs tool-specific instructions.

## Why not just list every rule?

A long flat list becomes hard to follow. It also hides which rules are fundamental and which are contextual. The base/operator split keeps the invariant behavior separate from the conditions that specialize it.

## No certainty claim

This contract does not prove that every model will always behave correctly. The realistic claim is narrower:

- explicit obligations are easier to follow than vague principles
- contextual operators reduce silent interpretation
- blocking conditions make uncertainty and risk visible
- handoff format makes completion auditable

The contract improves the agent's operating envelope; it does not replace review, tests, or engineering judgment.
