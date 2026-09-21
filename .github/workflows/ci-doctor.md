---
on:
  workflow_run:
    workflows: ["Dragon CI/CD Pipeline"]
    types: [completed]

if: ${{ github.event.workflow_run.conclusion == 'failure' }}

engine: copilot

permissions:
  contents: read
  actions: read
  issues: read

safe-outputs:
  create-issue:
    title-prefix: "[CI Doctor] "
    labels: [ci-failure]
---

# CI Failure Doctor

The "Dragon CI/CD Pipeline" workflow just failed.

Investigate the failed run and create an issue that contains:

1. **What failed**: which job and which step
2. **Why it failed**: the root cause in plain English, based on the logs
3. **How to fix it**: the exact change needed, shown as a small code snippet

Keep it short and beginner-friendly.