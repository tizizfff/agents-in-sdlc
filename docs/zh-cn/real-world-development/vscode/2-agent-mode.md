---
title: "练习 2：使用 Copilot智能体模式添加新功能"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

即使是最简单的应用更新，通常也需要修改多个文件并运行测试。作为开发者，你需要定位所有相关文件、进行修改、运行测试、调试、找出遗漏的文件，然后再次更新，工作流程会不断重复。

这正是 Copilot智能体模式发挥作用的地方。

Copilot智能体模式在 IDE中能够更自主地执行任务。它的工作方式类似开发者：探索现有项目结构、执行必要更新、运行测试等任务，并自动修复发现的问题。下面将探索如何使用智能体模式向站点添加新功能。

> [!NOTE]
> 虽然名称相近，智能体模式和云智能体面向不同体验。智能体模式在 IDE中执行任务，反馈和交互速度快；云智能体像团队成员一样异步工作，通过 issue和拉取请求与你协作。

在本练习中，你将了解：

- Copilot智能体模式如何探索项目、识别相关文件并协调变更。
- GitHub Copilot智能体模式如何跨 UI和数据层实现新功能。
- 如何在合并前审查智能体生成的变更和测试。

## 场景

随着游戏数量增加，你希望用户能够按类别和发行商筛选。上一练习已添加发行商辅助函数，现在将使用 Copilot智能体模式完成剩余的数据层、UI和测试工作。

## 运行 Tailspin Toys网站

修改前，先探索网站以了解当前功能。

网站是面向桌游的众筹平台，主题围绕开发者。它展示游戏列表并显示游戏详情。网站是一个单独的 Astro应用，构建时将页面渲染为静态 HTML。页面通过 Drizzle ORM直接在 frontmatter中查询本地 SQLite数据库，没有独立后端 API或客户端 UI框架。可复用数据访问辅助函数位于 `src/lib/`，交互通过使用标准 DOM API的轻量作用域 Astro `<script>`添加。

### 启动网站

项目提供了 `npm run dev`任务以启动单个 Astro开发服务器。

1. 返回 Codespace；上一练习后应已回到 `main`。
2. 按 <kbd>Control</kbd>+<kbd>\`</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>\`</kbd>（Windows/Linux）在 Codespace中打开新终端。
3. 创建筛选工作分支：

   ```bash
   git checkout main
   git pull
   git checkout -b filtering-vscode
   ```

4. 启动站点：

   ```bash
   npm run dev
   ```

   Astro开发服务器就绪后，应看到类似以下横幅：

   ```text
   🚀 Tailspin Toys is ready!
      Astro server: http://localhost:4321
      Press Ctrl-C to stop.
   ```

> [!NOTE]
> 如果出现对话框提示打开 `http://localhost:4321`，请选择 **x**关闭。

5. 按住 <kbd>Command</kbd>（Mac）或 <kbd>Ctrl</kbd>（Windows/Linux），选择终端中的 Astro服务器地址 `http://localhost:4321`打开站点。

> [!NOTE]
> 在 Codespace中选择 localhost链接时，终端会自动重定向到 `https://<your-codespace-name>-4321.app.github.dev/`，这是指向当前托管 Web服务器的私有隧道。

### 浏览站点

站点运行后，可探索主要功能：

- **Home Page**：显示带标题、图片和描述的桌游列表。
- **Game Details Page**：选择游戏后进入详情页，可查看标题、描述、发行商和类别等信息。

## 使用 Copilot浏览待办事项

> [!TIP]
> **打开 Copilot Chat**
>
> 开始下面练习前，请返回 Codespace、打开 Copilot Chat面板并选择 **New Chat**。

初始实现虽然可用，但希望通过新能力增强站点。先从待办事项开始：设置模板仓库时会自动创建 issue，使用 GitHub Copilot显示这些条目。

1. 在聊天视图智能体下拉列表中选择 **Agent**。**Agent**智能体可自主规划和实现跨文件修改、运行终端命令并调用工具。

   ![聊天视图中智能体选择器的截图](../../../_images/shared-chat-mode-selector.png)

2. 从可用模型中选择 **Claude Sonnet 4.5**。

> [!CAUTION]
> 本研讨会的作者并未暗示偏爱任何模型。构建时使用 Claude Sonnet 4.5，因此将它作为指令中的示例。希望得到相对一致的代码建议，但 LLM具有概率性，因此你的建议可能与研讨会显示的有所不同。

> [!NOTE]
> 由于 LLM具有概率性，Copilot可能使用不同 MCP命令，但仍应能够完成任务。

