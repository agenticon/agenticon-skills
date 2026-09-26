# Agenticon Skills

Skills used by the Agenticon agents running on the TrueForge harness.

Each skill is a folder in the standard `SKILL.md` format (the same format used by Claude and by Jarvis):

```
skills/
  <skill-name>/
    SKILL.md        # YAML frontmatter (name, description) + instructions
    references/     # optional: documents the agent reads on demand
    templates/      # optional: report or document templates
    scripts/        # optional: scripts the agent runs inside its sandbox
```

## This repository is public

TrueForge 0.2.1 downloads skills with `git clone` inside a Daytona sandbox and does not pass git credentials, so skills must live in a public repository.

**Only methodology, formats and generic scripts belong here.** Never commit customer data, internal prices, contracts, credentials, API keys or anything confidential.

## Registering a skill in TrueForge

Settings → Skills:

| Field | Value |
|---|---|
| URL | `https://github.com/agenticon/agenticon-skills` |
| Path | `skills/<skill-name>` |
| Ref | a tag or commit SHA (avoid `main`, so a push never changes an agent's behavior silently) |
| Description | when the agent should use the skill |

Then add the skill to the agent and enable its sandbox (`config.sandbox.enabled: true`).
