---
title: "练习 4：自定义智能体"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## 什么是自定义智能体？

[自定义智能体][custom-agents-concept]可以让 GitHub Copilot为开发工作流中的特定任务或领域创建专门的 AI助手。通过在仓库的 `.github/agents`文件夹中定义 Markdown文件，可向 Copilot提供专注指令、最佳实践、编码模式和领域知识，使它更有效地执行特定工作。团队可以将专业知识编码为可复用智能体：例如强制遵循 [WCAG][wcag]的可访问性智能体、遵循安全编码实践的安全智能体，或维护一致测试模式的测试智能体。

自定义智能体由项目的 `.github/agents`文件中的 Markdown定义，也可全局放在 `~/.copilot/agents`中。每个文件使用 YAML frontmatter至少包含 `name`和 `description`，后接定义行为、专业能力和指令的 Markdown提示。

### 自定义智能体与智能体技能

自定义智能体和[智能体技能][agent-skills-concept]存在部分重叠，两者都主要使用 Markdown定义，并指导 AI执行操作。最清晰的区分是：**自定义智能体**是执行者，**技能**是工具。

自定义智能体拥有独立上下文窗口，可在工作中编排技能甚至其他智能体。在此实验中，可访问性自定义智能体会根据可访问性指南审查并更新站点；工作中可调用拉取请求工作流技能或运行和管理测试的技能。

> [!NOTE]
> 编写自定义智能体没有唯一正确方式。与 AI领域的其他内容一样，应测试并迭代，找到适合环境和场景的方法。

[custom-agents-concept]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[agent-skills-concept]: https://docs.github.com/copilot/concepts/agents/about-agent-skills
[wcag]: https://www.w3.org/WAI/standards-guidelines/wcag/

## 场景

Tailspin Toys致力于让所有用户都能访问众筹平台，无论用户的视觉能力或偏好如何。最近的反馈显示，有些用户认为当前深色主题的文字与背景对比度不足，因而难以阅读。为解决这一可访问性问题，设计团队要求实现可开关的高对比度模式。

可访问性至关重要，因此你希望尽快实现该功能，并使用自定义智能体生成它。

在本练习中，你将：

- 审查现有的可访问性自定义智能体。
- 在 Copilot Chat中使用该智能体实现高对比度模式。

## 审查可访问性自定义智能体

系统已为你创建可访问性自定义智能体。先审查其内容，了解它将如何指导 Copilot。

返回 Codespace，打开终端，并从 `main`创建可访问性工作的新分支（筛选 PR应与练习 3分开）：

```bash
git checkout main
git pull
git checkout -b accessibility-vscode
```

1. 打开 `.github/agents/accessibility.md`。
2. 注意包含 `name`和 `description`字段的 YAML frontmatter。

> [!CAUTION]
> 自定义智能体的 frontmatter中必须包含 `name`和 `description`。

3. 继续阅读下面的章节：
   - 为可访问性网站生成代码时的核心职责。
   - 可访问性最佳实践。
   - HTML、CSS 和 JavaScript代码示例。
   - 常见陷阱和错误列表。

## 在 Copilot Chat中使用自定义智能体

VS Code会在 Copilot Chat视图底部的智能体下拉列表中显示 `.github/agents`中定义的所有自定义智能体。选择一个智能体，可将聊天会话限定为该智能体的指令和工具。

> [!TIP]
> **打开 Copilot Chat**
>
> 开始下面的练习前，请返回 Codespace、打开 Copilot Chat面板并选择 **New Chat**，开始干净的新对话。本练习的模式和模型选择会因步骤而异，后文会明确指出。

1. 如果尚未选择，请在聊天视图的智能体下拉列表中选择 **Agent**。

   ![聊天视图中智能体选择器的截图](../../../_images/shared-chat-mode-selector.png)

2. 选择聊天视图底部的智能体下拉列表；其中会显示当前智能体，默认通常是 **default**。
3. 从可用智能体列表中选择 **Accessibility agent**。
4. 向可访问性智能体发送以下提示：

    ```plaintext
    Add a high-contrast mode to the site. There should be a toggle for high contrast which the user can set, and the setting should persist across page reloads using local storage on the browser.
    ```

5. Copilot Chat将开始工作：探索代码库、提出变更并编辑项目文件。每项编辑都会以文件路径和差异的形式显示在聊天中。
6. 编辑落地后，**Files changed**指示器会更新，以便查看智能体修改的工作集。

> [!NOTE]
> 此过程可能需要几分钟。Copilot会对仓库进行真实修改，包括编辑 Astro组件、CSS及相关测试。

下一练习将审查并引导这项进行中的工作。

## 摘要和后续步骤

本课介绍了 GitHub Copilot中的[自定义智能体][custom-agents]：它们是为特定任务和领域定制的专业 AI助手。通过自定义智能体，可将团队的专业知识和规范编码为可复用智能体，使 Copilot更有效地执行特定类型的工作。

你已了解：

- 如何定义自定义智能体。
- 如何在 Copilot Chat智能体模式中使用自定义智能体。

接下来，你将[监控并引导智能体的工作][next-lesson]：实时审查变更，并在同一会话中添加浅色模式开关。

## 资源

- [关于自定义智能体][custom-agents]
- [在 IDE中创建自定义智能体][creating-custom-agents-ide]
- [VS Code中的自定义智能体][custom-agents-vscode]
- [自定义智能体配置][custom-agents-config]
- [awesome-copilot中的自定义智能体][awesome-copilot-agents]

---

| [← 上一课：使用 Playwright MCP服务器测试功能][previous-lesson] | [下一课：监控和管理智能体 →][next-lesson] |
|:--|--:|

[previous-lesson]: ../3-mcp/
[next-lesson]: ../5-managing-agents/
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[creating-custom-agents-ide]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents-in-your-ide
[custom-agents-vscode]: https://code.visualstudio.com/docs/copilot/customization/custom-agents
[custom-agents-config]: https://docs.github.com/copilot/reference/custom-agents-configuration
[awesome-copilot-agents]: https://github.com/github/awesome-copilot/tree/main/agents
