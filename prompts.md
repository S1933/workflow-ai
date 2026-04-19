# Prompt Templates

## 1. Planning prompt for Claude

```text
Analyze this task without modifying code.

Task:
[describe the task]

I only want:
1. understanding of the problem
2. impacted files
3. risks
4. an implementation plan in ordered steps
5. a test strategy
6. acceptance criteria

Constraints:
- keep changes minimal
- respect existing project conventions
- avoid over-engineering
- do not implement anything yet
```

## 2. Save-the-plan format

```md
# Plan — [task name]

## Objective
...

## Constraints
...

## Files involved
- ...
- ...

## Steps
1. ...
2. ...
3. ...

## Tests
- ...
- ...

## Risks
- ...
- ...
```

## 3. Implementation prompt for OpenCode

```text
Read docs/ai/plan.md.

Implement only step 1.

Constraints:
- minimal changes
- no unrelated refactor
- respect repository conventions
- add or update tests when needed
- list modified files
- do not implement future steps
```

## 4. Diff review prompt

```text
Review this diff against docs/ai/plan.md.

Find:
- possible bugs
- missing edge cases
- regressions
- missing tests
- deviations from the plan

Do not suggest cosmetic refactors.
Do not rewrite code outside the scope.
```

## 5. Small patch prompt for Cursor Agent

```text
Help me produce the smallest useful patch for this task.

Context:
- project: [name]
- stack: [Drupal / PHP / Go / React / TypeScript]
- goal: [goal]
- constraints: minimal changes, no unrelated refactor

Output:
- proposed patch
- files touched
- risks
- tests to run
```

## 6. Final review prompt for Claude

```text
Review this final diff as a senior engineer.

Check:
- correctness
- scope control
- architecture fit
- test coverage
- regression risk

Classify findings as:
- blocking
- important
- suggestion
```
