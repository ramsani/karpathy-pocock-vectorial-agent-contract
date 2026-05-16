# Contributing

Contributions should preserve the repository shape: one canonical `AGENTS.md`, one equivalent `CLAUDE.md`, and minimal supporting documentation.

## Good contributions

- clarify an instruction without broadening it
- remove ambiguity from wording
- improve attribution or positioning
- fix documentation drift
- reduce files or duplicated concepts

## Avoid

- alternate contract versions
- benchmarks, harnesses, or demos
- framework-specific defaults
- project-specific workflows
- long prompt templates
- vague principles that require interpretation
- role prompts such as "act as a senior engineer"

## Test for a change

Before changing the contract, ask:

1. Does this reduce a repeated coding-agent failure mode?
2. Can an agent follow it without project-specific knowledge?
3. Does it preserve the start-to-close protocol?
4. Does the same behavior already exist elsewhere in the file?

If the answer to #4 is yes, clarify the existing instruction instead of adding another one.
