# Janus Log

## 2026-10-13 - 接入前端工作流程

- **变更：** 增加 `frontend` 技能、界面元数据以及审计与布局、正式验证两个 references；连接 `brainstorming` 和 `developing`，同步 README 的职责、流程与四个技能的安装说明。
- **流程：** 覆盖任务与范围、页面理解、元素审计、状态设计、ASCII 草图、HTML Demo、正式修改、真实验证、相关页面核查、审核与提交、演示交付。草图先于 HTML，已有设计与用户修改持续有效。
- **预览：** 数据不足时使用独立标明的布局控制查看空白结果；需要尚未连接服务的业务操作保持不可用。Demo 与正式业务的证据范围分别记录。
- **Git：** Demo、HTML 预览与截图包保存于被 Git 忽略的项目工作目录，通过文件交付；正式修改完成 commit 后报告结果，push 需要用户明确授权。
- **格式验证：** 四个技能通过 `quick_validate.py`，四份 YAML 元数据与 21 个本地 Markdown 引用有效，`git diff --check` 和工作目录忽略检查通过。命令为 `.janus-work/validation-env/bin/python .janus-work/verify_frontend_skills.py`，版本 hash 与结果保存在 `.janus-work/frontend-validation.json`。
- **独立审核：** `workflow_review` 逐项核查本地流程的 11 个阶段及技能交接，审核通过；读取实际预览和运行证据后复核最终规则，确认结论成立。
- **实际使用：** `frontend_forward_test` 读取 Prism 当前交易风格页面及接口，先交付审计与 ASCII 草图，再生成独立 HTML。实际浏览器完成 13 项操作检查、12 个宽度、5 种状态和 60 组 DOM 几何检查；没有 JavaScript 错误，8 个 Prism 来源文件的前后 SHA256 一致。
- **证据：** `.janus-work/frontend-forward-test/` 保存理解、草图、预览、验证脚本和交付记录；`evidence/verification.json`、`run.log` 和 `cleanup.txt` 保存结果与清理记录，全部资料被 Git 忽略。使用现有 Playwright 与 Microsoft Edge，验证命令及完整输出位于交付记录。
- **覆盖范围：** 实际使用验证覆盖独立预览的 DOM、交互、键盘、焦点、布局与页面历史。缺少有效成交资料、账户和 Prism 服务的真实解析、保存、分析与行情操作保持未验证。测试服务与浏览器进程已关闭。
- **计划：** 实施范围和验收要求记录于 `docs/plans/2026-10-13-frontend-workflow.md`。

## 2026-09-22 - Define conditional workflow and complete-task handoff

- **Behavior:** `developing` retains the complete request and remaining work. `brainstorming` returns decisions and acceptance requirements; `debugging` returns supported findings and applicable repair evidence to the affected original step.
- **Selection:** Planning, discussion, persistence, verification, isolation, and delegation follow their task conditions. High-impact work receives appropriate checks and review, with discussion focused on unresolved decisions.
- **Research:** Experiment validity, execution, and hypothesis support have distinct completion evidence. Valid research findings are interpreted against the requested question, and performance targets retain their stated acceptance requirements.
- **State:** Current requests determine scope; current artifacts and results establish progress. Changed inputs invalidate affected checks. Recording follows writing permissions and uses existing project records.
- **Verification:** All three repository skills passed `quick_validate.py`; PyYAML validated their UI metadata, markdown-it-py parsed eight Markdown files and checked six local link targets, and `git diff --check` passed.
- **Task evidence:** An independent agent used the revised developing and debugging skills for an actual read-only comparison of the three repository skills and their local installations. It reported file and SHA-256 differences, verified referenced files, respected the read-only scope, and distinguished file evidence from untested host loading behavior.
- **Plan:** The implementation scope and real-task acceptance conditions are recorded in `docs/plans/2026-09-22-janus-workflow-logic.md`.
- **Validation scope:** Format, reference, and logical consistency checks are distinct from real-task behavior checks. Broader execution coverage remains tracked in TODO.

## 2026-08-27 - Add lightweight visual checkpoints

- **Changed:** Added an optional visual branch to `brainstorming`, a focused usage reference, and a self-contained HTML comparison template.
- **Decision:** Use a temporary static page only when seeing layout, hierarchy, spatial relationships, or design alternatives materially improves the decision.
- **Decision:** Keep feedback in the conversation. Local page clicks may highlight an option, but Janus does not add a server, WebSocket channel, persistent session, telemetry, or browser-to-agent event bridge.
- **Decision:** Treat visual checkpoints as disposable design aids. Implemented frontends continue to use their own development server and verification workflow.
- **Reason:** Preserve the useful visual-feedback idea from Superpowers while keeping Janus lightweight, host-agnostic, and free of a maintained web runtime.
- **Verification:** All three repository skills passed `quick_validate.py`; the template's inline JavaScript compiled successfully; its required files and responsive/accessibility markers are present; and no remote asset or browser-network call was found.
- **Constraint:** The Codex in-app browser blocks local `file://` navigation, so interaction was not replayed there. The remaining real-world forward test stays explicit in `TODO.md` instead of introducing a preview server solely for testing.
- **Follow-up:** Forward-test the workflow on a real visual decision before adding any further automation.

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

