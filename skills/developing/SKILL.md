---
name: developing
description: Use when implementing, modifying, running, or evaluating a non-trivial software or research task that needs proportionate planning, verification, state recording, context recovery, or a clear handoff.
---

# Janus Developing

## Core loop

Use one workflow for coding and research, scaled to risk:

```text
CONTEXT -> optional BRAINSTORM -> WORKING PLAN when warranted -> SELF REVIEW
-> BUILD -> VERIFY -> RECORD -> INSPECT DIFF -> COMMIT WHEN APPLICABLE -> REPORT
```

The plan is a thinking and recovery aid, not a second deliverable. Use it when task size, uncertainty, risk, or expected duration justifies it, and keep its detail proportional to uncertainty, impact, and reversibility.

This file is the normative source for Janus execution rules. Keep summaries elsewhere concise and refer here instead of duplicating conditional details.

## Durable plans and context recovery

Inspect enough read-only context to make a grounded plan before substantial implementation.

- For a broad, long-running, high-risk, or multi-step task likely to cross a context or session boundary, persist the Working Plan in the project's existing plan location. If none exists, use `docs/plans/YYYY-MM-DD-<task>.md`.
- A fresh execution conversation does not by itself require discovering, scanning for, or reading a plan. Read a known plan when the user points to it, asks to execute or continue plan-backed work, or the retained task context identifies it as the source of truth.
- Use the task's structured plan mechanism when available to mirror the current execution steps and statuses; the plan file remains the durable statement of intent and verification.
- Within an already plan-backed task, after conversation compaction or an explicit request to resume, first check whether the goal, next step, completed work, and constraints are still clear from the retained context and structured plan. If they are clear, continue without reloading the file.
- If any of that state is unclear or contradictory, stop and recover: re-read the known relevant plan, inspect `git status` and the relevant diff or artifacts, consult `LOG.md` / `TODO.md` when present, reconcile actual progress, then update the structured plan before continuing. Do not guess among multiple plans; ask for direction when the intended plan cannot be identified safely.
- If no durable plan exists, recover from the latest request, retained summary, repository state, and project records; create a plan only if the remaining work now warrants one.
- Do not re-read a plan on every turn, and do not search for one solely because a new conversation started. Compaction inside a plan-backed task is a reason to check clarity, not an unconditional reload trigger.
- If scope or evidence changes the approach, revise the durable plan instead of silently abandoning it.

Small, obvious, reversible work does not need a plan solely for ceremony.

## Documentation discipline

Apply these rules to documentation and process side effects, not to the code, tests, configuration, data, or requested deliverables needed to complete the task.

- A warranted durable Working Plan is an intentional exception: reuse the project's plan location or use `docs/plans/YYYY-MM-DD-<task>.md` as described above.
- After ordinary substantive work, record durable execution state in the project's existing log and TODO surfaces. If none exist, use `LOG.md` and `TODO.md`. Do not create standalone process files such as `NOTES.md`, `ANALYSIS.md`, `REVIEW.md`, `SUMMARY.md`, or ad hoc handoff documents merely to narrate the work. Keep transient reasoning and scratch notes in the conversation, structured plan, or a temporary location outside the project tree.
- Create or edit other project documentation only when it is a requested deliverable, is necessary to keep a task-owned public contract accurate, or is the warranted durable plan above. Do not duplicate information that belongs in an existing document, log, or TODO.
- When a new project document is warranted, reuse the project's existing categorized documentation structure. If no convention exists, place it in the smallest fitting `docs/<category>/` location and create only the category the task needs. Do not build a speculative documentation tree or reorganize existing files without a separate reason and authorization.
- Preserve conventional root or tool-required locations such as `README.md`, `LICENSE`, `CHANGELOG.md`, `CONTRIBUTING.md`, `AGENTS.md`, project logs and TODOs, and files whose path is part of a tool contract.
- Treat a PRD, proposal, project brief, product plan, or other upstream planning artifact as read-only unless the user explicitly asks to edit that artifact. A request to implement or continue its plan does not grant permission to rewrite it. If implementation evidence contradicts it, report the conflict and record the actionable state in the log or TODO rather than silently changing the artifact.

