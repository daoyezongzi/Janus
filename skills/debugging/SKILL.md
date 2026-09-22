---
name: debugging
description: Use when the user requests diagnosis or an observable bug, failed test, unexpected result, or research anomaly needs an evidence-based explanation.
---

# Janus Debugging

## Invariant

Do not stack speculative fixes. Each change should test an explicit explanation of the observed divergence.

## Task context

Identify the requested explanation, expected behavior, observed result, and permitted operations. A diagnosis request defines its own deliverable; repairs and project writes must remain within the current authorization.

When called during execution, retain the original goal, affected step, and remaining requirements. Use the current conversation or existing Working Plan for diagnostic state, and follow [developing](../developing/SKILL.md) for conditional planning and context recovery.

## Workflow

1. **Reproduce** the original failure or anomaly with the smallest reliable command, input, or experiment.
2. **Gather evidence** from output, logs, state, versions, data, environment, and the final known-good comparison.
3. **Locate divergence:** identify the first point where actual behavior differs from expected behavior.
4. **State one hypothesis** that explains that divergence and what evidence would disprove it.
5. **Run a discriminating probe:** state the expected observations, execute the test or experiment, and read the actual result.
6. **Check probe validity:** confirm that the intended operation ran and its observations can distinguish the explanations. A probe that did not run as intended or observe the relevant behavior leaves the hypothesis unresolved.
7. **Choose the supported outcome** below, preserving the evidence and any remaining uncertainty.

## Diagnostic outcomes

| Finding | Next action |
| --- | --- |
| Evidence supports an implementation, data, environment, or measurement defect | Within the authorized scope, apply the smallest repair addressing the cause and rerun the original reproduction and affected checks. A diagnosis-only request can finish with the supported explanation. |
| The research result passes its validity checks | Return the result and evidence to the research task for interpretation against its question and evaluation method. |
| Evidence remains insufficient | Identify the next probe that can add evidence. If the necessary input or execution condition is unavailable, state the limitation and continue independent authorized work. |

Confirm the cause before a broad repair. Use a probe to support or reject a hypothesis only when the probe ran correctly and its observations are sufficient for that judgment.

## Evidence checklist

Check the evidence most likely to reveal the divergence:

- assumptions and inputs;
- call path, control flow, or data transformations;
- versions, configuration, permissions, and environment;
- timing, state, randomness, and resource limits;
- measurement code, baselines, and expected values.

## Research anomalies

For an experiment that produces an unexpected result, distinguish:

- an implementation failure;
- a data or environment problem;
- a measurement failure;
- a genuine result that challenges the hypothesis.

Do not change the model, data, metric, and environment at the same time. Preserve a control or baseline whenever possible.

A valid result can support or challenge a research hypothesis, or establish a limit on the available evidence. Completion depends on the requested research deliverable; a requested performance target remains incomplete until the relevant evidence meets that target. Change evaluation criteria only when the requirements or measurement evidence justify the change.

## When hypotheses fail

When repeated probes add no evidence or successive hypotheses fail, recheck:

- assumptions;
- architecture or data flow;
- input data and labels;
- environment and dependency state;
- whether the measurement actually observes the claimed behavior.

## Completion standard

For a standalone diagnosis, report the requested explanation, supporting evidence, and remaining uncertainty. If repair was authorized and performed, also report the actual change, original reproduction command, and rerun results. State when evidence is still insufficient to complete the diagnosis.

When called during execution, return these findings to `developing` at the affected original step. Recheck the original task's remaining requirements and continue them; resolving the local issue only establishes its corresponding checks.

Follow [developing](../developing/SKILL.md) for applicable recording and repository handoff, within the task's write permissions. Embedded investigations use the original task's final handoff.