## 2026-08-16 - Replace active Superpowers registration

- **Changed:** Moved the 14 active Superpowers workflow skill directories and its `.tmp` plugin cache out of the active Codex paths into a local archive outside the active skills directory.
- **Changed:** Installed Janus `brainstorming`, `developing`, and `debugging` from the public Janus repository into the configured Codex skills directory.
- **Verification:** All three installed skills passed `quick_validate.py`; their `SKILL.md` hashes match the Janus repository; no active Superpowers plugin path or old workflow directory remains.
- **Preserved:** Frontend skills, `socrates`, PDF, Office, and `idea-refiner` were not changed. The historical `claude_imports` Superpowers archive was left untouched because it is not registered or active.
- **Result:** Janus is now the active lightweight workflow while Idea Refiner remains an independent optional upstream companion.

## 2026-08-20 - Add plan-backed context recovery

- **Changed:** Broad, long-running, high-risk, or multi-step tasks that may cross a context or session boundary now persist a Working Plan in the project; trivial work remains plan-free unless planning adds real value.
- **Decision:** A fresh execution conversation does not automatically discover or read plans. Read a known plan only when the user points to it, requests plan-backed execution or continuation, or retained task context identifies it; after compaction, re-read it only when execution state is unclear or contradictory.
- **Reason:** Codex compaction is designed to preserve task-relevant context, but its compacted state is opaque. The plan supplies durable intent while `git status`, diffs, artifacts, LOG, and TODO supply observable execution state.
- **Evidence:** The archived Superpowers workflow writes multi-step plans to `docs/superpowers/plans`, reads and reviews them at execution start, and mirrors extracted tasks into Todo state; it has no separate same-session post-compaction hook.
- **Preserved:** Small reversible work stays lightweight; brainstorming, TDD, worktrees, subagents, formal review, and plan-file creation remain proportional to task risk and duration.
- **Verification:** All repository and installed Janus skills passed `quick_validate.py`; corresponding skill and UI metadata files match by hash, and `git diff --check` reported no formatting errors.

## 2026-08-23 - Add lightweight Git commit closure

- **Changed:** Moved project recording before final diff inspection and added commit-when-applicable to the `developing` workflow, README overview, debugging handoff, and UI metadata.
- **Decision:** In a Git repository, commit only task-owned changes after verification; use one commit for a typical trivial task and split only genuinely independent, verified units.
- **Decision:** Never push automatically, never mix prior or unrelated work into a commit, and report commit IDs plus any uncommitted remainder.
- **Decision:** Keep `skills/developing/SKILL.md` as the normative execution source; README stays a concise overview and `debugging` delegates repository handoff instead of duplicating Git rules.
- **Reason:** Local commits improve recoverability and session handoff without restoring Superpowers-style mandatory plans, worktrees, approval gates, or forced commit batching.
- **Verification:** The changed `developing` and `debugging` skills passed `quick_validate.py`; the README normative-source link resolves; `git diff --check` reported no formatting errors.

## 2026-08-25 - Constrain documentation side effects

- **Changed:** Added documentation-discipline rules to the normative `developing` skill and summarized them in the README.
- **Decision:** Keep warranted durable plans, including the `docs/plans/YYYY-MM-DD-<task>.md` fallback, as an intentional part of the Janus workflow.
- **Decision:** Use the project's existing log and TODO for ordinary execution state instead of generating standalone `NOTES.md`, `ANALYSIS.md`, `REVIEW.md`, `SUMMARY.md`, or ad hoc handoff files.
- **Decision:** Put warranted new project documents in an existing categorized documentation structure, or the smallest fitting `docs/<category>/` location when no convention exists; preserve conventional root and tool-required paths.
- **Decision:** Treat PRDs, proposals, project briefs, product plans, and other upstream planning artifacts as read-only unless the user explicitly asks to edit the artifact itself.
- **Reason:** Preserve durable planning and context recovery without scattering unrequested process documents across project repositories or silently changing product intent.
- **Verification:** All three repository skills and the installed `developing` skill passed `quick_validate.py`; the repository and installed `SKILL.md` hashes match; `git diff --check` reported no formatting errors.
