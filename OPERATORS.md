# Operators

Operators specialize the base rules when a matching condition appears. They should not be activated manually by name; the condition triggers them.

## First Contact

Use when working in a repository without established context.

Purpose: prevent design from memory.

Effect: read README, structure, relevant files, and existing patterns before proposing or editing.

## Active Context

Use when a task spans multiple files, steps, decisions, or risks.

Purpose: prevent loss of working state.

Effect: keep goal, touched files, decision, open risk, and next check explicit.

## Scope Expansion

Use when work spans multiple independent areas, has unclear completion criteria, or is too large to verify as one unit.

Purpose: prevent broad unverifiable work.

Effect: define a smaller first verifiable slice and name what is deferred.

## Risk-First Planning

Use when work has multiple steps, uncertain constraints, data, permissions, contracts, integrations, critical UX, or a decision that could invalidate the approach.

Purpose: prevent broad implementation before the riskiest assumption is checked.

Effect: identify the constraint most likely to invalidate the plan, check it first, prefer vertical slices, state what each slice touches and how it will be checked, and avoid parallel work over shared critical files, data, migrations, or unstable contracts.

## Direction Change

Use when the user asks for something that conflicts with a prior decision, constraint, or accepted tradeoff in the current task.

Purpose: prevent silent contradiction.

Effect: name the conflict and ask whether to preserve or replace the prior direction.

## Contradiction Detection

Use when stated behavior conflicts with observed code, docs, tests, logs, or outputs.

Purpose: prevent assumptions from overriding repository evidence.

Effect: name the contradiction, state what was claimed, state what was observed, and do not resolve silently.

## Bug or Regression

Use when fixing a bug, failed test, or inconsistent behavior.

Purpose: prevent blind edits.

Effect: reproduce or inspect the failure, identify likely cause, fix minimally, verify against the failure mode.

## Public Surface

Use when touching API, schema, CLI flag, environment variable, file format, permission model, data model, documented behavior, or user-facing behavior.

Purpose: prevent accidental breaking changes.

Effect: name the affected surface, state what changes, state what remains compatible, verify the narrowest public behavior.

## Documentation Drift

Use when a task changes behavior, contracts, setup, terminology, or decisions that existing docs describe.

Purpose: prevent documentation from becoming false as part of the change.

Effect: update affected docs in the same change, or report the drift when docs are out of scope. Do not create new documentation structures unless required.

## Product UX

Use when work touches user-facing UI, flows, forms, errors, onboarding, checkout, dashboards, or visible product behavior.

Purpose: prevent technically working flows that trap, confuse, or mislead users.

Effect: treat loading, empty, success, failure, recovery, and next action as part of the main flow; use clear text, useful errors, trustworthy microcopy, essential accessibility, and reasonable mobile behavior when relevant; report unverified UX quality.

## High Risk

Use when touching production, secrets, auth, payments, privacy, migrations, deletion, irreversible actions, or data movement.

Purpose: prevent silent high-risk execution.

Effect: stop when confirmation is required, report risk and rollback path, prefer reversible preparation.

## External Tool

Use when using an unfamiliar tool, library, API, framework, or service.

Purpose: prevent hallucinated usage.

Effect: read official docs or local usage first, then verify with the smallest command or example.

## Simplicity Pressure

Use when a solution could add abstraction, provider, flag, configuration, dependency, worker, framework, future flexibility, or substantially more code than an equivalent simpler change.

Purpose: prevent overengineering.

Effect: use existing code first, add concepts only when required or risk-reducing, reject speculative flexibility.

## User-Visible Truth

Use when behavior affects latency, cost, privacy, destructive actions, irreversible actions, data movement, or user-facing behavior.

Purpose: prevent misleading user communication.

Effect: describe what the system actually does and reveal cost, uncertainty, delay, privacy implications, or irreversible effects before execution when relevant.

## Acceptance Gate

Use when work is intended for a user, customer, demo, beta, production, or a trust-critical flow.

Purpose: prevent treating passing tests as sufficient acceptance.

Effect: assess user impact, business impact, system fragility, data risk, security risk, known issues, rollback, and observability when relevant; classify residual findings; require fresh review, cross-evidence, or explicit user acceptance for high-risk work before calling it complete.
