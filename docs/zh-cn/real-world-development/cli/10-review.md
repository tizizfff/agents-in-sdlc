---
title: "第 10 课：总结和后续步骤"
description: "回顾 Copilot CLI工作流、两个拉取请求、可复用自定义项和更多资源。"
authors:
  - geektrainer
lastUpdated: 2026-09-29
---

你在连续的 Tailspin Toys工作流中使用了 GitHub Copilot CLI：

- 准备 Codespace、安装 Copilot CLI、探索项目并找到预置的筛选 issue。
- 添加星级评分，在转发的浏览器中审查结果，并手动合并第一个拉取请求（PR）。
- 从筛选 issue开始，在 Plan 模式中明确方案，在 Autopilot 模式中构建，并在 Interactive 模式中审查。
- 使用自定义指令指导智能体，自定义现有的 `quality-checks` 技能，并用它运行单元测试、lint 和类型检查。
- 添加 Playwright 模型上下文协议（MCP）服务器，并用它在真实浏览器中体验筛选功能。
- 创建并选择质量保证（QA）自定义智能体，以评估需求、覆盖率、技能结果和浏览器证据。
- 审查完整筛选变更，并为筛选 PR授权 Agent Merge。
- 探索用于上下文、模型、共享和可选云委派的斜杠命令。

## 已交付内容

研讨会包含两个 PR里程碑，每个里程碑都位于从更新后的 `main`创建的独立分支：

1. **星级评分**：在游戏卡片上显示现有的 `starRating`，并明确表示未评分状态。
2. **筛选和质量工作流**：实现筛选、更新指令并将其应用到功能中、自定义 `quality-checks`报告、创建 QA配置并包含相关测试。

从规划筛选到创建 PR，你始终使用相同对话和分支。为简化研讨会，我们将这些工作合并到一个 PR中。

## 不同类型的验证

你通过多种方式检查代码：自动测试、亲自浏览器检查，以及 Copilot通过 MCP进行的浏览器探索。`quality-checks` 技能运行了单元测试、lint 和类型检查，并以新格式报告结果。QA将这些结果与需求和测试覆盖率审查结合起来，再提交 PR。

添加测试应弥补真正的测试缺口；无需新增测试的 QA运行仍可能是正确的。授权合并前应审查代码和证据，并在变更后刷新受影响的证据。

## 最佳实践

提供给 Copilot的上下文和工具会影响其工作。本研讨会中，你更新了指令、自定义了技能、创建了 QA配置，并配置了 MCP服务器。请在其他对话中复用这些自定义项，并根据团队需求调整。指令设定标准，技能描述可重复任务，自定义智能体定义专业角色，MCP服务器连接外部工具。审查实际变更和工具结果，而不仅是智能体摘要。

根据任务匹配**模式和模型**。用 **Plan**在构建前思考方案，用 **Interactive**持续参与小范围变更，用 **Autopilot**处理范围明确的任务。常规编辑选择更快模型，复杂工作选择更强模型。

基础设施之外，上下文仍然同样重要。清楚说明要构建**什么**、**为什么**以及**如何构建**，会显著改变结果。

## 更多探索

你已掌握核心工作流。还有几个值得了解的 CLI功能：

- `/review`：请代码审查智能体分析变更。
- `/rubber-duck`：讨论问题并获得另一种视角。
- `/fleet`：并行协调独立子任务。
- `/worktree`：隔离独立任务。
- `/delegate`：将任务发送给 Copilot云智能体。

## 后续步骤

提高任何工具的熟练度，最好的方法就是持续使用！可用于生产代码、业余项目，以及你构想多年却一直未动手的小应用。与团队分享学习心得，也向他们学习。还应继续探索文档。

如果要从终端继续扩展 Tailspin Toys，可阅读可选的 [Foundry Backer Concierge 系列][foundry]。若要比较其他环境，可探索 [VS Code研讨会][vscode]、[GitHub Copilot app研讨会][app]或 [Copilot云智能体研讨会][cloud]。

## 资源

- [关于 GitHub Copilot CLI][about-cli]
- [Copilot CLI 命令参考][cli-reference]
- [自定义 Copilot CLI][customize-cli]
- [使用 Copilot CLI管理拉取请求][manage-prs]

[previous-lesson]: ../9-cli-power-tools/
[foundry]: ../8-foundry-agent/
[vscode]: ../../vscode/
[app]: ../../app/
[cloud]: ../../cloud/
[about-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[customize-cli]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
