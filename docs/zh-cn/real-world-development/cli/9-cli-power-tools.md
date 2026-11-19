---
title: "第 9 课：GitHub Copilot CLI中的斜杠命令"
description: "探索用于管理上下文、选择模型、共享会话和可选云委派的斜杠命令。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

与其他优秀 CLI工具一样，GitHub Copilot CLI包含许多用于交互的斜杠命令。这些命令可公开高级功能、后台信息和更多配置选项。你已使用 `/diff`、`/mcp`、`/skills`、`/agent` 和 `/pr`，下面再探索几个实用命令。

在本课中，你将：

- 使用 `/context` 和 `/compact`了解 Copilot如何管理对话上下文。
- 使用 `/model`探索可用模型。
- 了解 `/share`如何导出或共享会话。
- 探索用于并行工作、worktree 和委派给云智能体的可选命令。

## 场景

核心 CLI工作流已完成。现在来看其他能力，包括上下文管理、切换模型、共享会话，以及可选地委派工作给[Copilot 云智能体][about-cloud-agent]。

## 探索 Copilot CLI上下文

处理更大或更复杂的任务时，可能会达到模型的最大上下文窗口。Copilot CLI会在需要时自动压缩对话，也可使用斜杠命令自行检查或压缩。

1. 返回 Codespace；如果尚未打开 Copilot CLI，请从仓库根目录启动。
2. 输入：

   ```plaintext
   /context
   ```

3. 注意模型、当前 token 用量，以及上下文在系统指令、工具、消息和剩余空间中的分配。
4. 压缩对话：

   ```plaintext
   /compact
   ```

5. 再次输入 `/context`并比较结果。如果对话本身较小，变化可能不明显。

> [!NOTE]
> 上下文窗口填满时，Copilot CLI会自动压缩。想自行选择压缩时机，可使用 `/compact`。切换到无关任务且希望新建对话时，请使用 `/clear`或 `/new`。

## 选择模型

不同模型具有不同优势，开发者的偏好也可能不同。Copilot CLI允许你列出并选择模型。

1. 输入：

   ```plaintext
   /model
   ```

2. 浏览可用模型和用量信息。
3. 保持当前模型、选择其他模型，或按 <kbd>Esc</kbd>关闭列表。

## 共享会话

团队协作和分享经验有助于每个人更好地使用 AI工具。`/share`可将会话导出为 Markdown 或 HTML 文件、创建可共享链接或发布 GitHub gist。

1. 输入 `/help`并查看当前安装版本中的 `/share`选项。
2. 如果要共享此会话，请选择符合需求的目标，例如使用 `/share file`导出本地 Markdown。
3. 在发送或发布前审查导出内容；会话导出可能包含提示、回复和项目详情。

发布链接或 gist为可选操作。不要发布团队不打算共享的仓库或对话内容。

## 可选：横向扩展或委派

核心研讨会现已完成。Copilot CLI还提供适用于更大任务的命令：

- `/fleet`可将独立子任务分配给子智能体并并行运行。
- `/worktree`可为独立任务创建隔离的 Git worktree。
- `/delegate`可将任务发送给 Copilot云智能体；它异步工作并可能创建拉取请求。

这些命令为可选操作，因为它们可能创建额外 worktree 或远程工作。尝试前，请先开启一个范围明确的新任务，并通过常规工作流审查结果。如需深入了解异步智能体工作，请继续阅读[云智能体研讨会][cloud-workshop]。

## 摘要和后续步骤

使用 Copilot CLI斜杠命令可以配置工具、共享会话并查看后台信息。本课中，你：

- 使用 `/context`和 `/compact`了解了 Copilot如何管理对话上下文。
- 使用 `/model`浏览了可用模型。
- 了解了 `/share`如何导出或共享会话。
- 探索了并行工作、worktree 和委派给云智能体的可选命令。

还有更多斜杠命令等待探索！让我们[回顾所学内容][next-lesson]并查看后续学习方向，结束本次旅程。

## 资源

- [Copilot CLI 命令参考][cli-reference]
- [Copilot CLI中的上下文管理][context-management]
- [关于 Copilot云智能体][about-cloud-agent]

[previous-lesson]: ../8-create-pull-request/
[next-lesson]: ../10-review/
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[context-management]: https://docs.github.com/copilot/concepts/agents/copilot-cli/context-management
[about-cloud-agent]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[cloud-workshop]: ../../cloud/
