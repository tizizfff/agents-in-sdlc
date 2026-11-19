---
title: "练习 4：监控和管理智能体"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

在前面的练习中，你让 Copilot云智能体执行了多个任务。虽然云智能体异步自主运行，监控任务仍然重要。

GitHub.com上的[智能体页面][agents-page]等工具可用于管理分配给云智能体的任务。可在任务控制中心查看具有开放 PR的智能体任务、探索已执行操作，甚至引导进行中的会话。

在本课中，你将：

- 浏览智能体页面以监控云智能体任务。
- 引导进行中的会话，要求额外功能。

## 场景

分配智能体创建高对比度模式后，团队希望同时添加浅色模式。由于工作已在更新站点样式和切换功能，可将浅色模式纳入相同任务，并引导智能体同时添加浅色模式和高对比度模式。

## 审查云智能体任务

查看分配给 Copilot云智能体的所有任务：

1. 打开[Copilot智能体页面](https://github.com/copilot/agents)。
2. 查看主窗格和左侧窗格中的任务，包括文档更新、游戏 API生成和高对比度模式。
3. 选择正在运行的任务，审查 Copilot执行的操作，例如检出代码、创建环境、设置 MCP服务器和完成任务。
4. 注意右侧的拉取请求窗格，可查看 PR和已修改文件。

> [!NOTE]
> 具体步骤会因 Copilot工作状态和采用的方法而异。

## 引导云智能体

现在请求 Copilot在实现高对比度模式的同时添加浅色模式开关。

1. 选择标题提及高对比度模式的会话。

    ![任务控制中心中的可访问性会话](../../../_images/ex6-accessibility-session.png)

2. 等待几分钟，直到会话显示已完成设置并开始工作。
3. 在 **Steer active session while Copilot is working**对话框中发送：

    ```plaintext
    While we are working on a high contrast mode, let's also add a light mode. There should be a switch for this mode as well where users can select their desired display mode.
    ```

    ![智能体页面中突出显示引导对话框的截图](../../../_images/ex6-steer-cloud-agent-task.png)

4. 按 <kbd>Enter</kbd>发送提示。
5. Copilot会确认提示并将它纳入工作流程。

## 让 Copilot完成工作

Copilot会处理更新后的任务，并将新要求纳入正在执行的流程。它仍会异步工作，因此无需持续监控，完成后再审查即可。

## 摘要和后续步骤

本课介绍了 Copilot智能体页面：可通过任务控制中心跟踪所有活动和已完成任务、审查所做工作，并在任务进行中重定范围或提供额外指导。

接下来将[迭代 Copilot创建的拉取请求][next-lesson]。

## 资源

- [Copilot智能体页面][agents-page]
- [关于自定义智能体][custom-agents]

---

| [← 上一课：自定义智能体][previous-lesson] | [下一课：迭代 Copilot的工作 →][next-lesson] |
|:--|--:|

[previous-lesson]: ../3-custom-agents/
[next-lesson]: ../5-iterating/
[agents-page]: https://github.blog/changelog/2025-07-03-agents-page-for-copilot-coding-agent-in-public-preview
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
