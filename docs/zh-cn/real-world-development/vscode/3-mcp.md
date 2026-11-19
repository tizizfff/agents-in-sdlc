---
title: "练习 3：使用 Playwright MCP服务器测试功能"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← 上一课：智能体模式][previous-lesson] · [下一课：自定义智能体 →][next-lesson]

你已使用智能体模式构建筛选功能。创建拉取请求前，应确认它确实能在浏览器中运行。无需亲自逐步操作站点，只需连接 **Playwright MCP服务器**，让 Copilot在真实浏览器中测试功能，再发布分支并创建 PR。

在本练习中，你将：

- 了解模型上下文协议（MCP）以及 MCP服务器如何为 Copilot扩展新工具。
- 将 Playwright MCP服务器添加到工作区。
- 请 Copilot使用该服务器在浏览器中手动测试筛选功能。
- 发布分支并为筛选工作创建拉取请求。

## 什么是模型上下文协议（MCP）？

智能体模式在能够超越编辑器时会更加强大。模型上下文协议（MCP）正是实现这一点的方式：它为智能体提供与外部工具和服务通信的标准方法。

![展示智能体模式内部工作及其如何与上下文、LLM 和工具（包括 MCP服务器及 VS Code扩展提供的工具）交互的图示](../../../_images/ex1-mcp-diagram.png)

[模型上下文协议（MCP）](https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/)为 AI 智能体提供与外部工具和服务通信的方式。使用 MCP后，智能体可实时与外部工具和服务通信，从而访问最新信息并代表你执行操作。

这些工具和资源通过 MCP服务器访问；它充当 AI 智能体与外部工具或服务之间的桥梁。MCP服务器负责管理智能体与外部工具（例如现有 API 或本地工具）之间的通信。每个 MCP服务器代表智能体可访问的一组工具和资源。

常见的 MCP服务器包括：

