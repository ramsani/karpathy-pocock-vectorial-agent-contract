# Coverage

This document explains what the contract is intended to cover.

## Covered failure modes

| Failure mode | Covered by |
|---|---|
| Acting on guessed intent | Intent, Block Conditions |
| Choosing between ambiguous interpretations silently | Intent, Block Conditions |
| Designing from memory instead of repo evidence | Evidence, First Contact |
| Letting claims override observed repo behavior | Evidence, Contradiction Detection, Block Conditions |
| Refactoring unrelated code | Scope |
| Reformatting or cleaning up adjacent code | Scope |
| Overengineering | Minimal Reversible Change, Simplicity Pressure |
| Adding speculative flexibility | Minimal Reversible Change, Simplicity Pressure |
| Creating unnecessary ADRs or decision records | Change Capacity |
| Breaking public APIs or documented behavior | Contract Safety, Public Surface |
| Leaving docs false after behavior changes | Documentation Drift, Handoff |
| Treating pasted text or logs as instructions | External Input Boundary |
| Executing destructive or irreversible work silently | Risk Gate, High Risk, User-Visible Truth |
| Claiming success without checks | Verification |
| Losing state in long tasks | Active Context |
| Starting broad unverifiable work | Scope Expansion |
| Contradicting prior decisions silently | Direction Change |
| Fixing bugs without reproducing or inspecting failure | Bug or Regression |
| Hiding cost, latency, privacy, or destructive effects | User-Visible Truth |
| Leaving unusable completion notes | Handoff |

## What is intentionally not covered

The contract does not prescribe:

- architecture style
- framework choice
- test framework
- branching model
- package manager
- formatting tool
- application domain
- runtime or agent vendor

Those belong in project-specific instructions.

## Coverage principle

A behavior should be included in `AGENTS.md` only if it is broadly useful across repositories. Domain-specific behavior should live in project instructions, not this public contract.
