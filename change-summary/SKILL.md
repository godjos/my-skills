---
name: change-summary
description: Create concise changelogs, release notes, README/docs updates, weekly engineering summaries, or PR-ready change summaries from recent git diffs and code inspection. Use when the user asks to summarize recent work, document yesterday/today's changes, prepare release notes, or update docs after implementation.
---

# Change Summary

Use this skill when code already changed and the user wants a practical written artifact.

## Workflow

1. **Define the range**
   - Prefer the user's range: branch, PR, commit, "today", "yesterday", or unstaged diff.
   - If no range is given, inspect `git status`, `git diff --stat`, and recent commits.

2. **Read the evidence**
   - Review changed files and nearby context.
   - Identify user-visible behavior, operational impact, config changes, tests, and docs impact.
   - Ignore formatting-only churn unless it affects users or maintainers.

3. **Choose the artifact**
   - Changelog/release notes: user-facing changes, fixes, upgrade notes, known risks.
   - README/docs update: exact commands, env vars, behavior, and examples verified from code.
   - Weekly/engineering summary: purpose and effect first, technical details second.
   - PR summary: problem, approach, tests, risk.

4. **Write with evidence**
   - Do not invent motivation or results.
   - Mention verification only when a command was actually run or existing output is present.
   - Keep prose direct; no inflated claims.

5. **Verify**
   - For docs with commands/config, check the command or code path when feasible.
   - For release notes, verify referenced files or commits exist.

## Output

Default structure:

- **What changed**
- **Why it matters**
- **Verification**
- **Upgrade/config notes** if applicable

When editing repository docs, match the existing file style and keep the diff small.
