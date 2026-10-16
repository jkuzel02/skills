# Skills

A catalog of reusable skills for AI agents. Skills describe how to carry out
specific tasks, including when to use them, the workflow to follow, and how to
verify the result.

## Available skills

No skills have been published in this repository yet. As skills are added, this
section will link to their instructions and summarize their purpose.

## Using a skill

Once skills are available:

1. Browse the catalog and select a skill that matches your task.
2. Read its `SKILL.md` for prerequisites, scope, and instructions.
3. Make the skill available to your agent using that agent's supported mechanism
   for loading instructions or installing skills.
4. Give the agent a concrete task, relevant context, and the expected outcome.

Installation and invocation depend on the agent you use. This repository does
not currently provide an installer or agent-specific setup instructions.

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

In fact, even this README file has been created with the [docs-generator skill](./skills/docs-generator/).