## Work with other skills

Janus may coexist with specialized skills. If another skill is explicitly invoked, or has already produced an authoritative upstream artifact such as a PRD, API contract, dataset protocol, or experiment brief:

1. Read the relevant output and identify its current decisions, constraints, and open risks.
2. Do not duplicate the upstream skill's discovery, product definition, or domain procedure.
3. Continue from the Janus stage that remains: Working Plan, Build, Verify, Record, Commit, or Report.
4. Treat a real contradiction as a reason to pause and resolve it; do not silently overwrite the upstream source of truth.

No Janus stage depends on a particular external skill. If no upstream artifact exists, use the local context and the optional `brainstorming` stage; do not stop to request installation of another skill.

## Choose the risk level

### Trivial

Use for obvious, local, reversible edits.

```text
inspect -> change -> verify -> record if meaningful -> diff
-> commit when applicable -> report
```

### Normal

Use for a focused feature, analysis, or experiment.

```text
inspect -> short Working Plan -> self-review -> build/run
-> verify -> update project state -> inspect diff or artifacts
-> commit when applicable -> report
```

### High risk

Use when the change is broad, difficult to reverse, security-sensitive, algorithmically central, data-destructive, or experimentally consequential.

```text
inspect -> brainstorm -> detailed Working Plan -> self-review
-> isolate if useful -> build/run -> stronger tests or review
-> verify -> update project state -> inspect diff/artifacts
-> commit when applicable -> report
```

Do not upgrade a task merely because a heavier workflow exists.

## Working Plan

When a plan is warranted, use one structured task plan, concise document, or durable plan file that combines design and execution:

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

Omit sections that do not help this task. A focused normal task may need only a short in-thread or structured plan. A large or high-risk change may need a durable file covering alternatives, compatibility, migration, rollback, and risks.

## Self-review

Before substantial implementation, check:

- Does this solve the requested problem?
- Is anything unnecessary or over-generalized?
- Am I changing more than the scope requires?
- Did I miss compatibility, data, environment, or research risks?
- Is the planned verification strong enough for the claim?

Revise the Working Plan in place. Do not create a separate review document or default subagent review.

## Build and verify

Inspect the real files and existing state before editing. In a Git worktree, inspect the existing status first and keep task changes separate from prior or unrelated changes. Keep changes narrow and follow local conventions.

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
VERIFY -> UPDATE LOG -> SYNC TODO -> INSPECT DIFF
-> COMMIT WHEN APPLICABLE -> REPORT
```

Prefer existing project logs when they already exist. Otherwise, use:

- `LOG.md` for durable decisions, results, evidence, failed approaches, discoveries, and constraints that help a future session;
- `TODO.md` for the current state, completed items, invalidated ideas, priorities, and the next useful action.

Do not write a step-by-step activity diary.

## Commit when applicable

If a task changes files in a Git repository, commit the task-owned changes after verification unless the user opts out or they cannot be isolated safely.

- Stage only task-owned changes and inspect what will be committed. Never include pre-existing or unrelated work.
- A trivial task usually needs one commit. Split only when independently useful, verified changes make separate commits clearer or safer.
- Use a clear commit message and never push automatically.
- Check repository status once after committing. Report commit IDs and explain any uncommitted remainder.

## Report

Explain the result in four parts:

1. **What we did** - the concrete change or experiment.
2. **Why** - the selected design and important tradeoffs.
3. **Verification / Result** - commands, tests, outputs, experiment evidence, and commit IDs when created.
4. **What remains** - limitations, risks, uncommitted remainder, and the next action.

Keep technical details as supporting evidence, not as a substitute for explanation.
