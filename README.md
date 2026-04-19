# AI Development Workflow

A lightweight AI workflow for software developers who want better reasoning, fewer mistakes, and a repeatable process across projects.

This setup is designed for teams and solo developers who use:
- Cursor Agent
- Claude CLI
- OpenCode

## Core idea

Use the strongest model for planning.

Use a low-cost model for implementation.

Keep changes small.

Review diffs before merging.

## Why this workflow exists

Most AI coding workflows become noisy because too many tools are used at the same time, with no clear handoff.

This workflow solves that by giving each tool a fixed role:
- **Claude / Opus** for planning
- **OpenCode low-cost models** for implementation and review
- **You** for validation, testing, and final decisions

## Principles

- Plan before code.
- Implement one step at a time.
- Prefer the smallest useful patch.
- Do not refactor outside the task.
- Review diffs, not entire codebases.
- Keep architecture decisions human-owned.

## Recommended roles

### Claude CLI
Use it for:
- understanding the task
- mapping impacted files
- comparing 2 implementation options
- producing an implementation plan
- reviewing high-risk diffs

### OpenCode
Use it for:
- executing a single planned step
- writing small tests
- reviewing diffs
- checking conventions
- running low-cost iterations

### Cursor Agent
Use it for:
- quick local edits
- small fixes
- interactive debugging
- fast code navigation
- applying the smallest patch

## Workflow

1. Write a short task brief.
2. Ask Claude to create a plan without modifying code.
3. Save that plan in a markdown file.
4. Ask OpenCode to implement one step only.
5. Review the diff.
6. Run tests, lint, and type checks.
7. Repeat for the next step.

## Files

- `docs/workflow.md`: the full workflow
- `docs/prompts.md`: prompt templates
- `AGENTS.md`: project rules for consistent execution

## Goal

The goal is not to let AI code everything.

The goal is to use AI to think better, reduce mistakes, and move faster without losing control.
