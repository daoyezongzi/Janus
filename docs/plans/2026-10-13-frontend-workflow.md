# 前端流程接入 Working Plan

## Goal

增加 `frontend` 专业技能，连接 Janus 的设计、执行和诊断入口，并通过子代理审核确认符合本地前端工作流程。

## Context / Constraints

- 基于本机已确认的前端流程与 Janus 接入方案实施。
- HTML Demo 之前提供 ASCII 文本框草图，使用当前有效设计与用户反馈。
- Demo、HTML 预览和截图包不提交 Git，保存在项目内已被 Git 忽略的目录。
- 审计、预览与正式修改分别遵循当前授权；已确认设计和用户文件修改持续有效。
- 使用真实文件、接口与有效数据验证；不使用 mock，不主动使用视觉功能，不读写系统临时目录。
- 完成实施后进行独立子代理审核，处理确认的问题后提交本地 commit；push 需要用户明确授权。
- 本次修改范围为 Janus 仓库。已安装技能和 Prism 正式文件保持当前内容；Prism 可作为只读验证资料。

## Design

- `frontend` 提供页面理解、信息架构审计、布局和交互设计、草图、Demo 及前端验收方法。
- `brainstorming` 处理影响范围、业务含义和验收的未决问题；页面设计使用 `frontend`。
- `developing` 负责正式修改的完整执行、验证、项目记录和交付。
- `debugging` 使用实际异常证据完成诊断，返回原前端步骤。
- 专业技能入口保留关键阶段与限制，详细审计、布局和验证方法分别保存在 references。

## Changes

1. 编写 `skills/frontend/SKILL.md`、`agents/openai.yaml` 和两个 references。
2. 更新 `brainstorming` 的页面设计入口与 visual checkpoint reference，更新 `developing` 的专业技能入口和 Demo 提交规则。
3. 同步 README 的技能职责、前端流程及安装说明。
4. 执行技能格式、元数据、Markdown 引用和 Git 忽略检查。
5. 交给子代理进行流程符合性审核和独立实际使用验证，处理确认的问题并复核。
6. 更新 LOG、TODO 和本计划的验证结果，检查最终修改并创建本地 commit。

## Verification

- 四个技能通过 `quick_validate.py`。
- YAML 元数据、默认提示、相对 Markdown 引用和仓库文件引用有效。
- 当前技能与 references 覆盖已确认前端流程的全部阶段，且 Demo、ASCII 草图、授权与实际验证要求一致。
- 独立审核依据本地流程文件逐项提供结论与证据。
- 实际使用验证读取真实前端资料；生成资料仅写入 Git 忽略目录，运行结果与证据范围分别记录。
- 最终提交仅包含本任务正式修改，Demo 和验证中间资料保持 Git 忽略。

## Progress

- [x] 已检查 Janus 当前文件与已确认流程，仓库初始没有修改。
- [x] 已完成技能和入口修改。
- [x] 已完成格式、引用和忽略检查：四个技能、四份元数据和 21 个本地引用通过，验证脚本与证据被 Git 忽略。
- [x] 子代理审核及实际使用验证通过。
- [x] 已记录结果并完成提交前复核。

## 验证结果

- `workflow_review` 按本地流程完成 11 个阶段审核，并对最终技能与实际预览证据进行复核，两次结论均通过。
- `frontend_forward_test` 读取真实 Prism 页面与接口，交付审计及 ASCII 草图后生成独立 HTML。草图文件先于 HTML 创建，主代理也已在 HTML 创建前取得草图产物。
- 四个技能、四份元数据、21 个本地引用、修改格式及 Git 忽略检查通过；验证命令和来源 hash 位于 `.janus-work/frontend-validation.json`。
- 实际浏览器验证通过 13 项操作检查，覆盖 12 个宽度、5 种状态，共 60 组 DOM 几何；8 个 Prism 来源文件的前后 SHA256 一致。
- 预览、验证代码和证据位于 `.janus-work/frontend-forward-test/`，全部被 Git 忽略。真实业务资料和服务条件不足的操作保持未验证，范围记录于交付记录与 `evidence/verification.json`。
- 主代理已检查运行输出、验证代码和结果文件，确认预览使用空白业务数据与实际 DOM 操作。服务与浏览器进程已关闭，清理证据位于 `evidence/cleanup.txt`。
