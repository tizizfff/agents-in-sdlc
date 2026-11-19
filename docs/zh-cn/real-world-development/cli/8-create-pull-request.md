---
title: "第 8 课：创建并合并功能 PR"
description: "一并审查筛选、指令、技能更新、QA配置和测试，然后创建 PR并使用 Agent Merge。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

筛选实现、指令更新、技能更新、质量保证（QA）配置和测试已保存在同一分支上。现在可以一起审查并创建拉取请求。星级评分 PR由你亲自合并；这次将允许 **Agent Merge** 管理流程。

> [!NOTE]
> 通常应将功能、指令更新、技能更新和 QA智能体拆分为多个单独 PR。为简化研讨会，本节将完整筛选和质量工作流保留在同一个对话和分支中，并将全部工作合并到此 PR。

在本课中，你将：

- 了解 Agent Merge及其如何自动化合并生命周期。
- 检查完整功能变更和验证证据。
- 创建筛选 PR。
- 仅在审查后启用 Agent Merge，并确认 PR已合并。

## 场景

在筛选工作流中，你使用 Copilot规划、实现并验证功能。Tailspin Toys 希望自动化剩余 PR工作，同时将合并授权留给开发者控制。

## Agent Merge简介

**Agent Merge**自动处理落地拉取请求所需的剩余工作。启用后，Copilot会处理阻碍 PR的事项，包括修复失败的持续集成（CI）检查、响应审查意见以及必要时 rebase，然后在仓库允许时启用 GitHub 自动合并。

此前你亲自选择了 **Merge pull request**。Agent Merge可承担该职责。启用它前，请先审查工作并确定其已准备就绪。

## 使用 Agent Merge管理 PR

代码已创建，下面一起审查，创建 PR，并让 Agent Merge管理剩余流程。

1. 返回 Codespace。
2. 输入 `/agent`打开智能体对话框。
3. 从选项列表中选择 **Default**，并按 <kbd>Enter</kbd>。
4. 使用 `/pr create`创建新 PR。
5. 使用 `/pr agentmerge`激活 Agent Merge。
6. Copilot会监控 PR上的持续集成流程。全部成功后，它会执行合并。
7. 确信看到类似 “PR #14 was squash-merged successfully.” 的 Copilot消息。

> [!IMPORTANT]
> Agent Merge不会绕过必需批准、分支保护、合并队列、仓库设置或权限。如果遇到阻塞，请阅读报告原因，并在仓库允许时手动完成已审查的合并。

## 摘要和后续步骤

你已自动化开发流程中的多个环节，包括生成代码、测试和验证代码，以及现在的拉取请求流程：

- 了解了 Agent Merge及其如何自动化合并生命周期。
- 检查了完整功能变更和验证证据。
- 创建了筛选 PR。
- 仅在审查后启用 Agent Merge，并确认 PR已合并。

接下来，你将[探索更多实用的 Copilot CLI斜杠命令][next-lesson]，包括上下文、模型、共享和可选的云委派。

## 资源

- [使用 Copilot CLI管理拉取请求][manage-prs]
- [Copilot CLI 命令参考][cli-reference]

[previous-lesson]: ../7-qa-agent/
[next-lesson]: ../9-cli-power-tools/
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