- **[GitHub MCP Server](https://github.com/github/github-mcp-server)**：提供用于管理 GitHub仓库的 API，可创建仓库、更新仓库并管理 issue和拉取请求。
- **[Playwright MCP Server](https://github.com/microsoft/playwright-mcp)**：使用 Playwright提供浏览器自动化能力，可导航页面、填写表单和选择按钮。

GitHub通过 [MCP registry](https://github.com/mcp)集中展示生态中的服务器，以提升可发现性。

> [!CAUTION]
> 对 MCP服务器应像对项目中的任何其他依赖项一样谨慎。使用前，请仔细审查源代码、验证发布者并考虑安全影响。只使用可信服务器，并谨慎授予敏感资源或操作权限。

## 审查 MCP配置

`.vscode/mcp.json`文件配置此 VS Code工作区可用的 MCP服务器。

1. 在 Codespace中打开 `.vscode/mcp.json`。
2. 应看到已配置的 `github`服务器：

    ```json
    {
      "servers": {
        "github": {
          "type": "http",
          "url": "https://api.githubcopilot.com/mcp/"
        }
      }
    }
    ```

此 `github`条目随项目模板提供，因此 Copilot可以在上一练习中读取待办事项。它使用[远程 GitHub MCP服务器][remote-github-mcp-server]，无需在本地安装；VS Code通过 HTTP连接，并在首次使用工具时与 GitHub进行身份验证。

## 添加 Playwright MCP服务器

现在添加第二个服务器。[Playwright MCP服务器][playwright-mcp-server]为 Copilot提供可控制的浏览器，正是测试功能所需。

1. 在 `.vscode/mcp.json`中，将 `playwright`条目添加到 `github`旁边：

    ```json
    {
      "servers": {
        "github": {
          "type": "http",
          "url": "https://api.githubcopilot.com/mcp/"
        },
        "playwright": {
          "command": "npx",
          "args": ["@playwright/mcp@latest", "--headless"]
        }
      }
    }
    ```

2. 保存文件。

与远程 `github`服务器不同，`playwright`是**本地**服务器；VS Code通过运行 `npx @playwright/mcp@latest`在你的机器上启动它。`--headless`要求浏览器在没有可见窗口的情况下运行，这是 Codespace没有桌面环境时必需的。

> [!NOTE]
> Tailspin Toys项目已使用 Playwright进行端到端测试，因此通常已安装浏览器。如果 Copilot报告缺少浏览器，请让它运行 `npx playwright install chromium`后重试。

## 启动并信任服务器

VS Code会按需启动 MCP服务器：第一次需要服务器工具时，VS Code启动服务器并询问是否信任。

1. 在 `.vscode/mcp.json`中，`playwright`条目上方会显示 **Start**操作。选择它立即启动服务器并确认配置正确。
2. 如果 VS Code询问是否信任服务器，请审查配置并选择信任。

手动启动为可选操作；如果跳过，Copilot在下一步首次使用工具时会由 VS Code启动并提示信任。

## 测试筛选功能

使用[Playwright MCP服务器][playwright-mcp-server]可让 Copilot操作真实浏览器。智能体可以打开页面、导航、应用筛选并向你报告结果，无需离开对话即可确认功能行为。

服务器底层使用页面的可访问性树而不是截图，因此智能体可以像辅助技术一样依据结构化、带标签的元素（按钮、链接、列表项）进行推理。

服务器已连接且应用正在运行后，请 Copilot执行以下筛选测试：

```text
Using the Playwright MCP server, open a browser to the running app at http://localhost:4321 and verify the new game filtering feature:

1. Go to the games page and note how many games are listed.
2. Apply a category filter and confirm the list updates to only show games in that category.
3. Clear it, then apply a publisher filter and confirm the list updates to that publisher.
4. Combine a category and a publisher filter and confirm the results respect both.

Report what you observe at each step, and call out anything that does not behave as expected.
```

Copilot将通过 Playwright MCP服务器启动浏览器、逐步执行并报告发现。将其摘要与 issue中的验收标准对照；若发现问题，可追问或请它修复代码，再创建 PR。

> [!NOTE]
> 测试需要应用运行在 `http://localhost:4321`。如果已停止开发服务器，请在发送提示前重新启动。Copilot首次使用 Playwright MCP服务器时可能需要下载浏览器；若报告浏览器缺失，请运行 `npx playwright install chromium`并重试。

[playwright-mcp-server]: https://github.com/microsoft/playwright-mcp

## 发布分支并创建拉取请求

确认功能正常后，即可创建拉取请求（PR）供团队审查。首先发布 `filtering-vscode`分支。

1. 打开 Codespace中的 **Source Control**面板并审查 Copilot所做的变更。
2. 选择 **+**图标暂存变更。
3. 使用 **Sparkle**按钮生成提交消息。

   ![Source Control面板中已做变更的截图](../../../_images/ex3-source-control-changes.png)

4. 选择 **Publish**将分支推送到仓库。

## 创建拉取请求

既然正在使用 GitHub Copilot，让它为你创建 PR：它可找到相关 issue并建立关联。

1. 打开 Copilot Chat面板并选择 **New Chat**创建新会话。
2. 在智能体下拉列表中确保选择了 **Agent**，以便 Copilot使用 GitHub工具。
3. 请 Copilot创建 PR：

   ```plaintext
   Find the issue in the repo related to filtering by category and publisher. Create a new pull request for the current branch, and associate it with the correct issue.
   ```

4. 根据提示选择 **Continue**，允许 Copilot收集信息并执行操作。首次使用 GitHub工具时可能需要身份验证，按照提示操作。
5. 观察 Copilot搜索 issue、找到正确 issue并创建 PR。
6. 选择 Copilot生成的链接审查 PR，但暂时不要合并。

## 摘要和后续步骤

恭喜！本练习中，你：

- 了解了模型上下文协议（MCP）以及 MCP服务器如何为 Copilot扩展新工具。
- 将 Playwright MCP服务器添加到工作区。
- 在交付前使用浏览器手动测试筛选功能。
- 发布分支并为筛选工作创建拉取请求。

你使用 MCP服务器**测试**了功能；但 MCP只是 Copilot的一种扩展方式。接下来，[创建自定义智能体][next-lesson]，简化可访问性审查等专注任务。

## 资源

- [什么是 MCP，为什么大家都在讨论它？][mcp-blog-post]
- [Microsoft Playwright MCP Server][playwright-mcp-server]
- [GitHub MCP Server][github-mcp-server]
- [GitHub MCP Registry][mcp-registry]
- [VS Code中的 MCP服务器][vscode-mcp-config]

[previous-lesson]: ../2-agent-mode/
[next-lesson]: ../4-custom-agents/
[mcp-blog-post]: https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/
[github-mcp-server]: https://github.com/github/github-mcp-server
[mcp-registry]: https://github.com/mcp
[remote-github-mcp-server]: https://github.blog/changelog/2025-06-12-remote-github-mcp-server-is-now-available-in-public-preview/
[vscode-mcp-config]: https://code.visualstudio.com/docs/agents/reference/mcp-configuration
