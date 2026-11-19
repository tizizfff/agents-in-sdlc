---
title: "第 2 课：添加星级评分：快速赢得成果"
description: "使用 Copilot CLI 修改游戏卡片，在转发的浏览器中审查，并将其合并为你的第一个拉取请求。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

安装并尝试 Copilot CLI 后，现在可以对项目进行第一次小型修改。游戏数据已有星级评分，但首页的游戏卡片尚未显示评分。你将请智能体展示评分、审查修改，并将其合并为第一个拉取请求。

在本课中，你将：

- 在功能分支上开启一次专注的 Copilot 对话。
- 请智能体对项目进行小幅修改。
- 使用 `/diff` 审查修改。
- 运行应用，并在转发的浏览器中确认修改。
- 创建并合并第一个拉取请求。

## 场景

Tailspin Toys 中的每款游戏都有星级评分，并且游戏详情页已经显示该评分。但首页游戏卡片只显示标题、类别、发行商和描述。作为热身，你将让智能体在每张卡片上展示现有评分——这是适合第一次会话的小而独立的修改。

## 对话的组成

**对话**是你与 Copilot CLI 协作完成任务的工作区。与 Copilot app 不同，普通 CLI 对话使用终端当前检出的仓库和 Git 分支，不会创建专用 worktree。保存的对话可以让你稍后继续讨论，而文件和分支仍是磁盘上的普通 Git 状态。

一次对话包含三项内容：你的提示和智能体的回复、智能体探索和编辑文件时的工具活动，以及可以使用 `/diff`检查的变更。

## 开始对话并请求修改

1. 返回 Codespace。
2. 如果终端未打开，按 <kbd>Control</kbd>+<kbd>\`</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>\`</kbd>（Windows/Linux）。
3. 使用以下命令启动 Copilot：

   ```bash
   copilot --yolo
   ```

4. 使用斜杠命令 `/new` 开启新会话，并按 <kbd>Enter</kbd>。
5. 使用以下提示请求修改：

   ```plaintext
   Show each game's starRating out of 5 in the game cards on the list page. If the rating is null, show "No rating yet". Keep the card layout as it is, add tests, and run the relevant checks.
   ```

Copilot 会探索项目、定位用于显示游戏详情的文件，并创建必要代码。现在，你已使用 Copilot CLI 添加了一个新功能！

## 审查差异

即使是小改动，合并前也应审查所有由 AI 生成的修改。

1. 输入 `/diff` 并检查每个已修改文件。
2. 确认评分存在时卡片显示数值；`starRating` 为 `null` 时显示 `No rating yet`。
3. 确认测试覆盖了这两种状态。
4. 审查 Copilot运行的检查结果，并请它修复任何失败。
5. 完成审查后，按 <kbd>Esc</kbd>退出差异界面。

> [!NOTE]
> 与所有生成式 AI 工具一样，Copilot 具有概率性而非确定性，因此你的实际代码可能有所不同。应审查行为，而不是期待完全相同的实现。

## 检查修改

不应只阅读代码后就假定它能够正常工作。

1. 请 Copilot 启动应用：

   ```plaintext
   Start the app so I can inspect the star-rating change in my browser. Tell me the URL and leave the server running.
   ```

2. Codespaces 报告端口 `4321` 可用后，选择 **Open in Browser**。
3. 确认游戏卡片以五分制显示评分。
4. 返回 Copilot，请它停止已启动的服务器：

   ```plaintext
   Stop the development server you started.
   ```

## 创建并合并第一个拉取请求

现在功能已实现，可以创建拉取请求（PR）并将新代码合并到项目中。

1. 请默认智能体提交修改：

   ```plaintext
   Commit the reviewed star-rating changes with an appropriate commit message.
   ```

2. 输入 `/pr create`。Copilot CLI 创建 PR 时会推送现有提交，并显示 PR URL。
3. 按住 <kbd>Command</kbd>（Mac）或 <kbd>Ctrl</kbd>（Windows/Linux）并选择 Copilot CLI 显示的 URL，以打开 PR。
4. 审查已修改文件和检查。
5. 准备就绪后，选择 **Merge pull request**，然后确认合并。
6. 返回 Codespace，并使用 `/exit`退出 Copilot CLI。
7. 更新本地 `main`：

   ```bash
   git checkout main
   git pull
   ```

## 摘要和后续步骤

恭喜！你使用 GitHub Copilot CLI 完成了第一次修改：

- 在功能分支上开启了一次专注的 Copilot 对话。
- 指示智能体对游戏卡片进行了小幅修改。
- 使用 `/diff`审查修改。
- 在转发的浏览器中运行应用并确认星级评分。
- 创建并合并了第一个拉取请求。

接下来，你将[从筛选 issue 出发，使用 Plan 和 Autopilot 模式][next-lesson]构建更大的功能。

## 资源

- [关于 GitHub Copilot CLI][about-copilot-cli]
- [Copilot CLI 命令参考][cli-reference]

[previous-lesson]: ../1-install-copilot-cli/
[next-lesson]: ../3-agent-modes/
[about-copilot-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
