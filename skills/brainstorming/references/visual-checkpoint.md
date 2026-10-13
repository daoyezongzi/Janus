# Visual Checkpoint

Use this reference only after the brainstorming entrypoint routes a genuinely
visual decision here.

## Purpose

A visual checkpoint is a working HTML page that makes the current design
decision easier to judge. It can show structure, visual hierarchy, interaction
states, or a diagram. Page design uses [frontend](../../frontend/SKILL.md) and
its [audit and layout workflow](../../frontend/references/audit-and-layout.md),
including an ASCII wireframe delivered before the HTML Demo.

## Workflow

1. Name the decision the preview will clarify. Keep one checkpoint focused on
   one visual question.
2. For page tasks, deliver the current ASCII text-box wireframe using frontend's
   workflow. Use accepted artifacts and respond to the user's design feedback.
3. Create the working HTML in a permitted, Git-ignored project directory,
   defaulting to `.janus-work/`. Verify the ignore rule before creating files.
   Use [../assets/visual-checkpoint.html](../assets/visual-checkpoint.html) when
   its comparison layout serves the decision. Use the project's necessary
   dependencies and existing preview capability when they are needed.
4. Replace the sample title, supporting copy, options, and preview markup with
   content grounded in the current project. Use real labels and representative
   content from available data; leave unavailable data positions clearly empty.
5. Open and check the requested interactions using the existing local preview
   or project workflow. Screenshots and visual inspection require an explicit
   user request; DOM, interaction, response, and log checks provide ordinary
   verification. Do not introduce a preview server or event bridge for this aid.
6. Deliver the preview and its actual checked capabilities. When the user asked
   to see it before proceeding, wait for feedback in the conversation. Local clicks may
   highlight a choice for comparison, but they are not a feedback channel and
   must not be treated as user input until the user responds in chat.
7. Update the design and preview when feedback changes the decision. Return
   the resulting decision to the original task and continue authorized work.

Demo HTML and screenshots stay in Git-ignored directories and are never
committed. If the user asks to retain them, deliver the ignored files or an
archive. Useful decisions follow the original task's recording scope.

## Boundaries

- Prefer conversation for requirements, scope, technical tradeoffs, data
  models, API contracts, and choices expressible clearly in words.
- Use the necessary project components, dependencies, and preview workflow.
  Describe the actual data source, interaction, persistence, and API capabilities.
- Usually present one complete design. Present alternatives when a concrete
  unresolved decision requires them, explaining the choices and their effects.
- Scale fidelity to the question: wireframes for structure, representative
  styling for visual direction, and only enough interaction to compare states.
- Report only the preview behavior actually checked. Production routing,
  backend integration, persistence, and complete user flows require evidence
  from the real application using frontend's verification reference.
- Once implementation exists, preview and test the real application instead.

## Handoff

Return the current decision, artifact location, checked preview behavior, and
remaining requirements through the normal conversation or existing Working
Plan. Use developing for an execution task's final recording and handoff.
