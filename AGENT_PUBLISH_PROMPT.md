# Agent Publish Prompt

Use this prompt with an agent that has access to GitHub.

```text
You are publishing a public GitHub repository from the provided folder.

Goal:
Create a clean public repository for "Karpathy-Pocock Vectorial Composed Learnings".

Repository name:
karpathy-pocock-vectorial-agent-contract

Description:
Karpathy- and Pocock-inspired vectorial agent contract: fewer skills, stronger composition, verifiable coding-agent behavior.

Instructions:
1. Inspect all files before making changes.
2. Do not rewrite the project unless there is a clear broken link, typo, or private/internal reference.
3. Confirm the repo contains:
   - AGENTS.md
   - CLAUDE.md
   - AGENTS.min.md
   - README.md
   - DESIGN.md
   - OPERATORS.md
   - COVERAGE.md
   - EXAMPLES.md
   - NOTICE.md
   - LICENSE
   - PUBLISHING.md
4. Check for private/internal terms:
   grep -RniE "factory|20/40/60/80|secret-token|SwapChatGPT" .
5. If internal terms appear only inside this prompt or publishing guide, do not fail; otherwise remove them.
6. Initialize git if needed.
7. Create the first commit:
   Initial public release of agent behavior contract
8. Publish to GitHub as a public repository.
9. Return:
   - repository URL
   - commit hash
   - files changed
   - any unverified items
   - any risk
```
