# AGENTS.md

## Purpose

This repository uses AI as a controlled engineering assistant.

AI should help with:
- reasoning
- small implementation steps
- diff review
- test suggestions

AI should not make uncontrolled architecture changes.

## Global rules

- Always start from the task brief.
- If a plan file exists, follow it.
- Implement one step at a time.
- Prefer the smallest useful patch.
- Do not perform unrelated refactors.
- Do not rename or move files unless explicitly required.
- Keep the existing project style and structure.
- Explain touched files after each implementation.
- Suggest tests when changing behavior.
- Stop when the requested step is complete.

## Planning rule

When asked to analyze a task:
- explain the problem
- identify impacted files
- propose a small ordered plan
- describe risks
- define a test strategy
- do not modify code yet

## Implementation rule

When asked to implement:
- work from the existing plan
- implement only the requested step
- keep changes local
- avoid over-engineering
- preserve backward compatibility unless told otherwise

## Review rule

When asked to review:
- compare the diff against the plan
- identify bugs
- identify missing edge cases
- identify missing tests
- identify scope drift
- avoid cosmetic suggestions unless they block clarity

## Output format

After implementation, always provide:
- summary of what was changed
- list of touched files
- tests to run
- known risks or follow-up items

## Human ownership

Architecture, security, production risk, and merge decisions stay human-owned.
