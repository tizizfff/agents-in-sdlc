---
title: "第 3 课：智能体模式：Plan 和 Autopilot"
description: "使用 Plan 商定方案，使用 Autopilot 根据 issue 构建筛选功能，并使用 Interactive 模式审查结果。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

我们已向项目添加了一个小功能，但更大的变更需要更完善的流程。GitHub Copilot CLI 可融入组织现有的工作流，确保正确地构建正确的内容。本课将从 issue 开始介绍典型的智能体驱动开发流程：使用 Plan 定义方案，使用 Autopilot 实现功能，确保代码有效、功能符合预期，最后成功合并。

> [!NOTE]
> 在整个功能工作流中，你将使用相同的对话和分支。通常应为不同类型的文件使用不同分支或 PR，但在此研讨会中会采用一种快捷方式，以便集中练习核心概念。

在本课中，你将：

- 从 GitHub issue 开启新的 Copilot 对话。
- 在 Plan 模式中明确需求。
- 使用 Autopilot 模式实现新功能。
- 审查代码。
- 在转发的浏览器中手动验证功能。

继续实现此功能时，你还会更新仓库指令、自定义现有的 `quality-checks` 技能、添加 MCP 验证、创建 QA 智能体并创建功能 PR。

## 场景

Tailspin Toys 的目录不断扩展，访问者需要按类别和发行商筛选游戏。待办事项 issue 描述了该功能，但组合类别等细节在编码前需要达成共识。你将使用 Plan 模式解决这些决策，再使用 Autopilot 实施有边界的实现。

## 后台

将 AI 编码智能体引入开发流程不会改变软件开发的基本方法，反而会使这些方法更加重要。多数开发者遵循以下流程：

1. 从描述待办工作的 issue 开始。
2. 制定构建计划。
3. 编写并审查代码。
4. 运行测试验证代码。
5. 手动验证新功能。
6. 创建拉取请求（PR）。
7. 在审查代码且持续集成成功后合并代码。

> [!NOTE]
> 具体步骤会因团队和组织而异，但大多是上述流程的变体。

坚持这一标准流程，可确保 AI 生成的代码符合需求，并接受与手写代码相同的审查。

## 对话模式

**对话模式**控制智能体的自主程度。按 <kbd>Shift</kbd>+<kbd>Tab</kbd>循环切换：

- **Interactive**：你与智能体协作；智能体提出修改，并在继续前等待输入。
- **Plan**：智能体先制定计划，并禁止编辑项目文件。
- **Autopilot**：智能体自主工作，包括编写代码、运行测试并迭代直至完成任务。

先进入 Plan 模式，审查计划，再使用 Autopilot 实现。

## 从 issue 开始

开始筛选工作前，请返回 Codespace，确认仓库和终端已准备就绪。

1. 返回 Codespace；如果它已停止，请先重新启动。
2. 确认星级评分 PR 已合并。
3. 如果终端未打开，按 <kbd>Control</kbd>+<kbd>\`</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>\`</kbd>（Windows/Linux）。
4. 更新 `main`，并为筛选工作创建分支：

   ```bash
   git checkout main
   git pull --ff-only
   git checkout -b game-filters-cli
   ```

5. 启动 Copilot CLI：

   ```bash
   copilot --yolo
   ```

6. 按 <kbd>Tab</kbd> 两次打开 **Issues** 标签页。
7. 按 <kbd>A</kbd>显示所有 issue。
8. 使用方向键突出显示标题为 **Allow users to filter games by category and publisher** 的 issue。
9. 按 <kbd>C</kbd>将该 issue 添加到提示并返回 **Session** 标签页。

提示现在会以 `#7`（或相近编号）开头。`#` 可将 GitHub issue 或拉取请求（PR）带入上下文。

## 制定筛选功能计划

规划让你能够在交给 Copilot 前确定功能实现方法或任务方案。处理复杂任务时，花一点时间规划始终值得。

1. 按 <kbd>Shift</kbd>+<kbd>Tab</kbd>切换到 Plan 模式。确认提示下方的模式指示器显示 **Plan**。
2. 在上一步添加的 issue 引用后输入：

   ```plaintext
   Create a plan for implementing this feature.
   ```

Copilot 开始制定计划：先探索项目，再确定最佳方案。

3. Copilot 可能询问筛选能力应如何工作。根据你的偏好回答；这里没有唯一错误答案。
4. 计划完成后，按 <kbd>Control</kbd>+<kbd>E</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>E</kbd>（Windows/Linux）展开计划。
5. 上下滚动并审查计划。
6. 如果计划的任何部分不符合你的决定，请 Copilot修改。

## 批准 Autopilot

计划已编写并审查完毕，可以开始实现。让 Copilot 使用 Autopilot 完成工作。

1. 选择 **Accept plan and build on autopilot (recommended)**，或当前安装版本中标签相近的选项。
2. 确认提示下方的模式指示器显示 **Autopilot**。
3. 观察 Copilot 按既定计划迭代、生成代码并运行测试。

> [!NOTE]
> 批准后可能立即开始实现，因此务必先审查计划。如果 Copilot 报告缺少依赖项或端口冲突，请先解决设置问题，再将检查视为完成。

## 审查并验证实现

代码生成后，应像审查任何其他代码一样审查并合并。

1. 按 <kbd>Shift</kbd>+<kbd>Tab</kbd>进入 Interactive 模式。确认模式指示器不再显示 **Plan** 或 **Autopilot**。
2. 输入 `/diff`并检查筛选实现和测试。
3. 将结果与 issue 和规划时作出的决策进行比较。
4. 完成代码审查后，按 <kbd>Esc</kbd>退出差异视图。
5. 审查项目检查的输出，并请 Copilot解决所有失败。

## 体验新功能

代码看起来不错，但能否运行？像之前一样启动应用，并通过 Codespaces 转发端口打开站点。

1. 请 Copilot 启动应用：

   ```plaintext
   Start the app so I can try the filtering feature in my browser. Tell me the URL and leave the server running.
   ```

2. Codespaces 报告端口 `4321` 可用后，选择 **Open in Browser**。
3. 测试类别筛选、发行商筛选以及你在计划中约定的组合筛选。
4. 确认重置和空结果行为符合 issue 和你的决定。
5. 返回 Codespace，并请 Copilot 停止已启动的开发服务器。

## 摘要和后续步骤

你已使用不同对话模式构建并审查功能。本课中，你：

- 从 GitHub issue 开启了新的 Copilot 对话。
- 在 Plan 模式中明确需求。
- 使用 Autopilot 模式实现了新功能。
- 审查了代码。
- 在转发的浏览器中手动验证了功能。

接下来，让我们进一步了解代码生成过程，并确保代码遵循文档化实践：[使用自定义指令][next-lesson]。

## 资源

- [GitHub Copilot CLI 中的 Autopilot][autopilot]
- [Copilot CLI 命令参考][cli-reference]

[autopilot]: https://docs.github.com/copilot/concepts/agents/copilot-cli/autopilot
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[previous-lesson]: ../2-add-star-rating/
[next-lesson]: ../4-custom-instructions/
