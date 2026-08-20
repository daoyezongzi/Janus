---
name: debugging
description: Use when a bug, failed test, unexpected result, or research anomaly needs root-cause diagnosis before changing code, data, or experiment conditions.
---

# Janus Debugging

## Invariant

Do not stack speculative fixes. Each change should test an explicit explanation of the observed divergence.

For a long-running or multi-step investigation, keep a durable Working Plan. Within an already plan-backed investigation, after conversation compaction or an explicit request to resume, check whether the diagnostic state is still clear; if not, re-read the known plan and reconcile it with the current reproduction evidence, repository diff, and recorded results before continuing. A fresh conversation alone does not trigger plan discovery.

## Workflow

1. **Reproduce** the original failure or anomaly with the smallest reliable command, input, or experiment.
2. **Gather evidence** from output, logs, state, versions, data, environment, and the final known-good comparison.
3. **Locate divergence:** identify the first point where actual behavior differs from expected behavior.
4. **State one hypothesis** that explains that divergence and what evidence would disprove it.
5. **Write a minimal test or probe** that distinguishes the hypothesis from alternatives.
6. **Confirm the root cause** before making a broad fix.
7. **Apply the smallest fix** that addresses the cause, without unrelated cleanup.
8. **Rerun the original reproduction** and relevant regression, integration, or experiment checks.
9. **Record the result** when it changes future work: cause, evidence, fix, limitation, and implication.

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

## When hypotheses fail

After repeated failed hypotheses, stop patching and recheck:

- assumptions;
- architecture or data flow;
- input data and labels;
- environment and dependency state;
- whether the measurement actually observes the claimed behavior.

## Completion standard

Do not report a fix merely because the edited code looks plausible. Report the reproduction command, evidence, root cause, change, rerun result, and any remaining uncertainty.
