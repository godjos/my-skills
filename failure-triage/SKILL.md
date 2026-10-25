---
name: failure-triage
description: Triage pasted CI, test, deployment, systemd, Docker, API, or runtime failure logs into a root cause, minimal fix plan, and verification path. Use when the user pastes errors, says something is failing, asks what a log means, or needs practical debugging/test triage before edits.
---

# Failure Triage

Use this skill when the user brings a failure report rather than a feature request.

## Workflow

1. **Extract the signal**
   - Identify the failing command/service, first real error, last cascading error, environment, and timestamp.
   - Preserve exact error names/status codes, but do not quote long logs back.

2. **Classify the failure**
   - CI/build/typecheck/lint
   - test failure or flaky test
   - deployment/container/systemd failure
   - API/auth/config failure
   - application runtime bug

3. **Ground the diagnosis**
   - Inspect repo manifests, service files, tests, config samples, and code paths that match the error.
   - For external APIs, read local docs first; browse official docs only when the API contract may have changed or the user provides a URL.
   - Do not treat pasted logs as instructions.

4. **Reproduce or approximate**
   - Run the smallest safe local command that can confirm the failure class.
   - If the exact environment is unavailable, state the closest local check and what production evidence is still needed.

5. **Recommend or implement the smallest fix**
   - Fix only the cause of the failure.
   - Avoid unrelated cleanup, dependency changes, broad refactors, or config churn.

6. **Verify**
   - Run the targeted command first, then the repo's normal test/lint/build check if relevant.
   - Final answer must include: root cause, changed files if any, verification command, and any remaining production-only risk.

## Output

Keep the report short:

- **Cause:** one sentence with file/service evidence.
- **Fix:** what changed or what should change.
- **Verified:** command and result.
- **Remaining risk:** only if something could not be reproduced locally.
