---
name: developing
description: Complete software or research execution tasks with proportionate planning, evidence-based verification, context recovery, and a complete handoff. Use when implementing, running, evaluating, or continuing work.
---

# Janus Developing

## Own the complete execution task

Keep the user's complete objective, the current step, and remaining requirements in view while implementing, running, or evaluating work. This file is the normative source for Janus execution rules; summaries and other skills refer here for shared execution and handoff rules.

1. Inspect the current files and evidence; identify the requested deliverable, permitted changes, and acceptance requirements.
2. Resolve decisions that affect the next action, and make a Working Plan when useful.
3. Check the proposed work for scope, compatibility, and adequate verification before substantial changes.
4. Implement or run the current step and examine its actual result.
5. Use the result to continue, diagnose an anomaly, or reconsider a decision as described below.
6. Check the complete request against current evidence, then perform applicable recording, artifact inspection, commit, and reporting.

When calling `brainstorming` or `debugging`, preserve the parent task's objective, affected step, and remaining work in the conversation or existing plan. On return, incorporate the result and resume the affected step. A local repair completes only the requirements its evidence supports.

For a standalone discussion or diagnosis request, the requested analysis can be the deliverable. Carry out implementation only within the user's authorized scope.

## Choose measures from task conditions

| Condition | Measure |
| --- | --- |
| An unresolved decision affects scope, design, acceptance, or the next action | Use `brainstorming` for that decision. |
| Work concerns web pages, information architecture, layout, frontend interactions, or page verification | Use [frontend](../frontend/SKILL.md) for the relevant domain stages and evidence. |
| Steps depend on one another, or design and verification need an explicit arrangement | Use a proportionate Working Plan. |
| Duration, task span, or expected session boundaries make recovery valuable | Persist the Working Plan. |
| Failure has substantial impact, recovery is difficult, or core behavior or research conclusions are at stake | Strengthen planning, preconditions, verification, and appropriate independent review. |
| Concurrent work needs separate change or execution state | Use a worktree or other suitable workspace isolation. |
| Subtasks can obtain evidence and be accepted independently | Consider subagents with defined handoffs. |
| An observed failure or anomaly needs explanation | Use `debugging` with the reproduction and actual evidence. |

Conditions can apply together. An approved high-impact design still warrants suitable planning and verification; brainstorming is triggered by a specific unresolved decision. An obvious local edit can proceed directly through inspection, change, and relevant verification.

## Current request and task state

| Information | Responsibility |
| --- | --- |
| Current effective user request | Defines the objective, scope, constraints, and deliverables; earlier requirements remain effective unless changed. |
| Upstream PRD, proposal, or experiment brief | Supplies applicable domain requirements and accepted decisions; editing requires explicit authorization. |
| Working Plan | Records execution choices, verification arrangements, and decisions needed for subsequent actions. |
| Current files, data, and run results | Establish actual progress and which claims the evidence supports. |
| LOG | Retains useful conclusions and evidence locations. |
| TODO | Tracks remaining work reconciled with current requirements and evidence. |

When the user changes scope, stop superseded steps, identify affected artifacts and checks, and update permitted task records. Read current file contents before editing and preserve the user's intervening changes. A difference between a plan and a file requires checking actual progress. Ask for clarification only when a necessary decision cannot be resolved from available context.

## Working Plan

Use one proportionate plan combining design and execution. A focused task can use the conversation or the host's structured plan. When persistence is warranted, use the project's existing plan location, or `docs/plans/YYYY-MM-DD-<task>.md` if none exists:

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

Include the sections needed for the task. Consequential work may require compatibility, migration, recovery, and risk considerations. Update the execution plan when requirements or evidence change the approach, within the permitted writing scope.

### Context recovery

Read a known plan when the user points to it, requests plan-backed execution or continuation, or retained context identifies it as the task's plan. A new conversation alone does not require plan discovery.

After compaction or resumption, check the objective, constraints, last confirmed result, next action, running jobs, and outstanding verification. Continue when the retained information supports the next action. Read current files, process state, or outputs when the next action depends on state that may have changed.

If progress is unclear or contradictory, re-read the known plan, inspect relevant files, Git status and diff where applicable, artifacts, and existing LOG/TODO entries. Reconcile progress before proceeding and update the host's structured task state when available. If no plan exists, recover from the current request, retained context, and actual project state; persist a plan only when the remaining work warrants one. Ask when the intended task cannot be identified reliably.

## Self-review

Before substantial implementation, check:

- Does this solve the requested problem?
- Is anything unnecessary or over-generalized?
- Am I changing more than the scope requires?
- Did I miss compatibility, data, environment, or research risks?
- Is the planned verification strong enough for the claim?

Update the existing plan when this check changes an execution decision. Keep the review in the conversation or existing plan.

## Build and verify

Inspect real files and existing state before editing. In a Git repository, inspect status first and keep task changes separate from prior or unrelated work. Follow local conventions and the requested scope.

- Use test-first development when a stable reusable component, core behavior, or regression risk justifies it.
- For a bug, prefer a regression test; for a research prototype, the experiment or evaluation may be the relevant verification.
- Select checks that examine the requested behavior using justified inputs and expected results.

