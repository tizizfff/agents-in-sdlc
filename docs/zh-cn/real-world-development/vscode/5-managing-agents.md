---
title: "练习 5：监控和管理智能体"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← 上一课：自定义智能体][previous-lesson] |
|:--|

将 GitHub Copilot置于智能体模式后，它会自主探索代码库、提出变更、编辑文件并运行命令。由于工作在本机实时进行，VS Code中的 Copilot Chat可实时显示每次工具调用和每次文件编辑。你可以逐项审查差异、接受或拒绝单个变更，并通过后续提示引导对话以优化或扩展工作，无需离开编辑器。

在本练习中，你将：

- 实时监控可访问性智能体的工作。
- 审查并接受建议的文件编辑。
- 在会话中途引导智能体添加浅色模式开关。

## 场景

[练习 4][previous-lesson]中使用的可访问性自定义智能体正在实现高对比度模式。工作进行中时，设计团队提出了新要求：希望提供浅色模式开关，供认为默认主题过暗的用户使用。无需从头开启新会话，你可继续引导现有会话扩展工作。

## 监控 Copilot的进度

Copilot Chat视图会显示智能体采取的每一步，包括探索的文件、运行的命令和建议的编辑。每项文件编辑都会以差异和 **Keep** / **Undo**控件显示在聊天中。

1. 返回练习 4的 Copilot Chat视图。
2. 智能体工作时，滚动聊天以查看工具调用。你会看到文件读取、文件编辑以及它请求运行的终端命令。
3. 智能体提出文件编辑时，差异会内嵌显示：
   - 选择 **Keep**接受变更。
   - 选择 **Undo**恢复变更并让智能体重新尝试。
4. 可打开聊天顶部的 **Files changed**指示器，查看当前会话中智能体修改的完整工作集。

> [!NOTE]
> 工具调用需要权限时（例如运行终端命令），智能体会暂停并显示 **Allow**提示。仅批准你认为合适的命令。

5. 等待智能体完成高对比度模式实现。最后应会看到汇总所做变更的消息。

## 引导智能体添加浅色模式

高对比度模式已就位，现在可继续同一对话以添加浅色模式开关。由于继续使用同一聊天会话，智能体会保留先前工作的上下文，包括修改过的组件、使用的样式方法和设置的本地存储模式。

1. 在 Copilot Chat输入框中发送以下后续提示：

    ```plaintext
    Nice work! Now add a light-mode toggle alongside the high-contrast toggle. Light mode should follow the same pattern — persist via local storage and be accessible from the same area of the UI. The user should be able to enable high-contrast and light mode independently.
    ```

2. 智能体会从中断处继续，探索已做变更，并提出浅色模式的新增内容。
3. 与审查高对比度模式一样，逐项审查新编辑。在每个差异上使用 **Keep**或 **Undo**。
4. 如果智能体偏离预期，例如尝试以不想要的方式重构切换 UI，可选择聊天输入框旁的 **Stop**停止，然后发送澄清提示。

> [!TIP]
> 引导进行中的会话比从头重来更快。可使用后续提示进行调整（“简化 CSS，使用 CSS变量而非重复选择器”）、纠正方向（“不要添加第三个开关，将浅色模式整合到现有设置面板”），或扩展范围（“为两个开关添加键盘快捷键”）。

## 审查工作集

提交前，请快速检查智能体触及的所有内容。

1. 在 VS Code中打开 **Source Control**视图。
2. 审查完整的已修改文件列表；应看到 Astro组件、样式及相关测试的更新。
3. 打开几项已修改文件并逐一查看差异。确认自定义智能体的可访问性模式已体现，包括 ARIA属性、键盘导航、语义化 HTML 和通过本地存储持久化。
4. 确信无误后，在 Source Control面板中暂存并提交变更；将在[下一课][next-lesson]发布这些内容。

## 摘要和后续步骤

你已使用 Copilot Chat智能体模式监控并引导进行中的会话：逐项审查文件编辑、接受或拒绝变更，并发送后续提示在不丢失上下文的情况下扩展工作。

本课中，你了解了：

- 实时监控智能体工作。
- 接受或拒绝单个文件编辑。
- 使用后续提示在会话中途引导智能体。

在[下一课][next-lesson]中，你将把可访问性工作作为拉取请求发布，并审查本地自定义智能体在整个实验中生成的变更。

## 资源

- [VS Code中的 Copilot Chat][copilot-chat-vscode]
- [使用智能体模式][agent-mode]

---

| [← 上一课：自定义智能体][previous-lesson] | [下一课：迭代 Copilot的工作 →][next-lesson] |
|:--|--:|

[previous-lesson]: ../4-custom-agents/
[next-lesson]: ../6-iterating/
[copilot-chat-vscode]: https://code.visualstudio.com/docs/copilot/chat/copilot-chat
[agent-mode]: https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode
