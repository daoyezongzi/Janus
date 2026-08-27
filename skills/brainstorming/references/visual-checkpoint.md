# Visual Checkpoint

Use this reference only after the brainstorming entrypoint routes a genuinely
visual decision here.

## Purpose

A visual checkpoint is a temporary, self-contained HTML page that makes one
design decision easier to judge. It can show wireframes, layout alternatives,
visual hierarchy, interaction states, or a small diagram. It does not add a
server, live reload, browser-to-agent messaging, or a frontend framework.

## Workflow

1. Name the decision the preview will clarify. Keep one checkpoint focused on
   one visual question.
2. Create the working HTML in the host's temporary directory, outside the
   user's project. Start from [../assets/visual-checkpoint.html](../assets/visual-checkpoint.html)
   when its comparison layout fits; otherwise create an equally small,
   self-contained document.
3. Replace the sample title, supporting copy, options, and preview markup with
   content grounded in the current project. Use real labels and representative
   content when they affect the judgment.
4. Open the file with the host's available local HTML preview or browser
   capability. Do not introduce a server solely to display the checkpoint.
5. Ask the user to evaluate it and reply in the conversation. Local clicks may
   highlight a choice for comparison, but they are not a feedback channel and
   must not be treated as user input until the user responds in chat.
6. If feedback warrants another visual pass, revise the temporary HTML and
   reopen or reload it. Stop when the decision is clear.

If the user explicitly asks to retain the checkpoint, save it in the project's
existing artifact or design-document location. Otherwise leave it temporary
and do not add it to project state, LOG, TODO, or Git.

## Boundaries

- Prefer conversation for requirements, scope, technical tradeoffs, data
  models, API contracts, and choices expressible clearly in words.
- Keep the page self-contained: HTML, CSS, and optional local JavaScript only.
  Do not add dependencies, telemetry, remote assets, persistence, or network
  requests.
- Show two to four materially different options. Avoid decorative variants
  that do not change the decision.
- Scale fidelity to the question: wireframes for structure, representative
  styling for visual direction, and only enough interaction to compare states.
- Treat the page as a mockup. It does not verify routing, application state,
  accessibility, responsiveness, backend integration, or production behavior.
- Once implementation exists, preview and test the real application instead.

## Handoff

Record the resulting decision in the Working Plan or normal conversation at
the same level as any other brainstorming conclusion. Do not preserve the
temporary HTML merely to narrate the process.
