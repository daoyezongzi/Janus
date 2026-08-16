# Janus Log

## 2026-08-16 - Initialize Janus V1

- **Changed:** Created the Janus repository shape, three core skills, README, license, and state files.
- **Decision:** Keep `brainstorming`, `developing`, and `debugging`; merge spec and plan into one proportionate Working Plan.
- **Decision:** Make TDD, worktrees, subagents, and formal review risk-based instead of mandatory.
- **Decision:** Let explicitly invoked specialized skills and authoritative upstream artifacts remain authoritative; Janus consumes their output rather than duplicating it.
- **Reason:** The local Superpowers workflow repeats approval gates and execution ceremony that are useful for high-risk autonomous software work but excessive for routine personal development and research.
- **Result:** The workflow preserves context, evidence, diff inspection, recoverability, and an understandable handoff while allowing trivial work to stay trivial.
- **Verification:** Inspected the local Superpowers process skills before writing Janus; the three Janus SKILL.md files will be checked with the skill validator and repository status before the initial commit.
- **Implication:** Janus V1 is an independent, original rewrite inspired by Superpowers. Idea Refiner is optional, installed separately, and consumed only when present as an upstream product-definition skill.

## 2026-08-16 - Register Idea Refiner compatibility

- **Changed:** Installed `idea-refiner` from `BURIBURI-ZAEMON1/idea-refiner-skill` into the local Codex skill directory.
- **Decision:** Idea Refiner owns early idea refinement, related-work mapping, product identity, core mechanism, and PRD persistence; Janus owns proportionate implementation and research execution after that handoff.
- **Result:** Janus documents the boundary without vendoring or duplicating Idea Refiner; its own brainstorming mode remains complete when the external skill is absent.

## 2026-08-16 - Forward-test Janus V1

- **Evidence:** A software change scenario and a research anomaly scenario were reviewed against the three Janus skills by independent read-only forward tests.
- **Software result:** Brainstorming was correctly treated as optional for a small reversible CLI change. The output formed one proportionate Working Plan, identified the side-effect boundary, preserved the no-flag path, and required focused regression plus full verification.
- **Research result:** The workflow consumed an upstream experiment brief without rewriting it, compared run manifests and raw metrics before proposing fixes, and kept implementation evidence, execution evidence, and hypothesis support separate.
- **Decision:** Keep the current three-skill V1 surface. Do not add mandatory worktrees, subagents, approval rounds, or domain-specific templates based on these tests.
- **Follow-up:** Test a real Idea Refiner PRD-to-Janus handoff after the local project is committed; keep that integration optional.
