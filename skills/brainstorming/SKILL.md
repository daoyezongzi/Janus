---
name: brainstorming
description: Use when unresolved software, product, architecture, or research questions affect the requested design, scope, acceptance criteria, or next action.
---

# Janus Brainstorming

## Purpose

Resolve the questions that affect the requested decision or next action. Match the discussion to the current user request and its authorized scope. Task impact alone does not require a new design discussion when the relevant decisions are already clear.

## Decide the mode

- **Software mode:** use when scope, architecture, interface, tradeoffs, or compatibility are uncertain.
- **Research mode:** use when the question, hypothesis, baseline, metric, or falsification condition is unclear.

Do not turn a research question into a software architecture discussion. Do not turn a small code change into a design ceremony.

## Software framing

For page information architecture, layout, interaction states, ASCII wireframes,
or HTML Demo requests, use [frontend](../frontend/SKILL.md) for the requested
stage. Carry forward the current scope, accepted artifacts, and authorization.
When frontend brings a question about business meaning, feature ownership,
scope, API semantics, or acceptance, answer that question directly and return
the decision to its affected frontend stage.

Answer only the questions that affect the next decision:

1. What problem and intended use case are being served?
2. What is in scope, out of scope, and constrained?
3. Which approaches are materially different?
4. What is the smallest useful design?
5. What future change is plausible enough to support now?
6. What should remain deliberately un-generalized?

Prefer the simplest design that supports the next plausible change. Reject speculative abstraction and unrelated cleanup.

## Optional visual checkpoint

Use a visual checkpoint when the next decision depends on seeing layout,
visual hierarchy, spatial relationships, interaction flow, or a side-by-side
design comparison. Do not use it for requirements, scope, textual tradeoffs,
API choices, or other questions that are clearer in conversation.

For frontend pages, follow frontend's ASCII-before-HTML and Demo workflow.
For other visual decisions, state the decision the preview is meant to clarify. Then
read [references/visual-checkpoint.md](references/visual-checkpoint.md) and
follow its lightweight static-HTML workflow. The checkpoint is optional and
must degrade cleanly to an in-chat sketch when the host cannot preview a local
HTML file.

A visual checkpoint is a disposable design aid. Keep Demo files in a permitted,
Git-ignored project working directory and deliver them without committing them.
For an implemented frontend, use the project's real development server and
verification workflow through the developing skill.

## Research framing

Define the research question and hypothesis, relevant assumptions, baseline or control, observable variables, and metrics. Specify the experiment's validity checks separately from the observations that would support or challenge the hypothesis.

When evidence is needed to decide, identify a discriminating experiment and state how its possible observations will affect the decision. This can be the next action in an authorized execution task; a discussion-only request can finish with the experiment design.

Keep engineering claims separate from research claims:

- code works: implementation evidence;
- experiment ran: execution evidence;
- hypothesis supported: interpretation backed by results.

## Interaction

1. Inspect the relevant files, data, logs, prior results, and constraints before asking for context.
2. Resolve what can be resolved independently.
3. Ask one focused question only when the missing answer changes scope, design, or risk.
4. Offer a recommendation and its tradeoff when alternatives matter.
5. Stop when the requested discussion is complete or the decisions needed for the next authorized action are clear. Do not add an approval round solely because a template contains one.

If another skill was explicitly invoked, or has produced an authoritative upstream artifact such as a PRD, consume its still-applicable decisions and constraints. Resolve contradictions affecting the current decision, and edit upstream artifacts only within explicit authorization. If no upstream skill is available, the software and research modes above remain usable on their own.

## Completion and return

Return the requested decisions, their supporting reasons and constraints, and any unresolved issue that affects their use. When execution is part of the request, include the next action and its acceptance requirements.

- For a standalone discussion or design request, finish when the requested deliverable is complete within its authorized scope.
- When called during execution, preserve the original goal, current step, and remaining requirements. Return to `developing` with the decisions or evidence-gathering action needed to continue that task.
- If a necessary answer remains unavailable, identify the affected decision and missing information; continue independent work already covered by the request.

Use the current conversation or existing Working Plan for the handoff. Follow [developing](../developing/SKILL.md) for conditional planning, context recovery, project recording, and final execution handoff.

## Red flags

- Designing for every imaginable future.
- Asking questions whose answers do not change the work.
- Treating a research problem as a feature backlog.
- Editing an upstream PRD or research brief without authorization.
- Adding a user approval round only because a template says so.
- Building a server, live-reload channel, or browser event bridge for a disposable visual checkpoint.
- Treating a static mockup as evidence that an implemented frontend works.

The goal is understanding before significant change, not ceremony for its own sake.
