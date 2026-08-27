---
name: brainstorming
description: Use when a software, research, experiment, product, or architecture task has unresolved uncertainty, meaningful design choices, competing hypotheses, or scope decisions that make direct execution risky.
---

# Janus Brainstorming

## Purpose

Use the smallest amount of structured thinking needed to make the next action clear. Skip this skill for obvious, mechanical, reversible edits.

## Decide the mode

- **Software mode:** use when scope, architecture, interface, tradeoffs, or compatibility are uncertain.
- **Research mode:** use when the question, hypothesis, baseline, metric, or falsification condition is unclear.

Do not turn a research question into a software architecture discussion. Do not turn a small code change into a design ceremony.

## Software framing

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

Before creating one, state the decision the preview is meant to clarify. Then
read [references/visual-checkpoint.md](references/visual-checkpoint.md) and
follow its lightweight static-HTML workflow. The checkpoint is optional and
must degrade cleanly to an in-chat sketch when the host cannot preview a local
HTML file.

A visual checkpoint is a disposable design aid, not an application runtime.
For an implemented frontend, use the project's real development server and
verification workflow through the developing skill.

## Research framing

Move through this chain when it helps:

```text
research question
-> hypothesis or claim
-> existing assumptions
-> baseline or control
-> observable variables
-> metrics
-> minimal experiment
-> success criterion
-> failure or falsification criterion
```

Keep engineering claims separate from research claims:

- code works: implementation evidence;
- experiment ran: execution evidence;
- hypothesis supported: interpretation backed by results.

## Interaction

1. Inspect the relevant files, data, logs, prior results, and constraints before asking for context.
2. Resolve what can be resolved independently.
3. Ask one focused question only when the missing answer changes scope, design, or risk.
4. Offer a recommendation and its tradeoff when alternatives matter.
5. Stop when the next action is clear; do not require a formal approval gate for an obvious low-risk decision.

If another skill was explicitly invoked, or has produced an authoritative upstream artifact such as a PRD, consume that output instead of repeating its responsibility. Continue from the appropriate Janus stage and preserve the upstream artifact as the source of truth. This integration is optional: if no upstream skill is installed or invoked, the software and research modes above remain complete and usable on their own.

Return a proportionate Working Plan or a clear handoff to `developing`. For broad, long-running, high-risk, or multi-step work, persist that plan using the durable-plan rules in `developing`; do not create separate spec and plan documents here.

## Red flags

- Designing for every imaginable future.
- Asking questions whose answers do not change the work.
- Treating a research problem as a feature backlog.
- Rewriting an authoritative PRD or research brief without an identified contradiction.
- Adding a user approval round only because a template says so.
- Building a server, live-reload channel, or browser event bridge for a disposable visual checkpoint.
- Treating a static mockup as evidence that an implemented frontend works.

The goal is understanding before significant change, not ceremony for its own sake.
