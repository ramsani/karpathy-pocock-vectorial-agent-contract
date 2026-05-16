# Notice

This project was initially motivated by the public discussion around lightweight agent instruction files and coding-agent skills, including:

- `multica-ai/andrej-karpathy-skills`
- https://github.com/multica-ai/andrej-karpathy-skills
- `mattpocock/skills`
- https://github.com/mattpocock/skills

Those projects helped show two important things:

- coding agents fail in repeated, nameable ways
- small composable instructions can improve real engineering behavior

This repository explores a different direction: treating skills as source material for a compact behavioral basis.

It extracts transferable expert behavior from situational skills, expresses that behavior as base vectors and context operators, and composes those pieces into a portable `AGENTS.md` / `CLAUDE.md` contract.

This project is independent and is not affiliated with or endorsed by Andrej Karpathy, Matt Pocock, `multica-ai/andrej-karpathy-skills`, or `mattpocock/skills`.

The goal is attribution without overstating novelty or affiliation. This project builds on a public line of thought and contributes a more explicit organization of the same practical problem: how to make coding agents safer, narrower, more verifiable, and easier to hand off without growing prompt context linearly.
