---
name: developing
description: Use when implementing, modifying, running, or evaluating a non-trivial software or research task that needs a proportionate plan, verification, state recording, or a clear handoff.
---

# Janus Developing

## Core loop

Use one workflow for coding and research, scaled to risk:

```text
CONTEXT -> optional BRAINSTORM -> WORKING PLAN -> SELF REVIEW
-> BUILD -> VERIFY -> INSPECT DIFF -> RECORD -> REPORT
```

The plan is a thinking aid, not a second deliverable. Keep it proportional to uncertainty, impact, and reversibility.

## Work with other skills

Janus may coexist with specialized skills. If another skill is explicitly invoked, or has already produced an authoritative upstream artifact such as a PRD, API contract, dataset protocol, or experiment brief:

1. Read the relevant output and identify its current decisions, constraints, and open risks.
2. Do not duplicate the upstream skill's discovery, product definition, or domain procedure.
3. Continue from the Janus stage that remains: Working Plan, Build, Verify, Record, or Report.
4. Treat a real contradiction as a reason to pause and resolve it; do not silently overwrite the upstream source of truth.

No Janus stage depends on a particular external skill. If no upstream artifact exists, use the local context and the optional `brainstorming` stage; do not stop to request installation of another skill.

## Choose the risk level

### Trivial

Use for obvious, local, reversible edits.

```text
inspect -> change -> verify -> diff -> record if meaningful -> report
```

### Normal

Use for a focused feature, analysis, or experiment.

```text
inspect -> short Working Plan -> self-review -> build/run
-> verify -> inspect diff or artifacts -> update project state -> report
```

### High risk

Use when the change is broad, difficult to reverse, security-sensitive, algorithmically central, data-destructive, or experimentally consequential.

```text
inspect -> brainstorm -> detailed Working Plan -> self-review
-> isolate if useful -> build/run -> stronger tests or review
-> verify -> inspect diff/artifacts -> update project state -> report
```

Do not upgrade a task merely because a heavier workflow exists.

## Working Plan

Use one concise document or in-thread section that combines design and execution:

```markdown
# Working Plan

## Goal
## Context / Constraints
## Design
## Scope
## Changes
1. ...
2. ...
## Verification
```

Omit sections that do not help this task. A trivial change may need only two sentences. A high-risk change may need alternatives, compatibility, migration, rollback, and risks.

## Self-review

Before substantial implementation, check:

- Does this solve the requested problem?
- Is anything unnecessary or over-generalized?
- Am I changing more than the scope requires?
- Did I miss compatibility, data, environment, or research risks?
- Is the planned verification strong enough for the claim?

Revise the Working Plan in place. Do not create a separate review document or default subagent review.

## Build and verify

Inspect the real files and existing state before editing. Keep changes narrow and follow local conventions.

- Use test-first development when a stable reusable component, core behavior, or regression risk justifies it.
- For a bug, prefer a regression test; for a research prototype, the experiment or evaluation may be the relevant verification.
- Use a worktree only when isolation has real value.
- Use subagents or formal review only for independent work, large diffs, critical algorithms, public APIs, migrations, security-sensitive changes, release work, or material uncertainty.

Always run the relevant command, test, or experiment; read its output; and inspect the final `git diff`. Never convert "looks right" into a success claim.

For research, report these separately:

- code works;
- experiment ran;
- hypothesis is or is not supported by the result.

## Record project state

After substantive work:

```text
VERIFY -> INSPECT DIFF -> UPDATE LOG -> SYNC TODO -> REPORT
```

Prefer existing project logs when they already exist. Otherwise, use:

- `LOG.md` for durable decisions, results, evidence, failed approaches, discoveries, and constraints that help a future session;
- `TODO.md` for the current state, completed items, invalidated ideas, priorities, and the next useful action.

Do not write a step-by-step activity diary.

## Report

Explain the result in four parts:

1. **What we did** - the concrete change or experiment.
2. **Why** - the selected design and important tradeoffs.
3. **Verification / Result** - commands, tests, outputs, or experiment evidence.
4. **What remains** - limitations, risks, and the next action.

Keep technical details as supporting evidence, not as a substitute for explanation.