3. 向 Copilot发送以下提示以查看待办事项：

   ```plaintext
   Please show me the backlog of items from my GitHub repository. Help me prioritize them based on those which will be most useful to the user.
   ```

4. 选择 **Continue**运行列出所有 issue的命令。
5. 审查生成的 issue列表。Copilot会根据对用户的价值排序。

## 审查指令文件

启动智能体生成代码前，最好审查提供上下文的指令文件。将使用包含向站点添加功能方法的[用户界面（UI）](https://github.com/github-samples/tailspin-toys/blob/main/.github/instructions/ui.instructions.md)文件。

1. 在 Codespace中打开 `.github/instructions/ui.instructions.md`。
2. 注意其整体指导，包括：
   - 架构概览。
   - 组件设计、可测试性和可访问性原则。
   - 指向 Astro、Tailwind CSS、Drizzle等文件类型具体指令的链接。

> [!TIP]
> 指令文件可引用其他指令文件和项目文件；路径相对于指令文件位置。这支持复用、拆分复杂指令并提供示例和模板。

## 实现筛选功能

完成筛选至少需要三项更新：

- 在数据层（`src/lib/`）添加或完善剩余筛选逻辑。
- 添加或更新筛选行为测试。
- 更新游戏列表页以引入筛选 UI。

此外，合并前测试必须运行且通过。Copilot智能体模式可执行这些任务。

1. 可继续当前 Copilot对话，也可选择 **New Chat**。
2. 选择 **Add Context**、**Instructions**，再选择 **ui**指令文件。

   ![选择 UI指令文件的示例截图](../../../_images/ex3-select-instructions-file.png)

3. 在聊天视图智能体下拉列表中确认仍选择 **Agent**。

   ![聊天视图中智能体选择器的截图](../../../_images/shared-chat-mode-selector.png)

4. 确认仍选择 **Claude Sonnet 4.5**。
5. 根据待办事项中的相关 issue请 Copilot实现功能：

   ```plaintext
   Please update the site to include filtering by publisher and category based on the requirements from the related GitHub issue in the backlog. A publishers helper already exists from the previous exercise, so preserve and refine that work as needed while completing the remaining data-layer, UI, and tests. Ensure all tests are passing before completion. The server is already running, so you do not need to start it up.
   ```

6. 观察 Copilot：它先探索项目、定位相关文件，再开始修改文件并运行测试。

   ![Copilot探索项目文件的截图](../../../_images/ex3-agent-mode-explores.png)

> [!NOTE]
> Copilot会探索项目、修改文件并运行测试。复杂度取决于任务和代码库。编辑器可能出现 **Keep**和 **Undo**按钮；完成后可对全部变更逐项选择，不必在工作进行中操作。

7. 当 Copilot提示运行测试时，选择 **Continue**。

   ![Copilot Chat窗格询问是否运行测试的截图](../../../_images/ex3-agent-mode-run-tests.png)

8. 过程中可能暂停，甚至出现测试失败。这是正常现象；Copilot会在代码生成和测试之间迭代，直到完成且无错误。

   ![包含 Copilot智能体模式完整聊天会话的截图](../../../_images/ex3-agent-mode-proposed-changes.png)

9. 浏览生成代码，检查潜在问题。任何 AI工具生成的代码都必须审查。
10. 返回运行中的站点浏览器并体验新功能。
11. 确信一切正常且已审查代码后，在 Copilot Chat窗口选择 **Keep**。

## 摘要和后续步骤

恭喜！本练习中，你使用 GitHub Copilot智能体模式为 Tailspin Toys网站添加新能力，并了解：

- 智能体模式可跨 UI和数据层实现新功能。
- 智能体模式可探索项目、识别相关文件并进行协调修改。
- 合并前应审查智能体生成的变更和测试。

现在，[使用 Playwright MCP服务器测试功能][next-lesson]并为它创建拉取请求。

### 附加探索：实现分页

随着游戏数量增加，可能需要启用分页。使用本练习所学，请 Copilot实现分页，并考虑：

- 遵循现有最佳实践和指令文件。
- 决定是否允许用户选择页面大小，或使用固定值。
- 在提示中提供实现所需的指导。
- 可能需要与 Copilot迭代修改并提供上下文，这是正常工作流程。

## 资源

- [Copilot提问、编辑和智能体模式：用途及何时使用][choose-mode]
- [VS Code中的智能体模式][vs-code-agent-mode]

[previous-lesson]: ../1-custom-instructions/
[next-lesson]: ../3-mcp/
[choose-mode]: https://github.blog/ai-and-ml/github-copilot/copilot-ask-edit-and-agent-modes-what-they-do-and-when-to-use-them/
[vs-code-agent-mode]: https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode
