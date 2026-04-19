# Workflow

## Overview

This workflow is designed to keep AI useful, cheap, and reliable.

Instead of asking one model to do everything, we split the work into three phases:
1. planning
2. implementation
3. review

## The operating model

- **Claude / Opus** creates the plan
- **OpenCode low-cost models** implement the plan
- **You** validate each step

This avoids wasting expensive requests on routine implementation and reduces the risk of low-cost models inventing architecture.

## Step 1 — Write a short brief

Before using any model, write a short brief.

Template:
- task
- goal
- constraints
- affected area
- risks
- expected result

Example:

```md
Task: Add validation to the Drupal form submit handler.

Goal: Reject invalid payloads before service execution.

Constraints:
- minimal changes
- no unrelated refactor
- keep existing conventions

Affected area:
- form submit handler
- validation service
- related tests

Risks:
- breaking existing submissions
- missing edge cases

Expected result:
- invalid input is rejected
- tests cover success and failure cases
```

## Step 2 — Ask Claude to plan

Use Claude in planning mode.

Important:
- do not ask for implementation yet
- do not ask for refactoring yet
- do not ask for a complete feature in one shot

Expected output:
- task understanding
- likely impacted files
- risks
- implementation steps
- testing strategy
- acceptance criteria

## Step 3 — Save the plan

Save the plan in a file.

Recommended path:
- `docs/ai/plan.md`
- or `docs/tasks/<task-name>.md`

The plan should contain:
- objective
- constraints
- files involved
- ordered steps
- tests
- risks

## Step 4 — Implement with OpenCode

Ask OpenCode to read the saved plan.

Then ask it to implement **one step only**.

Rules:
- minimal changes
- no architecture redesign
- no cosmetic refactor
- list touched files
- add tests when needed

## Step 5 — Review the diff

Before moving to the next step:
- inspect the diff
- verify the scope
- check tests
- confirm alignment with the plan

You can use OpenCode for a low-cost review or use Claude again for a deeper review on risky changes.

## Step 6 — Validate locally

Always run the project checks before continuing:
- tests
- linter
- type checker
- static analysis if available

Do not trust a patch just because the code looks correct.

## Step 7 — Repeat

Move to the next step only when the current one is:
- implemented
- reviewed
- validated

Repeat until the plan is complete.

## Recommended task sizing

Use this workflow only if the task can be broken into small steps.

Good task size:
- one endpoint
- one handler
- one service change
- one component update
- one test suite update

Bad task size:
- "implement the whole feature"
- "refactor the entire module"
- "rewrite everything"

## Default rules

- Keep diffs small.
- One step at a time.
- No hidden refactors.
- No architecture decisions by cheap models.
- Expensive models plan; cheap models execute.
- Humans approve.

## Best use cases

This workflow works especially well for:
- backend tasks
- Drupal feature work
- React and TypeScript changes
- bug fixing
- test creation
- safe refactors

## Final note

This is not a fully autonomous agent system.

It is a controlled engineering workflow that uses AI where it helps most:
- reasoning
- execution
- review
