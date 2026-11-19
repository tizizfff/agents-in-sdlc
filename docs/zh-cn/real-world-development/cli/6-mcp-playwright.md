---
title: "第 6 课：使用 Playwright MCP 验证功能"
description: "在 Copilot CLI 中检查或配置 Playwright MCP，并使用它在浏览器中体验筛选功能。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

我们已经强调，编写代码远不止编写代码。我们需要处理数据、外部服务，还希望 Copilot能够使用更多自动化能力。MCP 服务器正是为此而生：它使 Copilot超越 CLI 内置功能，并提供更多工具和服务。

在本课中，你将：

- 了解模型上下文协议（MCP）及 Copilot CLI 如何使用它。
- 在 Playwright MCP 尚未可用时添加该服务器。
- 请智能体驱动浏览器并体验筛选功能。

## 场景

单元测试和端到端测试固然重要，但验证 UI 更新需要实际操作界面。你希望 Copilot像普通用户一样使用正在开发的站点，以进一步自动化变更验证并提高对预期行为的信心。

## 什么是模型上下文协议（MCP）？

[模型上下文协议（MCP）][mcp-blog-post]为 AI 智能体提供与外部工具和服务通信的方式。通过 MCP，AI 智能体可以实时通信并代表你执行操作。

这些工具和资源通过 MCP 服务器访问；服务器充当 AI 智能体与外部工具或服务之间的桥梁。每个 MCP 服务器代表一组可供智能体访问的工具和资源。

常见的 MCP 服务器包括：

- **[GitHub MCP Server][github-mcp]**：提供用于管理 GitHub 仓库、issue 和拉取请求的 API。
- **[Playwright MCP Server][playwright-mcp-server]**：使用 Playwright 提供浏览器自动化能力。

还有许多其他 MCP 服务器。GitHub 提供 [MCP registry][mcp-registry]以提升生态系统中的可发现性和贡献便利性。

> [!CAUTION]
> 对 MCP 服务器应像对项目中的其他依赖项一样谨慎。使用前，请审查源代码、验证发布者并考虑安全影响。

## 添加 Playwright MCP服务器

如果 Playwright MCP服务器尚不可用，请添加它，以便 Copilot像用户一样与站点交互。

> [!NOTE]
> 如果 Copilot CLI 已配置 Playwright MCP，请跳过以下设置步骤并继续下一节。

1. 返回 Codespace。
2. 在 Copilot CLI 中输入以下命令，打开添加 MCP 服务器对话框：

   ```plaintext
   /mcp add
   ```

3. 名称输入 `playwright`，然后按 <kbd>Tab</kbd>。
4. 按 <kbd>Enter</kbd>确认服务器类型为 **STDIO**，然后按 <kbd>Tab</kbd>。
5. 将以下内容粘贴到 **Command** 对话框：

   ```plaintext
   npx -y @playwright/mcp@latest --headless --no-sandbox
   ```

6. 按 <kbd>Control</kbd>+<kbd>S</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>S</kbd>（Windows/Linux）保存新 MCP 服务器。
7. 按 <kbd>Esc</kbd>退出 MCP 对话框。

## 请 Copilot通过 Playwright体验功能

之前你已手动确认功能符合预期。现在使用 Copilot提供的 Playwright MCP服务器执行相同验证！

1. 使用以下提示，请 Copilot使用 Playwright MCP验证功能：

   ```plaintext
   Start the app and use Playwright MCP to check filtering against the issue and our plan. Tell me what works and what doesn't, without making changes. Stop the server you started when you're done.
   ```

> [!NOTE]
> 实际上无需明确要求 Copilot使用 MCP服务器，因为它通常会自行判断。但既然你知道应使用的工具，适当指引从不会是坏事；这有助于获得更一致的结果并节省部分 token。

2. 观察 Copilot列出并执行的浏览器步骤，以确认功能正常。
3. 阅读报告并确保一切符合预期。

Copilot将启动服务器、使用 Playwright与站点交互、停止服务器并提供报告。

## 摘要和后续步骤

恭喜，你已从 Copilot CLI使用 Playwright MCP在真实浏览器中体验功能！回顾本课，你：

- 了解了模型上下文协议（MCP）及 Copilot CLI如何使用它。
- 在尚未配置时添加了 Playwright MCP服务器。
- 请智能体使用浏览器体验筛选功能。

接下来，你将[创建一个自定义 QA 智能体][next-lesson]，将技能和浏览器工具整合为专业角色。

## 资源

- [什么是 MCP，为什么大家都在讨论它？][mcp-blog-post]
- [Microsoft Playwright MCP Server][playwright-mcp-server]
- [向 Copilot CLI 添加 MCP服务器][add-mcp]

[previous-lesson]: ../5-agent-skills/
[next-lesson]: ../7-qa-agent/
[mcp-blog-post]: https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/
[playwright-mcp-server]: https://github.com/microsoft/playwright-mcp
[github-mcp]: https://github.com/github/github-mcp-server
[mcp-registry]: https://github.com/mcp
[add-mcp]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-mcp-servers
