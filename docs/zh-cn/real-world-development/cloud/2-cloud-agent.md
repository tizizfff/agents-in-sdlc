---
title: "练习 2：GitHub Copilot云智能体"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← 上一课：自定义指令][previous-lesson] |
|:--|

很少有组织不存在技术债务：可能是未解决的安全问题、需要更新的旧代码，或因缺少时间而长期停留在待办事项中的功能请求。GitHub Copilot云智能体可执行更新代码和添加功能等任务，并以自主方式工作。完成后会生成供人工开发者审查的草稿 PR。这可以卸载繁琐任务并加速开发流程，让开发者专注更宏观的工作。

你将探索：

- 自定义生成代码的环境。
- 确保操作安全。
- 明确限定 issue范围的重要性。
- 将 issue分配给 Copilot。

## 场景

Tailspin Toys需要处理一些技术债务。最初创建站点第一版的承包商留下了状态不佳的文档——现在几乎没有文档。团队希望先在所有导出函数中添加 TSDoc文档注释。

设计团队还希望改进游戏发现体验：每款游戏的详情页应显示同类别的相关游戏，以便继续浏览。团队不需要完善实现，只需一个可用于 UX验收测试的可用版本。

## GitHub Copilot云智能体简介

[GitHub Copilot云智能体](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent#overview-of-copilot-cloud-agent-formerly-copilot-coding-agent)可在后台执行任务，方式与人类开发者相似。可通过[将 GitHub issue分配给 Copilot](https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions)使用。分配后，Copilot会创建草稿拉取请求跟踪进度、设置环境并开始工作。可在会话进行中或完成后查看；准备审查时，它会在 PR中向你打标签。

## 明确限定指令范围的重要性

GitHub Copilot没有捷径可跳过思考。即使是看似直接的操作，深入层次后也可能充满复杂性，因此应[谨慎限定云智能体任务范围][cloud-agent-best-practices]。可将智能体视为 AI结对编程伙伴：分阶段工作、学习、实验并随时调整。生成式 AI不会改变软件开发的基本方法。

## 此仓库中的自定义指令

前面的练习介绍了自定义指令及其作用。如果已完成自定义指令实践，已有机会看到 `.github/copilot-instructions.md`的效果；如果未完成，请在分配工作前快速查看现有指令文件，以便稍后观察效果。

打开仓库中的以下文件：

- `.github/copilot-instructions.md`：审查 **Code standards**章节，尤其 TypeScript约定和 TSDoc文档注释。
- `.github/instructions/unit-tests.instructions.md`：注意其 `applyTo`frontmatter如何将指令限定到 `**/*.test.ts`。

将 `Code lacks documentation`issue分配给云智能体时，请观察生成 PR中的 TSDoc注释、TypeScript约定和注释头。

## 设置云智能体开发环境

无论由谁编写代码，通常都需要特定环境和设置脚本，以确保一切就绪。将任务分配给执行 SWE类工作的 Copilot时也是如此。

云智能体使用 [GitHub Actions][github-actions]作为工作环境，可通过 `.github/workflows/copilot-setup-steps.yml`中的专用设置工作流自定义环境：

```yaml
name: "Copilot Setup Steps"

on: workflow_dispatch

env:
  ASTRO_TELEMETRY_DISABLED: "1"

jobs:
  copilot-setup-steps:
    runs-on: ubuntu-latest
    permissions:
      contents: read
    steps:
      - name: Checkout code
        uses: actions/checkout@v5
      - name: Set up Node.js
        uses: actions/setup-node@v6
        with:
          node-version: "lts/*"
          cache: "npm"
          cache-dependency-path: "./package-lock.json"
      - name: Install JavaScript dependencies
        run: npm ci
      - name: Install Playwright browsers
        run: npx playwright install --with-deps chromium
      - name: Set up the database
        run: npm run db:setup
```

该工作流可在 Copilot开始工作前提供 Node.js、项目依赖项、浏览器二进制文件以及迁移并填充后的 SQLite数据库。

## 添加文档

文档长期未更新或完全缺失会拖慢生产力并妨碍新成员加入。Copilot擅长生成文档，适合将此类 issue分配给云智能体。

1. 在新的浏览器标签页中打开仓库。
2. 选择 **Issues**标签页。
3. 选择 **New issue**。
4. 选择 **Blank issue**。
5. 标题设为 `Code lacks documentation`。
6. 描述设为：

    ```plaintext
    Our organization has a requirement that functions and methods include TSDoc doc comments where helpful. Unfortunately, recent updates haven't followed this standard. We need to update the existing code to ensure doc comments are included where they clarify behavior.
    ```

7. 创建 issue。
8. 在右侧选择 **Assign to Copilot**。
9. 选择 **Assign**。

后续可在生成的 PR中查看文档工作和会话。

## 为游戏详情页添加相关游戏章节

将第二项任务分配给云智能体：

1. 打开仓库的 **Issues**标签页并选择 **New issue**。
2. 标题设为 `Show related games on the game details page`。
3. 描述设为：

    ```markdown
    We want to help people discover more games by showing related games on each game's details page. The design team wants to explore the UX and do some acceptance testing. Our requirements are:

   - Add a data-access helper in `src/lib/` that returns other games in the same category as a given game, excluding that game
   - Show a "Related games" section on the game details page that uses the helper
   - Handle the case where a game has no related games
   - There should be unit tests created for the new helper
   - Before creating the PR, ensure all tests pass
    ```

4. 创建 issue并选择 **Assign to Copilot**分配智能体。

## 摘要和后续步骤

本课介绍了 [GitHub Copilot云智能体][copilot-agents]。使用云智能体可将 issue异步分配给 Copilot处理技术债务、新增功能或迁移框架。

接下来将使用自定义智能体。云智能体也可使用 MCP服务器并遵循自定义指令。

## 资源

- [关于 Copilot云智能体][copilot-agents]
- [将 GitHub issue分配给 Copilot][assign-issue]
- [云智能体设置工作流最佳实践][cloud-agent-best-practices]

[previous-lesson]: ../1-custom-instructions/
[next-lesson]: ../3-custom-agents/
[cloud-agent-mcp]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/extend-cloud-agent-with-mcp
[assign-issue]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions
[setup-workflow]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[cloud-agent-best-practices]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[github-actions]: https://docs.github.com/actions
