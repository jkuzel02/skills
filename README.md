# Skills

A catalog of reusable skills for AI agents. Skills describe how to carry out
specific tasks, including when to use them, the workflow to follow, and how to
verify the result.

## Available skills

| Skill | Purpose |
| --- | --- |
| [docs-generator](./skills/docs-generator/SKILL.md) | Generate, update, and audit README files and API documentation against the actual repository source code. |

The documentation generator supports README updates, API documentation, accuracy
audits, and combined README/API updates. It verifies commands, links, and examples
against the repository and limits changes to the requested documentation.

## Using a skill

1. Browse the catalog and select a skill that matches your task.
2. Read its `SKILL.md` for prerequisites, scope, and instructions.
3. Make the skill available to your agent using that agent's supported mechanism
   for loading instructions or installing skills.
4. Give the agent a concrete task, relevant context, and the expected outcome.

Installation and invocation depend on the agent you use. This repository does
not currently provide an installer or agent-specific setup instructions.

For example, after making `docs-generator` available to your agent, ask:

```text
Use docs-generator to update README.md based on the current repository.
Verify the documented commands and links, and modify only README.md.
```

For API documentation, the skill uses `docs/API.md` by default unless the target
repository follows another convention. It does not install dependencies without
explicit authorization or run destructive commands or deployments.

## Adding a skill

Use the following layout for new contributions:

```text
skills/
└── <skill-name>/
    ├── SKILL.md
    └── ... supporting resources, if needed
```

Each `SKILL.md` should include:

- A name and a concise description of the skill's purpose.
- When to use it and what falls outside its scope.
- Required tools, permissions, and inputs.
- Clear workflow steps and a practical usage example.
- Verification steps and any known limitations.

Keep supporting resources alongside the skill and reference them with relative
paths. Never include credentials, tokens, or other secrets.

Before submitting a contribution, check that the instructions match the included
resources, verify any commands and examples, and add a link and description to
the **Available skills** section above. Document any agent-specific requirements
explicitly.

---

This README is maintained with the [docs-generator skill](./skills/docs-generator/SKILL.md).
