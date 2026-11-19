---
title: "练习 5：迭代 GitHub Copilot的工作"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← 上一课：管理智能体][previous-lesson] |
|:--|

## 审查工作

在本实验中，你让 GitHub Copilot完成了多个改进用户体验和新增功能的任务，包括添加文档、构建相关游戏功能，以及实现高对比度和浅色模式等可访问性功能。下面审查代码变更，并在必要时向 Copilot提供反馈。

### 场景

生成式 AI不会改变软件设计和 DevOps的基本方法。始终应审查生成代码，并遵循正常 DevOps流程。请在向团队开放审查前，审查 Copilot生成的文档、相关游戏功能和可访问性功能。

## 安全与 Copilot云智能体

由于云智能体异步且无需监督地执行任务，已设置安全约束：

- Copilot只能读取仓库，并且只能向用于编写代码的分支写入。
- 云智能体在 GitHub Actions中运行，并创建独立、临时的工作环境。
- 所有 GitHub Actions工作流在运行前都需要人工批准。
- 默认限制[对外部资源的访问][agent-firewall]，包括 MCP服务器。

## 审查生成的文档

先审查 GitHub Copilot云智能体生成的第一个拉取请求，即添加代码文档。

> [!NOTE]
> 探索 PR时可能看到 Copilot被防火墙阻止的警告；这是预期行为，因为 Copilot默认限制外部资源访问。

1. 返回仓库。
2. 选择 **Pull Requests**并打开标题类似于 **Add missing documentation**的 PR。
3. 选择 **Files changed**审查变更。
4. 查看新建的 TSDoc注释、TypeScript约定和注释头。
5. 如需修改，可在 PR中标记 **@copilot**；它会启动新会话处理反馈。

## 审查相关游戏功能

返回 Copilot为解决相关游戏 issue生成的 PR：

1. 在仓库中选择 **Pull Requests**。
2. 打开标题类似于 **Show related games on the game details page**的 PR。
3. 审查生成代码。
4. 工作流等待批准时，选择 **Approve and run workflows**。
5. 工作流通过后，可切换到对应分支并运行手动测试：

    ```bash
    git fetch origin
    git checkout <branch-name>
    ```

## 审查可访问性功能

最后审查自定义可访问性智能体实现的功能。PR应包含练习 3分配的高对比度模式，以及练习 4在任务控制中心请求的浅色模式。

1. 打开相关 PR并审查 **Files changed**。
2. 注意：
   - 模式切换 UI组件。
   - 使用本地存储持久化用户偏好。
   - 高对比度和浅色模式的 CSS或样式变更。
   - ARIA属性和键盘导航等可访问性属性。
   - 管理模式切换的 JavaScript/TypeScript代码。
3. 工作流等待批准时，选择 **Approve and run workflows**。
4. 可切换到分支并手动测试：

    ```bash
    git fetch origin
    git checkout <branch-name>
    ```

可在浏览器中测试高对比度和浅色模式，并确认刷新页面后偏好仍会保留。

## 可选练习：继续委派

将更多真实待办事项分配给 Copilot，例如：

- 在游戏详情页创建支持者兴趣表单。
- 为游戏列表实现分页。
- 为数据访问辅助函数添加输入验证和错误处理。

## 摘要

你已完成云智能体实验。整个过程中，你：

- 棡查了仓库中的自定义指令文件。
- 将 issue分配给 Copilot云智能体，并监控环境、计划和异步执行。
- 创建并使用可访问性自定义智能体。
- 使用智能体页面监控并引导会话。
- 审查并迭代云智能体 PR。

## 审查和后续步骤

云智能体的实践可与其他环境工作流互补：

- 🖥️ **[VS Code研讨会](../../vscode/)**：直接在 IDE中体验 Copilot Chat智能体模式和 MCP集成。
- 💻 **[CLI研讨会](../../cli/)**：在终端完成并审查变更，使用 Plan/Autopilot模式、智能体技能、自定义 QA智能体、Playwright MCP和可选 `/delegate`。

可继续尝试重构、测试覆盖率、其他技术栈或新的自定义智能体。

## 资源

- [GitHub Copilot][github-copilot]
- [关于 Copilot智能体][copilot-agents]
- [将 GitHub issue分配给 Copilot][assign-issue]
- [云智能体防火墙配置][agent-firewall]

---

| [← 上一课：管理智能体][previous-lesson] |
|:--|

[github-copilot]: https://github.com/features/copilot
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[assign-issue]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions
[cloud-agent-best-practices]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[agent-firewall]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-firewall
[previous-lesson]: ../4-managing-agents/
