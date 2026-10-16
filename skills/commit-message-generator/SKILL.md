---
name: commit-message-generator
description: Generate exactly one precise Conventional Commit message by inspecting the current repository's Git changes. Use when the user asks for a commit message, wants to summarize changes for a commit, or invokes $commit-message-generator.
---

# Commit Message Generator

Generate a single accurate Conventional Commit message
based on actual changes in the repository.

## Workflow

### 1. Inspect Git changes

Run:

- `git status --short`
- `git diff --cached --stat`
- `git diff --cached`

If staged changes exist, consider ONLY staged changes.

If nothing is staged, inspect unstaged tracked changes:

- `git diff --stat`
- `git diff`

Also inspect untracked files when relevant. Git does not
include their contents in ordinary diffs.

Do not include unrelated changes or already committed work.

If necessary, inspect nearby source code to understand
the purpose and impact of the changes.

Check recent commit messages using:

- `git log -5 --pretty=format:%s`

Use repository conventions for scope and wording, but
always follow Conventional Commits ([v1.0.0 specification link](https://www.conventionalcommits.org/en/v1.0.0/)).

### 2. Understand the changes

Determine:

- What functionality was added, removed, or modified?
- What bug or behavior was corrected?
- Was this a refactor without behavior changes?
- Were only documentation, tests, or configuration changed?
- What is the primary purpose of the change?

Focus on the actual behavior or intent, not file names.

Never invent changes that are not supported by the diff.

### 3. Choose the commit type

Use the most appropriate Conventional Commit type:

- feat: new functionality
- fix: bug fix
- refactor: code restructuring without behavior changes
- perf: performance improvement
- docs: documentation-only changes
- test: test-only changes
- build: build system or dependency changes
- ci: CI/CD configuration changes
- style: formatting changes without behavior impact
- chore: other maintenance changes

Choose exactly ONE type representing the primary change.

### 4. Choose the scope

Use a scope when a clear module, component, or area
of the application is affected.

Examples:

- feat(auth): ...
- fix(api): ...
- refactor(database): ...

Prefer existing project naming conventions.

If changes span unrelated areas or no meaningful
scope exists, omit the scope.

### 5. Write the message

Format:

<type>(<optional-scope>): <description>

Requirements:

- Use imperative mood.
- Start the description with a lowercase verb.
- Do not end the description with a period.
- Keep the subject concise, ideally under 72 characters.
- Be specific about what changed.
- Prefer describing behavior over implementation details.
- Avoid vague words like "update", "changes", or "improvements"
  unless qualified with concrete details.
- Do not mention file names unless essential.
- Do not invent reasons or impact.

For changes requiring explanation, add a short body
separated from the subject by a blank line.

Use a breaking-change marker and BREAKING CHANGE footer
only when an actual incompatible change is verified.

### 6. Output rules

CRITICAL:

- Output exactly ONE commit message.
- Never provide multiple candidates.
- Never explain why the message was chosen.
- Never add introductory text.
- Never include headings or Markdown code fences.
- Never add quotation marks around the message.
- Never include a summary outside the commit message.
- Do not run git add or git commit.
- Do not modify repository files.

The entire response must be directly copy-pasteable
as a Git commit message.

If no changes exist, output exactly:

No changes to commit.