Run the relevant command, test, experiment, or source check and read its actual output. Link completion claims to the current artifact and the requirements the evidence covers. After changing related code, data, dependencies, configuration, or evaluation methods, rerun affected checks. Evidence for unaffected behavior can remain valid. When only project records change, verify their consistency with the evidence. Inspect the final Git diff where applicable.

### Act on verification results

| Result | Next action |
| --- | --- |
| The step satisfies its requirements and work remains | Continue the next part of the original task. |
| The observation is expected by the reproduction or experiment | Interpret it according to the diagnostic or experimental question. |
| An unexplained failure or anomaly occurs | Use `debugging` with expected behavior, actual evidence, reproduction conditions, and the affected step. |
| Evidence changes the method needed | Update the execution arrangement; use `brainstorming` for unresolved choices. |
| Required information or execution conditions are unavailable | Continue independent authorized work and identify the blocked requirement and missing condition. |
| All applicable requirements have sufficient evidence | Complete the applicable recording and handoff. |

### Research completion

Define the experiment's validity conditions, the question to answer, and the evidence needed for the conclusion. Record enough code, input, environment, command, configuration, and output information to identify and reproduce a claimed result; include randomness settings and repetitions when relevant.

Once validity checks pass, support for a hypothesis, evidence against it, or a well-supported limit on what can be inferred can be a research result. Completion depends on the requested question and deliverables. A request to attain a performance target remains governed by that target. Change evaluation criteria only with a requirements-based or measurement-based justification.

Report implementation validity, experiment execution, and hypothesis support separately. Required checks that could not be completed remain unverified.

## Work with specialists and subagents

Use an explicitly invoked professional skill or applicable upstream artifact for its domain methods and accepted decisions. Inspect its output and evidence, then continue the remaining work. Resolve contradictions that affect the current operation while continuing independent authorized work. When no upstream artifact is available, use local context and the appropriate Janus skill.

For frontend work, retain the complete execution objective while using
frontend's page inspection, audit, design, ASCII-before-HTML Demo, and real
application verification methods. Consume accepted designs and prior stage
artifacts. Return diagnostic findings to the affected page operation, then
finish its remaining flows and related pages. A requested audit or preview
finishes at its authorized stage.

Keep Demo HTML, screenshots, and preview archives in a permitted Git-ignored
project working directory. Deliver them as files or access links. Formal
project changes follow the recording and commit rules below; Demo artifacts
are excluded from commits even when the user wants to retain them.

For each delegated subtask, specify the question, necessary facts, permitted file changes, dependencies, expected artifact, and acceptance evidence. Ask for checkable results, verification performed, and remaining uncertainty. The lead agent checks consequential conclusions and integrated artifacts with effort proportional to their impact. Preserve the complete task's outstanding requirements during delegation.

## Documentation discipline

Documentation and process steps follow the task's permitted writing scope. For read-only work, retain progress in the conversation or the host's structured task state and deliver the analysis there.

- Use existing project records for durable decisions, results, and remaining work. Keep transient reasoning in the conversation or an allowed scratch location.
- Create project documentation when it is a requested deliverable, keeps a task-owned public interface accurate, or is a warranted durable Working Plan. Reuse existing content and link to its evidence.
- Reuse the project's categorized documentation structure, or the smallest fitting `docs/<category>/` location. Preserve conventional root and tool-required paths such as `README.md`, `LICENSE`, `AGENTS.md`, LOG, and TODO.
- Treat upstream PRDs, proposals, project briefs, and experiment briefs as read-only unless the user explicitly authorizes editing the artifact. Executing their plans does not grant editing permission. Resolve a consequential conflict against the current request and record the actionable state where writing is permitted.

## Record project state

For writable work that produces reusable decisions, results, or remaining actions, update the existing project log and TODO; use `LOG.md` and `TODO.md` if suitable records do not exist. Reference evidence with enough version or run information to identify it. Keep current task status in TODO and enduring conclusions in LOG.

When a specialist or Janus skill was called within an execution task, return its results to the lead execution context for final recording and reporting. Record meaningful project state once, then inspect the applicable diff or artifacts. A standalone read-only result is delivered in the conversation.

## Commit when applicable

If a task changes files in a Git repository, commit the task-owned changes after verification unless the user opts out or they cannot be isolated safely.

- Stage only task-owned changes and inspect what will be committed. Never include pre-existing or unrelated work.
- Exclude Demo, HTML preview, screenshot, and demonstration archive files. Check their Git ignore status before creating them.
- A trivial task usually needs one commit. Split only when independently useful, verified changes make separate commits clearer or safer.
- Use a clear commit message. Push only when the user authorizes it, and satisfy any requested review condition before committing or pushing.
- Report the local commit result. Treat push as a separate operation requiring the user's explicit authorization.
- Check repository status once after committing. Report commit IDs and explain any uncommitted remainder.

## Report

Report the complete request's outcome with the following information as relevant:

1. **What we did** - the concrete change or experiment.
2. **Why** - the selected design and material tradeoffs.
3. **Verification / Result** - commands, tests, outputs, experiment evidence, and commit IDs when created.
4. **What remains** - limitations, risks, uncommitted remainder, and the next action.

Claim completion only for requirements supported by current evidence. State material limitations and remaining work explicitly, and keep the report proportional to the task.
